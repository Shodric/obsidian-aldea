---
tipo: documento
estado: borrador
area: tecnologia
actualizado: 2026-11-20
---

# Producto — App MVP

> [!info] Principio de producto
> La app debe ser tan simple que una persona que nunca usó una billetera digital pueda completar su primer intercambio en menos de 5 minutos, con ayuda de una guía.

## Usuarios

### Persona 1 — “El oficio”
- **Perfil**: albañil, parquero, plomero, electricista, costurera.
- **Necesidad**: conseguir clientes sin depender de pesos.
- **Dolor**: no sabe cómo mostrar su oficio; le da vergüenza pedir.
- **Éxito**: recibe su primer pedido en la primera semana.

### Persona 2 — “La productora”
- **Perfil**: vende comida, panificados, conservas, artesanías.
- **Necesidad**: vender más y conseguir insumos.
- **Dolor**: competencia homogénea; precios bajos.
- **Éxito**: rota su producción y compra lo que necesita.

### Persona 3 — “El que no tiene nada”
- **Perfil**: desempleado, subocupado, persona mayor.
- **Necesidad**: acceder a bienes básicos sin dinero.
- **Dolor**: no tiene nada que ofrecer; se siente excluido.
- **Éxito**: encuentra algo que puede ofrecer (tiempo, ayuda, cosas usadas).

### Persona 4 — “El administrador”
- **Perfil**: comité, referente territorial, soporte.
- **Necesidad**: gestionar altas, ofertas, disputas y métricas.
- **Dolor**: procesos manuales y conflictos.
- **Éxito**: resuelve todo desde un panel.

## Historias de usuario

### Registro
- Como persona, quiero registrarme con un seudónimo y mi contacto para entrar al circuito sin exponer mis datos.
- Como persona, quiero verificar mi identidad una sola vez para poder operar y ser sancionable.
- Como persona, quiero entender las reglas antes de aceptar.

### Oferta
- Como oferente, quiero publicar qué ofrezco, con foto, descripción y precio en créditos.
- Como oferente, quiero saber cuántos créditos recibo y cuándo vencen.
- Como oferente, quiero pausar o editar mi oferta.

### Catálogo
- Como comprador, quiero ver las ofertas cerca de mí, filtradas por categoría y precio.
- Como comprador, quiero ver la reputación y la antigüedad del oferente.
- Como comprador, quiero saber si me alcanzan mis créditos antes de comprar.

### Compra
- Como comprador, quiero pagar con créditos y recibir un código de confirmación.
- Como comprador, quiero confirmar la entrega para cerrar la transacción.
- Como comprador, quiero abrir una disputa si algo salió mal.

### Billetera
- Como usuario, quiero ver mi saldo total y cuánto vence pronto.
- Como usuario, quiero ver el historial de mis créditos.
- Como usuario, quiero recibir un aviso antes de que venza mi crédito.

### Administración
- Como administrador, quiero ver usuarios, ofertas y obligaciones.
- Como administrador, quiero resolver disputas y aplicar sanciones.
- Como administrador, quiero exportar métricas.

## Flujos principales

### Alta y primera oferta
```
Inicio → Registro (seudónimo + contacto) → Verificación → Aceptar reglas
→ Crear oferta → Ver créditos asignados → Ver catálogo → Fin
```

### Intercambio
```
Catálogo → Ver oferta → Confirmar compra → Pagar créditos
→ Recibir código → Encuentro/entrega → Confirmar código → Calificar → Fin
```

### Vencimiento
```
Job diario → Detectar lotes por vencer → Notificar (7, 3, 1 día)
→ Si vence: marcar expirado → Notificar → Actualizar saldo
```

## Pantallas mínimas

1. **Onboarding**: qué es Aldea, cómo funciona, reglas.
2. **Registro**: seudónimo, contacto, territorio.
3. **Verificación**: documento/teléfono.
4. **Home**: saldo, vencimientos próximos, accesos.
5. **Catálogo**: lista, filtros, búsqueda, mapa.
6. **Detalle de oferta**: fotos, precio, reputación, botón comprar.
7. **Confirmación**: resumen, código, instrucciones.
8. **Billetera**: lotes, vencimientos, historial.
9. **Mis ofertas**: crear, editar, pausar.
10. **Disputas**: abrir, ver estado, responder.
11. **Perfil**: datos, reputación, configuración.
12. **Admin**: usuarios, ofertas, disputas, métricas.

## Requisitos funcionales

| ID | Requisito | Prioridad |
|---|---|---|
| RF-01 | Registro con seudónimo y contacto | Must |
| RF-02 | Verificación de identidad | Must |
| RF-03 | Publicar oferta con precio en créditos | Must |
| RF-04 | Emitir créditos contra oferta | Must |
| RF-05 | Catálogo geolocalizado | Must |
| RF-06 | Compra con créditos | Must |
| RF-07 | Confirmación con código | Must |
| RF-08 | Vencimiento y notificación | Must |
| RF-09 | Historial de transacciones | Must |
| RF-10 | Panel de administración | Must |
| RF-11 | Disputas | Should |
| RF-12 | Reputación | Should |
| RF-13 | Notificaciones push | Could |
| RF-14 | Mapa interactivo | Could |

## Requisitos no funcionales

- **Usabilidad**: primera operación sin ayuda en < 5 minutos.
- **Accesibilidad**: letra grande, contraste, lenguaje simple.
- **Rendimiento**: carga < 3 segundos en 3G.
- **Disponibilidad**: 99% en horario de operación.
- **Seguridad**: cifrado, autenticación, auditoría.
- **Privacidad**: seudónimo por defecto; datos mínimos.
- **Compatibilidad**: navegadores móviles modernos; PWA.

## Fuera de alcance del MVP

- Token de recompensa.
- Apps nativas.
- Integración bancaria.
- Gobernanza on-chain.
- Múltiples territorios.
- Facturación.
- Chat interno (usar WhatsApp).

## Métricas de producto

| Métrica | Meta |
|---|---|
| Tiempo de registro | < 3 min |
| Tiempo hasta primera oferta | < 10 min |
| Tasa de activación | > 60% |
| Tasa de conversión de catálogo a compra | > 10% |
| Tasa de confirmación de entrega | > 90% |
| Retención a 4 semanas | > 30% |

## Enlaces

- [[07 - Tecnologia y Producto/Arquitectura - Creditos con vencimiento|Arquitectura]]
- [[07 - Tecnologia y Producto/Stack y decisiones tecnicas|Stack]]
- [[12 - Procesos y SOPs/SOP - Alta de oferta|SOP — Alta de oferta]]
- [[12 - Procesos y SOPs/SOP - Intercambio y confirmacion|SOP — Intercambio y confirmación]]
