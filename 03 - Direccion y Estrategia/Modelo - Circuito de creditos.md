---
tipo: modelo
estado: borrador
area: economia
fecha: 2026-11
version: 0.1
actualizado: 2026-11-20
---

# Modelo — Circuito de créditos

> [!info] Qué es este documento
> Explica el mecanismo económico de Aldea con precisión suficiente para diseñar el MVP, la simulación y los contratos. **No es una decisión aprobada**: es el modelo de trabajo. Las reglas marcadas `por confirmar` requieren validación con Hernán, legal y el piloto.

## 1. Principios

1. **La oferta respalda la emisión**: nadie recibe créditos si no ofrece algo.
2. **El crédito es gratuito**: no se compra con pesos ni se cambia por pesos dentro del sistema.
3. **El crédito vence en posesión**: si queda quieto, se pierde; si se transfiere, se renueva.
4. **La obligación no vence**: el compromiso de entregar sobrevive al crédito.
5. **La comunidad es la contraparte**: la DAO/asociación emite, garantiza y reclama.
6. **El precio se fija antes**: no hay regateo ni subasta.
7. **El sistema es finito por ciclo**: se abre, circula y cierra; no hay emisión infinita.

## 2. Actores y roles

| Actor | Rol | Responsabilidad |
|---|---|---|
| **Participante/prosumidor** | Ofrece y compra | Entregar lo ofrecido; usar el crédito antes de que venza |
| **DAO/asociación** | Emisor y contraparte | Emitir créditos, mantener el registro, reclamar obligaciones |
| **Comité ejecutivo** | Operación | Altas, catálogo, disputas, comunicación |
| **Árbitro/mediador** | Resolución de conflictos | Mediar, aplicar sanciones, proponer mejoras |
| **Municipio/aliado** | Legitimidad y apoyo | Mediación, espacio, validación, posibles beneficios |
| **Desarrollador** | Tecnología | Billetera, contratos, panel, datos |

## 3. Unidades

### 3.1 Crédito de intercambio (ALDEA)
- **Naturaleza**: unidad de cuenta interna, fungible y divisible.
- **Emisión**: gratuita, contra oferta verificada.
- **Vencimiento**: en posesión, por plazo `T` (por confirmar; hipótesis: 30 días).
- **Transferencia**: al transferirse, el crédito se parte y el nuevo UTXO recibe un plazo renovado.
- **Alcance**: solo bienes y servicios del circuito. No convertible a pesos dentro del sistema.
- **Representación técnica**: UTXO con metadata de vencimiento; o registro en base de datos con la misma lógica.

### 3.2 Token de recompensa (fase 3, no MVP)
- **Naturaleza**: token permanente, fungible, sin vencimiento.
- **Emisión**: por participación sostenida, a definir.
- **Uso**: gobernanza, acceso a beneficios, posible intercambio externo.
- **Requisitos**: CNV, patrimonio, habilitaciones, diseño de emisión.
- **Estado**: **excluido del MVP**. Se evalúa después de la Fase 2.

## 4. Ciclo de vida del crédito

```
[Oferta verificada]
       ↓
[Emisión] → crédito con plazo T
       ↓
[Posesión] → el reloj corre; si llega a 0, se quema
       ↓
[Transferencia] → se parte; el nuevo UTXO recibe plazo T
       ↓
[Consumo] → el crédito se extingue; la obligación del emisor queda registrada
       ↓
[Cierre de ciclo] → se auditan obligaciones y se habilita la reinscripción
```

### Reglas de vencimiento
- **R1**: todo crédito nace con plazo `T` desde su emisión o desde su última transferencia.
- **R2**: al transferirse, el crédito se divide en el monto transferido y el vuelto; **ambos** renuevan su plazo.
- **R3**: al vencer, el crédito se quema y no genera derecho a reclamo.
- **R4**: la obligación del emisor **no se quema** con el crédito; queda en el registro de compromisos.
- **R5**: el plazo `T` es un parámetro de gobernanza; no se cambia durante un ciclo.

### Ejemplo numérico
- Ana ofrece 10 horas de jardinería a 1.000 créditos/hora → recibe **10.000 créditos**.
- Con esos créditos compra a Beto 20 docenas de empanadas a 400 créditos/docena → paga **8.000**; le quedan **2.000** de vuelto.
- Beto recibe **8.000** con plazo renovado. Ana conserva **2.000** con su plazo original.
- Beto usa **5.000** para pagarle a Carla por ropa; Carla recibe **5.000** con plazo nuevo.
- Si Ana no usa sus 2.000 antes del vencimiento, se queman. Su obligación de 10 horas sigue registrada hasta que entregue.

## 5. Precios y valor hora

### 5.1 Mecanismos posibles

| Mecanismo | Ventaja | Riesgo |
|---|---|---|
| **A. Valor hora único** | Simple, igualitario, fácil de explicar | No reconoce especialización; puede expulsar oficios calificados |
| **B. Escala por oficio** | Más justo con la especialización | Complejo, discrecional, requiere datos |
| **C. Precio declarado + conversión** | Flexible, usa el conocimiento local | Inflación de precios, comparabilidad difícil |

**Propuesta de trabajo**: empezar por **A** para el MVP, con una tabla de conversión para productos, y evaluar **B** en la Fase 2.

### 5.2 Ecuación base

```
valor_hora_promedio = promedio ponderado del valor de la hora en pesos
1 crédito = valor_hora_promedio / unidad_de_referencia
precio_créditos(producto) = precio_pesos(producto) / valor_crédito_en_pesos
```

- El valor de referencia se actualiza por ciclo, no durante el ciclo.
- El sistema puede aplicar un factor de ajuste por categoría (por confirmar).
- Los precios se publican antes del intercambio; no se negocian.

