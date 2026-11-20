---
tipo: modelo
estado: borrador
area: economia
actualizado: 2026-11-20
---

# Modelo — Créditos de intercambio

> [!info] Relación con otros documentos
> Este documento profundiza la **economía** del crédito. El mecanismo completo (actores, obligaciones, sanciones) está en [[03 - Direccion y Estrategia/Modelo - Circuito de creditos|Modelo — Circuito de créditos]].

## 1. Oferta y demanda de créditos

### Oferta
La oferta de créditos es **endógena**: se crea cuando un participante publica una oferta y recibe créditos por ella.

```
Oferta de créditos = Σ (valor de las ofertas activas)
```

No hay una autoridad que emita de la nada. Cada crédito tiene detrás un compromiso de entrega.

### Demanda
La demanda de créditos viene de:
- Personas que quieren comprar bienes o servicios.
- Personas que necesitan pagar una obligación.
- Personas que quieren evitar el vencimiento.

### Equilibrio
Si la oferta crece más rápido que la demanda, hay créditos que no encuentran qué comprar y vencen. Si la demanda crece más rápido, faltan créditos y el circuito se frena.

**Señal de equilibrio**: tasa de vencimiento baja y tiempo de circulación estable.

## 2. Velocidad de circulación

```
V = volumen de intercambios / stock promedio de créditos
```

- **V baja**: créditos atesorados, circuito lento.
- **V alta**: créditos circulando, circuito dinámico.
- **V excesiva**: puede indicar inflación o desconfianza.

El vencimiento en posesión actúa directamente sobre `V`: cuanto más corto es `T`, más rápido se gasta.

## 3. Ecuación de intercambio adaptada

```
M × V = P × Q
```

| Variable | Significado |
|---|---|
| `M` | Stock de créditos activos |
| `V` | Velocidad de circulación |
| `P` | Precio promedio en créditos |
| `Q` | Cantidad de bienes y servicios intercambiados |

Si `M` crece sin que crezcan `Q` o `V`, los precios en créditos suben (inflación interna). El techo por participante y el vencimiento limitan `M`.

## 4. Parámetros y su efecto

| Parámetro | Aumenta | Disminuye | Efecto deseado |
|---|---|---|---|
| Plazo `T` | Atesoramiento | Circulación | `T` corto → más velocidad |
| Techo por participante | Oferta | Concentración | Limita riesgo |
| Piso por operación | Transacciones grandes | Microtransacciones | Eficiencia |
| Devaluación por rechazo | Costo de rechazar | Aceptación | Incentiva aceptar |
| Duración del ciclo | Estabilidad | Renovación | Equilibrio |

## 5. Ejemplo de circuito

Supongamos un barrio con 50 participantes y un valor hora de referencia de 3.000 ARS.

| Participante | Oferta | Valor | Créditos |
|---|---|---|---|
| Ana | 10 h de jardinería | 30.000 ARS | 300 |
| Beto | 20 docenas de empanadas | 8.000 ARS | 80 |
| Carla | 5 blusas | 15.000 ARS | 150 |
| Diego | 4 h de plomería | 12.000 ARS | 120 |

- Ana compra 4 docenas a Beto: paga 16 créditos. Beto recibe 16 con plazo renovado.
- Beto compra 2 blusas a Carla: paga 60 créditos.
- Carla contrata a Diego: paga 120 créditos.
- Diego contrata a Ana: paga 30 créditos.
- Ana vuelve a tener créditos y los usa antes de que venzan.

**Resultado**: el circuito gira, todos intercambian y nadie acumula de más.

## 6. Riesgos económicos

| Riesgo | Señal | Mitigación |
|---|---|---|
| **Inflación interna** | Precios suben sin mejora de oferta | Techo, auditoría, ajuste |
| **Deflación** | Nadie gasta, todos esperan | Vencimiento corto, incentivos |
| **Concentración** | Pocos acumulan mucho | Techo, Gini, alertas |
| **Desintermediación** | Intercambios fuera del sistema | Precio fijo, confianza |
| **Free riding** | Compran y no entregan | Identidad, sanción, reputación |
| **Colapso de confianza** | Abandono masivo | Gobernanza, mediación, transparencia |

## 7. Indicadores

| Indicador | Fórmula | Meta |
|---|---|---|
| Tasa de vencimiento | créditos vencidos / emitidos | < 20% |
| Velocidad | intercambios / stock | > 1 por ciclo |
| Concentración | Gini de saldos | < 0.5 |
| Cobertura | usuarios con al menos 1 intercambio | > 50% |
| Retención | usuarios activos mes 2 / mes 1 | > 30% |
| Equilibrio | oferta / demanda | 0.8–1.2 |

## 8. Preguntas abiertas

- ¿Cómo se ajusta `T` sin generar shocks?
- ¿Qué pasa si la oferta supera la demanda de forma estructural?
- ¿Cómo se mide la inflación interna?
- ¿Se puede usar un índice de precios local?
- ¿Qué rol juega el ingreso básico en créditos?

## Enlaces

- [[03 - Direccion y Estrategia/Modelo - Circuito de creditos|Modelo — Circuito de créditos]]
- [[10 - Modelo Economico y Tokenomia/Mecanismo - Precios y valor hora|Precios y valor hora]]
- [[15 - Reportes e Indicadores/KPIs - Circuito|KPIs del circuito]]
