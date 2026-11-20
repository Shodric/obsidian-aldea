---
tipo: riesgo
estado: activo
area: legal
severidad: alta
probabilidad: media
responsable: Legal / Tecnologia
actualizado: 2026-11-20
---

# Riesgo — Datos personales e identidad

## Descripción
El sistema necesita identidad para sancionar, pero el catálogo debe proteger la privacidad. Un mal diseño puede exponer datos personales, permitir discriminación o incumplir la Ley 25.326. También existe el riesgo de suplantación y cuentas múltiples.

## Impacto
- Sanciones legales y pérdida de confianza.
- Exposición de personas vulnerables.
- Fraude y manipulación del sistema.
- Imposibilidad de sancionar si no hay identidad verificable.

## Probabilidad
**Media**. El equilibrio entre privacidad y rendición de cuentas es delicado y requiere diseño.

## Mitigación
1. **Minimización**: solo los datos necesarios; seudónimo en el catálogo.
2. **Separación de capas**: identidad verificada en un registro cerrado; perfil público con seudónimo.
3. **Consentimiento informado** y política de privacidad clara.
4. **Cifrado** en tránsito y en reposo; acceso por roles.
5. **Verificación de identidad** solo para sanciones, contratos y retiros.
6. **Prevención de sybil**: un humano, una cuenta; teléfono o documento según el caso.
7. **Derecho de acceso, rectificación y baja**.
8. **Auditoría** periódica de accesos y datos.

## Indicador de alerta
- Datos personales visibles en el catálogo público.
- Cuentas duplicadas o suplantación.
- Incidentes de seguridad o filtraciones.
- Reclamos por discriminación o exposición.

## Enlaces
- [[13 - Legal y Cumplimiento/Proteccion de datos y privacidad|Protección de datos y privacidad]]
- [[02 - Gobernanza y Comunidad/Identidad y confianza|Identidad y confianza]]
- [[07 - Tecnologia y Producto/Seguridad y privacidad|Seguridad y privacidad]]