### 5.3 Límites
- **Piso**: monto mínimo por operación (por confirmar).
- **Techo por participante**: hipótesis 100.000 ARS equivalentes (a estudiar).
- **Techo por operación**: a definir.
- **Cantidad de ofertas activas**: a definir.

## 6. Obligación y DAO

### 6.1 Modelo de deuda
- La DAO emite el crédito **al vendedor** contra la promesa del comprador.
- El comprador queda en deuda con la **DAO**, no con el vendedor.
- La deuda se representa en un **contrato de compromiso** con estado: `pendiente`, `en curso`, `cumplido`, `incumplido`, `en disputa`.
- Al transferir el crédito, la deuda puede transferirse con él (endoso), según la regla que se defina.

### 6.2 Flujo de cumplimiento
1. El comprador recibe el bien/servicio y confirma con un código.
2. El vendedor recibe los créditos; el comprador recibe una obligación de entrega.
3. El comprador cumple su obligación (trabajo, producto o transferencia a otro).
4. La DAO marca la obligación como cumplida y actualiza la reputación.

### 6.3 Incumplimiento
| Situación | Respuesta | Responsable |
|---|---|---|
| No entrega en plazo | Aviso, plazo extra, registro | Comité |
| Rechaza ofertas repetidamente | Devaluación del crédito (ej. 5% por rechazo) | Protocolo |
| Incumple reiteradamente | Exclusión del ciclo; reincorporación con pago | Comité/DAO |
| Disputa sobre calidad | Mediación; árbitro; sanción | Árbitro |
| Fraude | Exclusión, reclamo legal, registro | DAO + legal |

> [!warning] Límite del modelo
> No se puede sancionar a quien no tiene bienes. La sanción real es **perder acceso al circuito** y la **reputación**. El respaldo legal (contrato, mediación) es lo que le da fuerza.

## 7. Parámetros de diseño

| Parámetro | Valor propuesto | Estado | Nota |
|---|---|---|---|
| Plazo de vencimiento `T` | 30 días | Hipótesis | A calibrar en simulación |
| Duración del ciclo | 4 semanas | Hipótesis | Alineado con `T` |
| Créditos iniciales | 0 | Propuesta | Se emiten contra oferta |
| Piso por operación | Por confirmar | Pendiente | Evitar microtransacciones |
| Techo por participante | 100.000 ARS eq. | Ejemplo | A estudiar |
| Piso por participante | 20.000 ARS eq. | Ejemplo | A estudiar |
| Devaluación por rechazo | 5% | Propuesta | Acumulativa |
| Comisión por intercambio | 0% | Propuesta | No cobrar en MVP |
| Ingreso básico en créditos | 10.000 ARS/mes | Exploratoria | Solo para quienes no pueden ofrecer |
| Token de recompensa | No en MVP | Decisión de trabajo | Fase 3 |

## 8. Casos borde

| Caso | Pregunta | Respuesta propuesta |
|---|---|---|
| **Emisión sin oferta** | ¿Puedo emitir si no tengo nada? | No. La emisión requiere oferta verificada. |
| **Oferta falsa** | ¿Qué pasa si ofrezco lo que no tengo? | Verificación, reputación y sanción; el crédito se emite igual, pero la obligación queda. |
| **Crédito vencido** | ¿Puedo reclamar? | No. El crédito se quema; la obligación del emisor sigue. |
| **Todos rechazan** | ¿Se cae el sistema? | Es señal de que el grupo no es adecuado; el circuito se cierra y se reabre con otros. |
| **Precio inflado** | ¿Quién lo controla? | El sistema puede rechazar o ajustar; regla a definir. |
| **Intercambio fuera del sistema** | ¿Se puede? | No se promueve; el diseño no lo impide, pero no hay garantía. |
| **Usuario sin smartphone** | ¿Puede participar? | Mesa de ayuda, registro asistido, tarjetas físicas (a evaluar). |
| **Muerte del usuario** | ¿Qué pasa con su deuda? | A definir con legal; probablemente se extingue. |
| **Cierre del proyecto** | ¿Qué pasa con los créditos? | Se queman; las obligaciones se liquidan según contrato. |

## 9. Preguntas abiertas

1. ¿El crédito es endosable con la deuda o la deuda queda fija en el emisor original?
2. ¿Cómo se actualiza el valor de referencia sin generar inflación?
3. ¿Qué pasa si un participante ofrece un servicio que nadie demanda?
4. ¿Cómo se mide la reputación sin crear un “Veraz” informal?
5. ¿La DAO puede emitir sin respaldo legal? ¿Qué vehículo se usa?
6. ¿Cómo se articula el crédito con el municipio (ABL, tasas, programas)?
7. ¿Qué pasa con el IVA y las obligaciones fiscales de los participantes?
8. ¿Cómo se previene el lavado de activos si no hay dinero?
9. ¿El token de recompensa puede existir sin violar la normativa de valores?
10. ¿Cómo se sale del sistema sin perjudicar a los que confiaron?

## 10. Enlaces

- [[03 - Direccion y Estrategia/2026-11 - Documento Ejecutivo Aldea|Documento Ejecutivo]]
- [[10 - Modelo Economico y Tokenomia/Modelo - Creditos de intercambio|Créditos de intercambio]]
- [[10 - Modelo Economico y Tokenomia/Mecanismo - Precios y valor hora|Precios y valor hora]]
- [[07 - Tecnologia y Producto/Arquitectura - Creditos con vencimiento|Arquitectura — Créditos con vencimiento]]
- [[02 - Gobernanza y Comunidad/Reglas de membresia y sanciones|Reglas de membresía y sanciones]]
- [[13 - Legal y Cumplimiento/Marco regulatorio - Tokens y trueque en Argentina|Marco regulatorio]]
