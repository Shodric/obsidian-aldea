---
tipo: modelo
estado: borrador
area: economia
actualizado: 2026-11-20
---

# Mecanismo — Precios y valor hora

> [!warning] Cifras de ejemplo
> Los valores en pesos son ilustrativos y no representan precios reales del territorio. La calibración se hace con datos del piloto.

## 1. La pregunta

¿Cómo se traduce el valor de un producto o servicio a créditos, sin dinero de por medio y sin regateo?

## 2. Ecuación base

```
H = valor de la hora de trabajo de referencia (ARS/hora)
U = unidad de crédito (ARS por crédito)
precio_créditos = precio_ARS / U
```

Ejemplo: si `H = 3.000 ARS/hora` y `U = 100 ARS`, entonces una hora de trabajo vale **30 créditos**.

### Valor hora único
```
1 hora de cualquier oficio = 30 créditos
```
Simple e igualitario. Es el punto de partida del MVP.

### Escala por oficio (fase 2)
```
valor_hora(oficio) = H × factor(oficio)
```
Factores posibles: 0.8 (ayudante), 1.0 (oficio general), 1.3 (especializado), 1.5 (experto). Los factores se definen participativamente.

## 3. Conversión de productos

| Producto | Precio ARS | Créditos (U=100) |
|---|---|---|
| Docena de empanadas | 4.000 | 40 |
| Pan casero | 1.500 | 15 |
| Hora de jardinería | 3.000 | 30 |
| Hora de plomería | 5.000 | 50 |
| Blusa usada | 3.000 | 30 |
| Clase de guitarra | 4.000 | 40 |
| Corte de pelo | 4.500 | 45 |

> Los precios incluyen el valor del trabajo y los insumos. El sistema no distingue; el oferente declara el precio final.

## 4. Reglas de precio

1. **Ex ante**: el precio se publica antes del intercambio.
2. **No se negocia**: el comprador acepta o busca otra oferta.
3. **Público**: todos ven el mismo precio.
4. **Actualizable por ciclo**: el oferente puede cambiarlo al inicio de un ciclo, no durante.
5. **Rango**: el sistema puede rechazar precios fuera de un rango (ej. ±50% del promedio de la categoría).
6. **Justificación**: si el precio está fuera de rango, el oferente debe explicar por qué.

## 5. Actualización del valor de referencia

### Fuentes
- Relevamiento trimestral de precios locales.
- Índice de inflación oficial (INDEC).
- Encuesta a participantes.
- Precios de la feria o mercado local.

### Procedimiento
1. El comité recopila datos.
2. Propone un nuevo `H` y `U`.
3. La asamblea aprueba por mayoría simple.
4. Se aplica al inicio del ciclo siguiente.
5. Se comunica con 7 días de anticipación.

### Regla de estabilidad
- No se actualiza más de una vez por ciclo.
- El cambio no puede superar el 20% sin justificación.
- Los créditos ya emitidos mantienen su valor nominal; el ajuste afecta nuevas emisiones.

## 6. El problema del “bono blue”

La gente puede asignarle al crédito un valor distinto al oficial y negociar por fuera. Eso genera:
- Precios paralelos.
- Ventajas para quienes tienen más información.
- Riesgo regulatorio.

### Mitigaciones
- Precio fijo y público.
- Vencimiento corto.
- Educación: el crédito no es inversión.
- Detección de operaciones fuera de rango.
- Sanción por comercialización externa.

## 7. Ejemplo completo

| Paso | Acción | Créditos |
|---|---|---|
| 1 | Ana ofrece 10 h de jardinería a 30 créditos/h | Recibe 300 |
| 2 | Ana compra 4 docenas de empanadas a 40 | Paga 160; quedan 140 |
| 3 | Beto (empanadas) compra 2 blusas a 30 | Paga 60; quedan 80 |
| 4 | Carla (blusas) contrata 2 h de plomería a 50 | Paga 100; queda -20 → no puede |
| 5 | Carla ajusta: 1 h de plomería | Paga 50; quedan 30 |
| 6 | Diego (plomero) compra 1 h de jardinería a 30 | Paga 30; queda 0 |

## 8. Preguntas abiertas

- ¿El valor hora debe ser único o por oficio?
- ¿Cómo se manejan los insumos en los productos?
- ¿Qué pasa con los precios de productos importados?
- ¿Cómo se actualiza `H` sin generar inflación?
- ¿Se permite precio negociado en algún caso?
- ¿Cómo se trata el IVA y los impuestos?

## Enlaces

- [[03 - Direccion y Estrategia/Modelo - Circuito de creditos|Modelo — Circuito de créditos]]
- [[10 - Modelo Economico y Tokenomia/Modelo - Creditos de intercambio|Créditos de intercambio]]
- [[03 - Direccion y Estrategia/Decisiones/Decision - Precios ex ante y valor hora|Decisión — Precios ex ante]]
