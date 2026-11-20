---
tipo: documento
estado: borrador
area: tecnologia
actualizado: 2026-11-20
---

# Stack y decisiones técnicas

> [!info] Estado
> Ninguna decisión técnica está cerrada. Este documento compara opciones y propone un camino por fases.

## Criterios

1. **Costo**: bajo o nulo para el MVP.
2. **Simplicidad**: pocas piezas, fáciles de mantener.
3. **Usabilidad**: mobile-first, rápida en 3G.
4. **Reemplazabilidad**: poder cambiar blockchain por base de datos y viceversa.
5. **Seguridad**: cifrado, auditoría, backups.
6. **Comunidad**: documentación y soporte.
7. **Soberanía**: código abierto, datos exportables.

## Opciones de arquitectura

| Opción | Ventaja | Desventaja | Recomendación |
|---|---|---|---|
| **A. Monolito web + Postgres** | Simple, barato, rápido | No descentralizado | **MVP** |
| **B. Monolito + smart contracts** | Trazabilidad pública | Costo, complejidad, privacidad | Fase 3 |
| **C. Microservicios** | Escalable | Complejo para el equipo | No ahora |
| **D. Híbrido (off-chain + anclaje)** | Equilibrio | Requiere diseño | Evaluar Fase 3 |

## Stack propuesto para el MVP

| Capa | Tecnología | Motivo |
|---|---|---|
| **Frontend** | Next.js + Tailwind | Rápido, PWA, buen ecosistema |
| **Backend** | Node.js + TypeScript o Python + FastAPI | Familiaridad, velocidad |
| **Base de datos** | PostgreSQL | Transacciones ACID, integridad |
| **Autenticación** | Email/WhatsApp + OTP | Baja fricción |
| **Identidad** | Proveedor KYC (a definir) | Verificación |
| **Almacenamiento** | S3 compatible | Fotos de ofertas |
| **Notificaciones** | WhatsApp Cloud API / email | Canal real |
| **Hosting** | Railway / Fly.io / VPS | Bajo costo |
| **Observabilidad** | Sentry + logs estructurados | Detección de errores |
| **CI/CD** | GitHub Actions | Automatización |

## Blockchain: cuándo y cómo

### Cuándo no usarla
- Un solo territorio.
- Un solo operador.
- Datos personales en el registro.
- Volumen bajo.

### Cuándo usarla
- Múltiples organizaciones que no confían entre sí.
- Necesidad de auditabilidad pública.
- Token de recompensa negociable.
- Gobernanza descentralizada real.

### Opciones
| Red | Ventaja | Desventaja |
|---|---|---|
| **Ethereum L2 (Base, Optimism, Arbitrum)** | Bajo costo, ecosistema | Complejidad, puentes |
| **Polygon** | Bajo costo, adoptado | Centralización relativa |
| **Solana** | Rápido, barato | Otro modelo mental |
| **Hyperledger / permissioned** | Privacidad, control | No descentralizado |
| **Bitcoin (con protocolo propio)** | UTXO nativo | Limitado para smart contracts |

**Recomendación**: no elegir blockchain hasta la Fase 3. Si se elige, empezar con una L2 de bajo costo y un contrato simple.

## Custodia de claves

| Opción | Ventaja | Desventaja |
|---|---|---|
| **Custodia del servidor** | Simple para el usuario | Riesgo de hackeo |
| **Wallet no custodial** | Soberanía | Difícil para usuarios |
| **Social recovery** | Equilibrio | Complejo |
| **Passkey** | Moderno, seguro | Soporte limitado |

**Recomendación**: custodia del servidor en el MVP, con opción de exportar y migrar a no custodial después.

## Datos y privacidad

- Separar identidad de perfil público.
- Cifrar datos sensibles.
- Minimizar datos.
- Exportación y borrado.
- Backups cifrados.

## Costos estimados

| Ítem | Mensual |
|---|---|
| Hosting | USD 10–50 |
| Base de datos | USD 0–25 |
| Almacenamiento | USD 0–10 |
| Notificaciones | USD 0–20 |
| Dominio | USD 1–2 |
| **Total** | **USD 11–107** |

## Decisiones pendientes

| Decisión | Opciones | Responsable | Fecha |
|---|---|---|---|
| Backend | Node vs. Python | Rodrigo | Por confirmar |
| KYC | Proveedor | Rodrigo/Legal | Por confirmar |
| Blockchain | Sí/No, cuál | Rodrigo | Fase 3 |
| Custodia | Server vs. no custodial | Rodrigo | Por confirmar |
| Notificaciones | WhatsApp vs. email | Rodrigo | Por confirmar |

## Enlaces

- [[07 - Tecnologia y Producto/Arquitectura - Creditos con vencimiento|Arquitectura]]
- [[07 - Tecnologia y Producto/Seguridad y privacidad|Seguridad y privacidad]]
- [[07 - Tecnologia y Producto/Producto - App MVP|Producto — App MVP]]
