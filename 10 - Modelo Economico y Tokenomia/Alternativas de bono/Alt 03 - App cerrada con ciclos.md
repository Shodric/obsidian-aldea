---
tipo: modelo
estado: propuesta
area: economia
alternativa: "03"
eje: soporte y emision
factibilidad: alta
actualizado: 2026-11-20
---

# Alternativa 03 — App cerrada con ciclos

> [!abstract] En una línea
> Un circuito que se abre, se inscribe, circula y cierra. Simple de construir y de auditar, pero el cierre genera el problema que Hernán identificó: cerca del vencimiento nadie quiere recibir bonos.

## 1. Qué se planteó en la llamada

> «En un principio lo empecé como una **app cerrada**: se arma un circuito, todos se juntan, se inscriben con lo que van a producir, reciben bonos a cambio y los disponen.»
> — Hernán, §3

> «Por eso está el tema de los **ciclos**. Esto tiene que cerrar y se tiene que volver a armar. Hay que estudiar los ciclos de cierre.»
> — Hernán, §10

## 2. Cómo funciona

1. **Apertura**: se anuncia el ciclo y se abre la inscripción.
2. **Alta**: cada participante declara qué ofrece y con qué valor.
3. **Emisión**: recibe créditos contra esa oferta, con un techo y un piso.
4. **Circulación**: compra y vende dentro del catálogo durante el ciclo.
5. **Cierre**: se auditan saldos y obligaciones; lo que no se usó se quema o se renueva.
6. **Reapertura**: hay que volver a inscribirse y ofertar.

## 3. Por qué se propuso

- **Control de la emisión**: el ciclo acota cuánto crédito existe.
- **Auditoría simple**: se cierra, se cuenta y se vuelve a abrir.
- **Modelo mental claro**: «el Mes», como en el circuito original.
- **Reinscripción obligatoria**: obliga a confirmar que la oferta sigue en pie.

## 4. Evaluación

| Dimensión | Valor | Fundamento |
|---|---|---|
| Técnica | Alta | App simple, base de datos, sin blockchain |
| Legal | Media-alta | Circuito cerrado, sin dinero; el riesgo aparece si se abre |
| Operativa | Media | Requiere coordinar apertura, cierre y reapertura |
| Dependencias | Baja | No necesita municipio ni permiso previo |
| Costo de prueba | Bajo-medio | Se puede pilotear con un grupo y una planilla |

**Factibilidad: Alta (4/5).** Es la alternativa más fácil de construir y de auditar. Su debilidad no es técnica, es económica.

## 5. El problema central

El cierre de ciclo produce un **acantilado**: en las últimas semanas, el que tiene créditos quiere gastarlos y el que tiene bienes no quiere recibirlos porque se vencen. Hernán lo dijo: «llega un momento en que la gente no quiere recibir bonos porque se van a vencer».

Ese acantilado se agrava con tres decisiones:

- Si el ciclo y el vencimiento coinciden, todo vence el mismo día.
- Si la reinscripción es obligatoria, el que no se inscribe pierde acceso y obligaciones a la vez.
- Si el cierre es administrativo, el que llegó tarde queda fuera.

## 6. Riesgos

| Riesgo | Señal | Mitigación |
|---|---|---|
| Acantilado de cierre | Caída de intercambios en la última semana | Vencimiento en posesión continuo, no global |
| Deserción en la reapertura | Menos inscriptos cada ciclo | Reinscripción simple, recordatorios, beneficio por continuidad |
| Captura del coordinador | Un grupo controla altas y precios | Reglas públicas, auditoría, gobernanza |
| Obligaciones huérfanas | El ciclo cierra con deudas | Registro de compromisos que sobrevive al cierre |

## 7. Rol en el MVP

**Sí, pero como período contable, no como única regla de caducidad.** La recomendación es:

- El **ciclo** (por ejemplo, 4 semanas) ordena la auditoría, la reinscripción y la comunicación.
- El **vencimiento en posesión** (Alternativa 04) corre por dentro, crédito por crédito.
- El cierre **no quema todo**: quema lo vencido y audita lo pendiente.

Así se conserva lo bueno del ciclo —control y simplicidad— sin su acantilado.

## 8. Preguntas específicas

1. ¿Se puede entrar a mitad de ciclo?
2. ¿Qué pasa con las obligaciones pendientes al cierre?
3. ¿Quién cierra y con qué criterio?
4. ¿El ciclo es fijo o se ajusta por demanda?
5. ¿La reapertura es automática o requiere una decisión de la asamblea?

## Enlaces

- [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Indice - Alternativas de bono|Índice — Alternativas de bono]]
- [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Alt 04 - UTXO con vencimiento en posesion|Alternativa 04 — Vencimiento en posesión]]
- [[03 - Direccion y Estrategia/Modelo - Circuito de creditos|Modelo — Circuito de créditos]]
