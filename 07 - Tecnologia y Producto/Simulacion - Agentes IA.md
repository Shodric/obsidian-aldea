---
tipo: documento
estado: borrador
area: tecnologia
actualizado: 2026-11-20
---

# Simulación — Agentes IA

> [!info] Propósito
> Usar agentes con personalidad, memoria y diálogo para explorar cómo se comporta el circuito de Aldea antes de construirlo. No es un modelo predictivo: es un **laboratorio de diseño**.

## Por qué agentes y no una planilla

Una simulación estadística (como la del JSX de Hernán) asume probabilidades fijas. Un agente con LLM puede:
- Cambiar de opinión al conversar.
- Detecta atajos y oportunidades.
- Cooperar, competir o hacer trampa.
- Olvidar y volver a aprender.

Eso permite ver **emergentes** que una planilla no muestra: monopolios, colusión, abandono, innovación.

## Perfiles de agente

| Perfil | Motivación | Comportamiento esperado | % inicial |
|---|---|---|---|
| **Optimista** | Cree en el proyecto, quiere participar | Oferta variada, compra, invita | 30% |
| **Neutro** | Busca utilidad concreta | Participa si le conviene | 40% |
| **Especulativo** | Maximizar créditos | Acapara, negocia, busca arbitraje | 15% |
| **Escéptico** | Desconfía de la propuesta | Prueba poco, cuestiona, abandona | 15% |

Cada agente tiene:
- **Identidad**: nombre, edad, barrio, oficio.
- **Recursos**: tiempo, habilidades, productos, créditos.
- **Necesidades**: comida, arreglos, clases, ropa.
- **Personalidad**: confianza, aversión al riesgo, sociabilidad.
- **Memoria**: conversaciones, transacciones, percepciones.
- **Objetivo**: sobrevivir, prosperar, acumular, aprender.

## Entorno

- **Mercado**: catálogo de ofertas con precios en créditos.
- **Ciclo**: 4 semanas; el crédito vence a los 30 días.
- **Reglas**: emisión contra oferta, techo, sanciones.
- **Espacio**: un barrio con 30–50 agentes.
- **Tiempo**: cada turno representa un día.
- **Comunicación**: diálogo 1 a 1 y grupo.

## Bucle de simulación

```
Para cada día:
  1. Cada agente observa el mercado y su billetera.
  2. Decide: ofrecer, comprar, esperar, conversar.
  3. Ejecuta acciones.
  4. Se aplican reglas (emisión, transferencia, vencimiento).
  5. Se registran eventos y métricas.
  6. Se actualiza la memoria.
```

## Métricas

| Métrica | Qué mide |
|---|---|
| Intercambios totales | Volumen del circuito |
| Intercambios por agente | Equidad |
| Créditos emitidos / usados / vencidos | Eficiencia |
| Tiempo promedio de circulación | Velocidad |
| Concentración (Gini) | Desigualdad |
| Tasa de incumplimiento | Confianza |
| Categorías activas | Variedad |
| Conflictos y sanciones | Gobernanza |
| Satisfacción declarada | Percepción |

## Diseño de prompts

Cada agente recibe:
- **System prompt**: quién es, qué quiere, cómo decide.
- **Contexto**: estado del mercado, su billetera, sus necesidades.
- **Memoria**: resumen de interacciones previas.
- **Instrucción**: “¿Qué hacés hoy? Respondé con una acción y una frase.”

Ejemplo:
```
Sos Marta, 54 años, cocinera. Vendés empanadas y necesitás arreglar
la canilla. Tenés 3.000 créditos que vencen en 12 días. En el catálogo
hay un plomero a 2.500. ¿Qué hacés?
```

## Modelos y costos

| Opción | Ventaja | Costo | Uso |
|---|---|---|---|
| Modelos gratuitos | Sin costo | Límite de llamadas | Prueba inicial |
| DeepSeek | Buen costo/calidad | ~USD 0,14 por 1M tokens (verificar) | Corrida principal |
| Modelos premium | Mejor razonamiento | Alto | Casos específicos |

**Presupuesto**: USD 10–30 para la primera fase. Con caché se reduce el costo.

## Plan de experimentos

| Experimento | Variable | Hipótesis |
|---|---|---|
| E1 | 10 agentes, perfiles balanceados | El circuito arranca |
| E2 | 30 agentes, 15% especuladores | Aparece acaparamiento |
| E3 | 30 agentes, 30% escépticos | Baja la participación |
| E4 | Vencimiento 15 vs. 30 vs. 60 días | El plazo afecta la circulación |
| E5 | Precio fijo vs. negociado | El regateo distorsiona |
| E6 | Sanción fuerte vs. débil | La sanción sostiene la confianza |

## Salidas esperadas

1. **Informe de simulación**: resultados por escenario.
2. **Ranking de parámetros**: qué valores funcionan mejor.
3. **Lista de puntos de bloqueo**: dónde se traba el circuito.
4. **Detección de atajos**: qué hacen los agentes para romper el sistema.
5. **Recomendaciones**: qué cambiar antes del MVP.

## Riesgos

- **Sesgo de cooperación**: los LLM tienden a colaborar; hay que forzar conflicto.
- **Olvido**: los agentes pierden memoria; hay que resumir.
- **Costo**: muchas llamadas; usar caché y modelos baratos.
- **Abstracción**: el barrio simulado no es el barrio real.
- **Sobreinterpretación**: los resultados no son profecías.

## Enlaces

- [[08 - Proyectos/Activos/Proyecto - Simulacion agentica/Proyecto - Simulacion agentica|Proyecto — Simulación agéntica]]
- [[10 - Modelo Economico y Tokenomia/Simulacion - Parametros y resultados|Parámetros y resultados]]
- [[03 - Direccion y Estrategia/Modelo - Circuito de creditos|Modelo — Circuito de créditos]]
