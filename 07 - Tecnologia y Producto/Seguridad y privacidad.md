---
tipo: politica
estado: borrador
area: tecnologia
actualizado: 2026-11-20
---

# Seguridad y privacidad

> [!warning] Documento en borrador
> No hay sistema en producción. Estas son las bases para diseñar la seguridad desde el inicio, no una auditoría.

## Modelo de amenazas

| Amenaza | Impacto | Probabilidad | Mitigación |
|---|---|---|---|
| Robo de cuenta | Alto | Media | OTP, passkeys, alertas |
| Suplantación de identidad | Alto | Media | KYC, verificación |
| Fuga de datos | Alto | Media | Cifrado, mínimo privilegio |
| Doble gasto | Alto | Baja | Transacciones ACID |
| Manipulación de vencimiento | Medio | Media | Reloj del servidor |
| Sybil (cuentas múltiples) | Medio | Alta | Verificación, límites |
| Colusión | Medio | Media | Grafo, detección |
| Ataque al smart contract | Alto | Baja | Auditoría, límites |
| Phishing | Medio | Alta | Educación, dominios |
| Denegación de servicio | Medio | Media | Rate limit, CDN |

## Principios

1. **Privacidad por diseño**: solo los datos necesarios.
2. **Mínimo privilegio**: cada rol accede a lo mínimo.
3. **Defensa en profundidad**: varias capas.
4. **Cifrado**: en tránsito y en reposo.
5. **Auditoría**: todo movimiento queda registrado.
6. **Recuperación**: planes de backup y restauración.
7. **Transparencia**: política clara para el usuario.

## Identidad y acceso

- Autenticación con OTP o passkey.
- Sesiones con expiración.
- Bloqueo por intentos fallidos.
- Roles: usuario, administrador, árbitro, auditor.
- Registro de accesos.

## Datos

| Tipo | Sensibilidad | Tratamiento |
|---|---|---|
| Seudónimo | Baja | Público |
| Contacto | Media | Cifrado, acceso restringido |
| Documento | Alta | Cifrado, KYC, acceso mínimo |
| Transacciones | Media | Registro, seudonimizado |
| Disputas | Alta | Acceso comité/legal |
| Logs | Media | Retención limitada |

## Billetera

- Lotes con estado y vencimiento.
- Transacciones atómicas.
- Bloqueo optimista o pesimista.
- Conciliación diaria.
- Alertas de saldo negativo o inconsistente.

## Smart contracts (si se usan)

- Código simple y auditado.
- Límites de gas y de operaciones.
- Pausa de emergencia.
- Actualización con multisig.
- Pruebas exhaustivas y testnet.

## Operación

- Backups diarios cifrados.
- Restauración probada.
- Monitoreo de errores y latencia.
- Alertas de seguridad.
- Plan de respuesta a incidentes.
- Revisión de dependencias.

## Respuesta a incidentes

1. **Detectar**: monitoreo y reportes.
2. **Contener**: bloquear cuentas o contratos.
3. **Evaluar**: alcance y datos afectados.
4. **Notificar**: usuarios y autoridad si corresponde.
5. **Corregir**: parche y revisión.
6. **Documentar**: post-mortem público.

## Cumplimiento

- Ley 25.326 de datos personales.
- Consentimiento informado.
- Derecho de acceso, rectificación y supresión.
- Registro de bases de datos si corresponde.
- Política de retención.

## Enlaces

- [[13 - Legal y Cumplimiento/Proteccion de datos y privacidad|Protección de datos]]
- [[02 - Gobernanza y Comunidad/Identidad y confianza|Identidad y confianza]]
- [[07 - Tecnologia y Producto/Arquitectura - Creditos con vencimiento|Arquitectura]]
