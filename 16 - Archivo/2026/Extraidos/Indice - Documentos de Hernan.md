---
tipo: indice
estado: activo
area: archivo
actualizado: 2026-11-20
---

# Documentos de Hernán — índice y lectura rápida

> [!info] Qué es esta nota
> Los documentos que Hernán prometió en la llamada llegaron a `16 - Archivo/2026/`. Esta nota los cataloga, resume y marca qué confirman del vault y qué conviene revisar. Los originales no se editan; las copias de trabajo están en `Extraidos/`.

## Documentos

| Documento | Original | Copia de trabajo | Qué es |
|---|---|---|---|
| Aproximación técnica v6 — con token de recompensa | `Aldea_Aproximacion_Tecnica_v6.docx` | [[16 - Archivo/2026/Extraidos/Aldea_Aproximacion_Tecnica_v6]] | Arquitectura funcional con dos tokens |
| Aproximación técnica v6 — sin token de recompensa | `Aldea_Aproximacion_Tecnica_v6_sin_recompensa.docx` | [[16 - Archivo/2026/Extraidos/Aldea_Aproximacion_Tecnica_v6_sin_recompensa]] | Arquitectura funcional con un solo token |
| Pitch empresarial v2 — con token de recompensa | `Aldea_Pitch_Empresarial_v2.docx` | [[16 - Archivo/2026/Extraidos/Aldea_Pitch_Empresarial_v2]] | Pitch comercial con dos tokens |
| Pitch empresarial v2 — sin token de recompensa | `Aldea_Pitch_Empresarial_v2_sin_recompensa.docx` | [[16 - Archivo/2026/Extraidos/Aldea_Pitch_Empresarial_v2_sin_recompensa]] | Pitch comercial con un solo token |
| Proyecto Moneda Social (2018 + apéndice 2024) | `moneda social.doc` | [[16 - Archivo/2026/Extraidos/moneda social]] | Modelo original, fundamentos y análisis de valor |

## Qué confirman del vault

- **Caducidad individual por lote**: cada token recibido tiene su propia fecha de vencimiento; no vence toda la emisión a la vez.
- **Gasto FIFO**: se usan primero los lotes más próximos a vencer.
- **Transferencia con reloj nuevo**: al pagar, el receptor recibe un lote nuevo con su propio plazo.
- **Compromiso mínimo de venta**: el saldo inicial es proporcional a la oferta declarada y obliga a aceptar ventas por ese monto.
- **Sanción solo por negarse a vender**: no se sanciona la falta de demanda.
- **Zonas y ciclos**: el ciclo sigue siendo el marco de inscripción, evaluación y reparto; ya no es la fecha de vencimiento de todos los tokens.
- **Entrega inmediata y diferida**: el pago puede confirmar la entrega o quedar pendiente.
- **Token de recompensa separado**: no caduca y requiere análisis legal; no es el token de intercambio.
- **Arquitectura simple**: app React Native + backend Supabase/Firebase; no exige blockchain para el MVP.
- **Estimación**: MVP funcional de 9–13 semanas para 1–2 desarrolladores.

## Qué ajusta o profundiza

| Tema | Lo que dice el documento | Implicancia para el vault |
|---|---|---|
| Emisión inicial | Es proporcional a la oferta declarada y se fija como compromiso mínimo | Hay que precisar la fórmula y el techo en `Mecanismo - Precios y valor hora` y en el modelo del circuito |
| Sanción | Se activa por rechazo explícito o silencio confirmado, no por falta de demanda | La simulación debe distinguir rechazo de ausencia de demanda |
| Vencimiento | Cada lote tiene plazo completo desde su recepción | La simulación debe modelar lotes, no un saldo único |
| Token de recompensa | Sigue presente en una versión de los documentos | La decisión del MVP sin token sigue siendo una propuesta, no una decisión de Hernán |
| Alcance del MVP | Registro, zonas, lotes, compromiso, catálogo y transacciones inmediatas | El MVP técnico es más acotado que el documento ejecutivo actual |
| Stack | React Native + Supabase/Firebase | Coincide con la recomendación de empezar simple y sin blockchain |
| Piloto | 50–100 usuarios en una zona acotada | Ajustar el rango de 100–300 que figura en el roadmap |

## Qué falta

- [ ] Simulador JSX de Claude.
- [ ] Confirmar cuál de las dos versiones (con o sin token de recompensa) es la vigente para el MVP.
- [ ] Contrastar la fórmula de emisión inicial y el compromiso mínimo con el modelo del vault.
- [ ] Validar la estimación de 9–13 semanas y el stack con Rodrigo.
- [ ] Decidir si el piloto es de 50–100 o de 100–300 usuarios.

## Relación con la simulación agéntica

La simulación tiene que modelar:

- Lotes con vencimiento individual.
- Gasto FIFO.
- Emisión inicial proporcional a la oferta.
- Compromiso mínimo y rechazo de ventas.
- Diferencia entre no vender por falta de demanda y negarse a vender.
- Zonas y ciclos.
- Token de recompensa como escenario separado, no como parte del MVP.

## Enlaces

- [[16 - Archivo/Indice - Archivo|Índice del archivo]]
- [[08 - Proyectos/Activos/Proyecto - Simulacion agentica/Proyecto - Simulacion agentica|Proyecto — Simulación agéntica]]
- [[03 - Direccion y Estrategia/Modelo - Circuito de creditos|Modelo — Circuito de créditos]]
- [[10 - Modelo Economico y Tokenomia/Mecanismo - Precios y valor hora|Mecanismo — Precios y valor hora]]
