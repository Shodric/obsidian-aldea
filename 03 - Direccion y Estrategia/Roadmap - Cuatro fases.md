---
tipo: roadmap
estado: activo
area: direccion
fecha: 2026-11
actualizado: 2026-11-20
---

# Roadmap — Cuatro fases

> [!summary] Lógica del roadmap
> Primero se prueba el modelo, después se construye. La tecnología es la última capa, no la primera. Cada fase tiene un **criterio de salida** claro: si no se cumple, no se avanza.

## Vista general

| Fase | Nombre | Duración estimada | Costo estimado | Criterio de salida |
|---|---|---|---|---|
| **0** | Simulación y validación | 4–6 semanas | USD 10–30 + tiempo | El modelo no se bloquea en escenarios adversos |
| **1** | Diseño legal y territorial | 6–8 semanas | Por confirmar | Vehículo, contratos, territorio y aliados definidos |
| **2** | MVP y piloto | 8–12 semanas | Por confirmar | 100–300 usuarios y intercambios repetidos |
| **3** | Evaluación y réplica | 8–12 semanas | Por confirmar | Informe de evaluación y decisión sobre escalar |

> Las duraciones y costos son **órdenes de magnitud**, no compromisos. Se ajustan al equipo y al financiamiento.

---

## Fase 0 — Simulación y validación

**Objetivo**: probar el modelo económico y de comportamiento antes de escribir código de producción.

### Entregables
- [ ] Documento ejecutivo v1.0.
- [ ] Modelo del circuito con parámetros y casos borde.
- [ ] Simulación agéntica v1 (10 agentes, 4 perfiles).
- [ ] Informe de simulación: dónde se bloquea, cuántos intercambios, qué atajos aparecen.
- [ ] Dictamen legal preliminar sobre el crédito de intercambio.
- [ ] Mapa de oferta y demanda del territorio candidato.
- [ ] Presupuesto de Fase 1.

### Actividades
1. Procesar los archivos de Hernán (modelo original, pitches, simulador JSX).
2. Diseñar los perfiles de agente y las métricas.
3. Correr la simulación con modelos gratuitos o de bajo costo.
4. Analizar resultados y ajustar parámetros.
5. Entrevistar a 10–15 personas del territorio.
6. Consultar a la abogada y al municipio.

### Criterio de salida
- La simulación muestra un circuito viable con al menos 40% de agentes activos.
- Los mecanismos de vencimiento y sanción no colapsan el sistema.
- Hay un territorio candidato y contactos dispuestos a participar.
- El encuadre legal es favorable o, al menos, no bloqueante.

### Riesgos de la fase
- Que la simulación sea demasiado abstracta y no represente el comportamiento real.
- Que el costo de las llamadas a modelos supere el presupuesto.
- Que la abogada no tenga disponibilidad.

---

## Fase 1 — Diseño legal y territorial

**Objetivo**: convertir el modelo en una estructura jurídica y territorial operable.

### Entregables
- [ ] Vehículo legal elegido y constituido (asociación civil, cooperativa, fundación o SAS).
- [ ] Estatuto y reglamento interno.
- [ ] Contrato de membresía y términos de uso.
- [ ] Política de privacidad y tratamiento de datos.
- [ ] Convenio con el municipio o aliado territorial.
- [ ] Mapa de aliados y pipeline de contactos.
- [ ] Plan de comunicación y materiales.
- [ ] Diseño del piloto: territorio, tamaño, duración, métricas.

### Actividades
1. Reunión con abogada: encuadre del crédito, contratos, datos.
2. Reunión con municipio: rol, mediación, espacio, beneficios.
3. Relevamiento de oferta y demanda en el territorio.
4. Definición de la gobernanza: quién decide qué.
5. Diseño de la identidad visual y el relato.
6. Armado del presupuesto detallado.

### Criterio de salida
- El vehículo legal existe o está en trámite.
- Hay un convenio o carta de intención con el territorio.
- El piloto tiene territorio, tamaño, duración y métricas.
- El presupuesto está financiado o hay un plan de financiamiento.

