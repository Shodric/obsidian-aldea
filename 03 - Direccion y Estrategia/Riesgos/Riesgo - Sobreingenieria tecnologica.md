---
tipo: riesgo
estado: activo
area: tecnologia
severidad: media
probabilidad: alta
responsable: Rodrigo
actualizado: 2026-11-20
---

# Riesgo — Sobreingeniería tecnológica

## Descripción
Construir una solución blockchain compleja antes de validar el circuito. Smart contracts costosos, wallets difíciles de usar, gobernanza on-chain prematura y una arquitectura que no resiste cambios.

## Impacto
- Costos y tiempos de desarrollo desproporcionados.
- Mala experiencia de usuario y baja adopción.
- Dificultad para cambiar reglas económicas.
- Dependencia de una tecnología que no aporta valor al MVP.

## Probabilidad
**Alta**. Es un riesgo clásico en proyectos web3: la tecnología se vuelve el fin y no el medio. Hernán y Rodrigo ya acordaron empezar simple, pero la presión puede reaparecer.

## Mitigación
1. **Regla de oro**: blockchain solo si resuelve un problema real de confianza o trazabilidad.
2. **MVP con base de datos** y lógica de vencimiento, si alcanza.
3. **Interfaz simple**: la blockchain debe ser invisible; la wallet, recuperable.
4. **Arquitectura modular**: separar reglas económicas, registro y pagos.
5. **Decisiones técnicas documentadas** con costo, beneficio y alternativa.
6. **Revisión por pares** antes de invertir en infraestructura.
7. **Presupuesto acotado** para Fase 2.

## Indicador de alerta
- Más de 3 meses de desarrollo sin usuarios reales.
- Costos de gas o infraestructura superiores al presupuesto.
- Usuarios que no pueden completar el registro sin ayuda.
- Reglas económicas que no se pueden cambiar sin migrar contratos.

## Enlaces
- [[07 - Tecnologia y Producto/Arquitectura - Creditos con vencimiento|Arquitectura]]
- [[07 - Tecnologia y Producto/Stack y decisiones tecnicas|Stack y decisiones técnicas]]
- [[07 - Tecnologia y Producto/Producto - App MVP|Producto — App MVP]]
