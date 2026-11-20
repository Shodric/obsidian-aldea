---
tipo: documento
estado: borrador
area: tecnologia
actualizado: 2026-11-20
---

# Arquitectura — Créditos con vencimiento

> [!info] Principio
> La arquitectura debe implementar el modelo económico con la **mínima complejidad posible**. Blockchain es una opción, no un requisito. El MVP puede funcionar con una base de datos y migrar después si hace falta.

## 1. Concepto: crédito como “lote” con vencimiento

El crédito no es un saldo único: es un conjunto de **lotes** (equivalente a UTXO) con:

| Campo | Tipo | Descripción |
|---|---|---|
| `id` | UUID | Identificador del lote |
| `owner_id` | UUID | Dueño actual |
| `amount` | Decimal | Monto del lote |
| `created_at` | Timestamp | Emisión o última transferencia |
| `expires_at` | Timestamp | `created_at + T` |
| `status` | Enum | `active`, `spent`, `expired`, `frozen` |
| `origin_obligation_id` | UUID | Obligación que respalda la emisión |
| `parent_id` | UUID | Lote del que se partió (si aplica) |

**Saldo disponible** = suma de lotes `active` con `expires_at > now`.

## 2. Ciclo de vida

```
emisión → lote activo → transferencia (parte) → nuevos lotes → vencimiento → quemado
```

### Emisión
- Se crea un lote por el monto de la oferta.
- `origin_obligation_id` apunta al compromiso del emisor.
- `expires_at = now + T`.

### Transferencia
- Se seleccionan lotes del comprador (primero los que vencen antes).
- Se debita el monto y se crea un lote para el vendedor con `expires_at = now + T`.
- El vuelto se crea como lote nuevo para el comprador, también con plazo renovado.
- Se registra la transacción y el motivo.

### Vencimiento
- Un job periódico marca `expired` los lotes con `expires_at <= now`.
- Se emite un evento `credit.expired` para auditoría.
- El saldo se recalcula.

### Partición
- Un lote de 10 se parte en 5 + 5; ambos heredan `parent_id`.
- Cada parte mantiene su propio `expires_at` (renovado al transferir).

## 3. Reglas anti-abuso

| Riesgo | Regla |
|---|---|
| **Auto-transferencia para renovar** | Detectar transferencias entre cuentas vinculadas; no renovar si el beneficiario es el mismo grupo. |
| **Fraccionamiento excesivo** | Límite de lotes por cuenta y mínimo por lote. |
| **Acaparamiento** | Techo por cuenta y alerta de concentración. |
| **Colusión** | Grafo de transacciones y detección de ciclos. |
| **Reloj manipulado** | Timestamps del servidor, no del cliente. |
| **Doble gasto** | Transacción atómica y bloqueo por lote. |

## 4. Componentes

```
┌─────────────────────────────────────────────┐
│                 Frontend (web)              │
│  registro · catálogo · billetera · disputas │
└──────────────────┬──────────────────────────┘
                   │ HTTPS
┌──────────────────▼──────────────────────────┐
│                API Gateway                  │
│  auth · rate limit · validación · logging   │
└───┬──────────┬───────────┬──────────┬───────┘
    │          │           │          │
┌───▼───┐ ┌────▼────┐ ┌────▼────┐ ┌───▼────┐
│Identidad│ │Catálogo │ │Ledger   │ │Disputas│
│(KYC)   │ │ofertas  │ │lotes    │ │casos   │
└───┬───┘ └────┬────┘ └────┬────┘ └───┬────┘
    │          │           │          │
┌───▼──────────▼───────────▼──────────▼────┐
│         Base de datos (Postgres)          │
│  usuarios · ofertas · lotes · transacciones│
└──────────────────┬────────────────────────┘
                   │
┌──────────────────▼────────────────────────┐
│      Jobs: vencimiento · reputación       │
│      notificaciones · conciliación        │
└───────────────────────────────────────────┘
```

## 5. On-chain vs. off-chain

| Capa | MVP (off-chain) | Fase 3 (on-chain) |
|---|---|---|
| Registro de usuarios | Postgres | Postgres + prueba de identidad |
| Ofertas | Postgres | Postgres |
| Lotes y transferencias | Postgres con doble registro | Smart contract |
| Vencimiento | Job | Contrato + oráculo de tiempo |
| Reputación | Postgres | Postgres + anclaje de hash |
| Disputas | Postgres | Postgres + registro on-chain |
| Tesorería | Multisig | Multisig + contrato |

**Recomendación**: empezar off-chain. La blockchain agrega valor cuando hay múltiples organizaciones que no confían entre sí o cuando se necesita auditabilidad pública. Para un piloto de un solo territorio, no es necesario.

## 6. Modelo de datos mínimo

```sql
users (id, alias, contact, identity_status, created_at)
offers (id, user_id, title, category, price_credits, status, geo)
obligations (id, user_id, offer_id, amount, status, due_at)
lots (id, owner_id, amount, created_at, expires_at, status, obligation_id, parent_id)
transactions (id, from_user, to_user, lot_ids, amount, created_at, type)
disputes (id, transaction_id, opened_by, status, resolution, created_at)
events (id, type, payload, created_at)
```

## 7. Contrato inteligente (si se implementa)

### Estructura conceptual
```solidity
struct Lot {
    address owner;
    uint256 amount;
    uint64 createdAt;
    uint64 expiresAt;
    bool active;
    bytes32 obligationId;
}

function transfer(bytes32 lotId, address to, uint256 amount) external {
    Lot storage lot = lots[lotId];
    require(lot.active && lot.owner == msg.sender, "not owner");
    require(block.timestamp < lot.expiresAt, "expired");
    // partir el lote
    // crear nuevo lote para `to` con expiresAt = now + T
    // crear vuelto para msg.sender con expiresAt = now + T
}
```

### Consideraciones
- El tiempo en blockchain es aproximado (timestamp del bloque).
- El gas puede ser alto para muchas operaciones.
- La upgradability es compleja; mejor un contrato simple y migrable.
- La privacidad es limitada: las transacciones son públicas.

## 8. Eventos y observabilidad

| Evento | Uso |
|---|---|
| `user.registered` | Alta |
| `offer.published` | Catálogo |
| `credit.issued` | Emisión |
| `credit.transferred` | Transferencia |
| `credit.expired` | Vencimiento |
| `obligation.fulfilled` | Cumplimiento |
| `obligation.defaulted` | Incumplimiento |
| `dispute.opened` / `dispute.resolved` | Disputas |

Estos eventos alimentan métricas, notificaciones y auditoría.

## 9. Preguntas abiertas

- ¿El vencimiento se mide desde la emisión o desde la última transferencia? (Propuesto: desde la última transferencia.)
- ¿El vuelto también renueva? (Propuesto: sí.)
- ¿Qué pasa si el lote se transfiere a sí mismo? (Bloquear.)
- ¿Cómo se maneja la fracción mínima?
- ¿Se permite transferir lotes vencidos? (No.)
- ¿Cómo se reconcilia con la contabilidad legal?

## Enlaces

- [[03 - Direccion y Estrategia/Modelo - Circuito de creditos|Modelo — Circuito de créditos]]
- [[07 - Tecnologia y Producto/Stack y decisiones tecnicas|Stack y decisiones técnicas]]
- [[07 - Tecnologia y Producto/Producto - App MVP|Producto — App MVP]]
- [[07 - Tecnologia y Producto/Seguridad y privacidad|Seguridad y privacidad]]