### Riesgos de la fase
- Que el municipio quiera capturar el proyecto.
- Que el marco legal sea más complejo de lo previsto.
- Que el territorio no tenga densidad suficiente.

---

## Fase 2 — MVP y piloto

**Objetivo**: operar un circuito real con 100–300 usuarios durante 4–8 semanas.

### Entregables
- [ ] App MVP: registro, oferta, catálogo, billetera, transferencia, confirmación, vencimiento.
- [ ] Panel de administración: usuarios, ofertas, obligaciones, disputas.
- [ ] Piloto operado con soporte presencial.
- [ ] Reporte de piloto: intercambios, usuarios activos, tiempo de circulación, incumplimientos.
- [ ] Manual de operación y SOPs.

### Alcance del MVP
**Incluye**:
- Registro con seudónimo y contacto.
- Oferta con precio en créditos.
- Emisión contra oferta.
- Catálogo geolocalizado.
- Transferencia de créditos.
- Vencimiento y renovación.
- Confirmación de entrega con código.
- Panel de administración básico.

**No incluye**:
- Token de recompensa.
- Integración con bancos o billeteras fiduciarias.
- Gobernanza on-chain completa.
- Reputación compleja.
- Aplicaciones nativas iOS/Android (empezar web).

### Criterio de salida
- Al menos 100 usuarios registrados y 40 activos semanales.
- Al menos 200 intercambios completados.
- Tasa de incumplimiento menor al 10%.
- Usuarios que repiten: al menos 30%.
- El circuito se sostiene sin intervención constante del equipo.

### Riesgos de la fase
- Baja adopción.
- Oferta homogénea.
- Problemas técnicos de usabilidad.
- Conflictos no resueltos.

---

## Fase 3 — Evaluación y réplica

**Objetivo**: medir resultados, ajustar el modelo y decidir si se escala o se replica.

### Entregables
- [ ] Informe de evaluación con datos cuantitativos y cualitativos.
- [ ] Análisis de costo por usuario y por intercambio.
- [ ] Recomendaciones de ajuste.
- [ ] Manual de réplica para nuevos territorios.
- [ ] Evaluación del token de recompensa (viabilidad legal y económica).
- [ ] Plan de financiamiento para la siguiente etapa.

### Actividades
1. Analizar datos del piloto.
2. Entrevistar a participantes, aliados y municipio.
3. Comparar con la simulación.
4. Decidir: escalar, ajustar o cerrar.
5. Diseñar la siguiente versión del protocolo.

### Criterio de salida
- Hay una decisión fundada sobre escalar, replicar o cerrar.
- El modelo tiene evidencia de impacto.
- Existe un plan para la siguiente etapa.

---

## Dependencias entre fases

```
Fase 0 ──→ Fase 1 ──→ Fase 2 ──→ Fase 3
   │           │           │
   └─ legal ───┘           │
   └─ territorio ──────────┘
   └─ simulación ──────────┘ (alimenta el diseño del MVP)
```

## Hitos críticos

| Hito | Fase | Fecha objetivo | Estado |
|---|---|---|---|
| Documento ejecutivo v0.1 | 0 | 2026-11-27 | En curso |
| Archivos de Hernán recibidos | 0 | Por confirmar | Pendiente |
| Simulación v1 | 0 | Por confirmar | Pendiente |
| Dictamen legal preliminar | 1 | Por confirmar | Pendiente |
| Territorio definido | 1 | Por confirmar | Pendiente |
| MVP funcionando | 2 | Por confirmar | Pendiente |
| Piloto lanzado | 2 | Por confirmar | Pendiente |
| Informe de evaluación | 3 | Por confirmar | Pendiente |

## Enlaces

- [[03 - Direccion y Estrategia/2026-11 - Documento Ejecutivo Aldea|Documento Ejecutivo]]
- [[03 - Direccion y Estrategia/Modelo - Circuito de creditos|Modelo — Circuito de créditos]]
- [[08 - Proyectos/Indice - Proyectos|Proyectos]]
- [[00 - Centro de Mando/Aldea - Centro de Mando|Centro de Mando]]
