---
tipo: documento
estado: borrador
area: finanzas
proyecto: "[[Proyecto - Simulacion agentica]]"
actualizado: 2026-11-20
---

# Recursos y presupuesto — Simulación agéntica

> [!info] Principio
> La primera versión no necesita dinero. El modo deterministico y los modelos gratuitos alcanzan para validar el arnés. El presupuesto se libera solo cuando el diseño está cerrado y hay una pregunta que justifica el gasto.

## 1. Recursos humanos

| Rol | Quién | Dedicación estimada | Responsabilidad |
|---|---|---|---|
| Dirección | Rodrigo | 30–40% durante la ejecución | Alcance, diseño, construcción y análisis |
| Dominio | Hernán | 2–4 horas por etapa | Reglas del circuito, supuestos y validación |
| Análisis externo | Por definir | 4–8 horas | Lectura crítica de resultados |
| Revisión legal | Por definir | Solo si se usan datos reales | Privacidad y términos |

## 2. Herramientas

| Herramienta | Uso | Costo |
|---|---|---|
| Python 3.11+ | Simulador | Gratis |
| Git | Versionado | Gratis |
| SQLite | Persistencia | Gratis |
| pandas + matplotlib | Análisis y gráficos | Gratis |
| Jupyter o scripts | Exploración | Gratis |
| Editor de código | Desarrollo | Gratis |
| API de LLM | Agentes con lenguaje | Variable |
| Almacenamiento | Datos y resultados | Gratis o bajo costo |

## 3. Modelos de lenguaje

| Opción | Ventaja | Límite | Costo | Uso recomendado |
|---|---|---|---|---|
| Modo mock | Sin costo, reproducible | No hay lenguaje emergente | USD 0 | Pruebas y línea base |
| Modelos gratuitos | Sin costo | Límite de llamadas y calidad variable | USD 0 | Primera exploración |
| DeepSeek | Buen costo/calidad | Requiere cuenta y verificación | Bajo | Corrida principal |
| Modelos premium | Mejor razonamiento | Costo alto | Alto | Casos puntuales |

> [!warning] Precios
> Los precios de los modelos cambian. Verificar tarifas, límites y condiciones al momento de contratar. No usar créditos compartidos ni cuentas personales para datos sensibles.

## 4. Fórmula de costo

```text
costo_corrida =
  llamadas
  × (tokens_entrada / 1.000.000 × precio_entrada_por_millon
     + tokens_salida / 1.000.000 × precio_salida_por_millon)
```

**Ejemplo ilustrativo, no cotización:**

- 30 agentes × 28 días = 840 llamadas.
- 3.000 tokens de entrada y 400 de salida por llamada.
- Precio bajo de referencia: USD 0,14 por millón de entrada y USD 0,28 por millón de salida.
- Costo estimado: menos de USD 1 por corrida, sin contar reintentos ni resúmenes.

Con prompts más largos, memoria y reintentos, el costo puede multiplicarse. Por eso el límite duro es obligatorio.

## 5. Escenarios de presupuesto

| Escenario | Qué incluye | Rango | Cuándo |
|---|---|---|---|
| A — Mock | Solo modo deterministico, sin API | USD 0 | Validar el arnés y las métricas |
| B — Gratuito | Mock + modelos gratuitos | USD 0–10 | Primera exploración con lenguaje |
| C — Recomendado | Mock + DeepSeek o similar | USD 10–30 | Corrida principal E1-E8 |
| D — Extendido | Modelos premium y más repeticiones | USD 30–100 | Solo si C deja preguntas abiertas |

**Recomendación:** empezar por A, pasar a B y liberar C solo con el diseño cerrado. D no se justifica en la primera etapa.

## 6. Estimación de esfuerzo

| Fase | Esfuerzo | Costo de tiempo |
|---|---|---|
| Preparación | 0,5–1 día | Rodrigo |
| Diseño | 1–2 días | Rodrigo + Hernán |
| Construcción | 3–5 días | Rodrigo |
| Prueba | 1–2 días | Rodrigo |
| Corrida | 1–3 días | Rodrigo |
| Análisis | 2–3 días | Rodrigo |

**Total preliminar:** 8–16 días de trabajo efectivo. No incluye espera de insumos ni revisión externa.

## 7. Insumos que deben estar disponibles

- [ ] Simulador JSX de Hernán.
- [ ] Modelo original de moneda social 2016–2024.
- [ ] Los dos pitches de Aldea.
- [ ] Parámetros del circuito: vencimiento, techos, precios y sanciones.
- [ ] Definición de perfiles y porcentajes.
- [ ] Presupuesto máximo aprobado.
- [ ] Cuenta y API key del proveedor elegido.
- [ ] Carpeta o repositorio para datos crudos.

## 8. Compras y trámites

1. Elegir proveedor de modelo.
2. Crear cuenta con correo del proyecto, no personal.
3. Configurar límite de gasto y alertas.
4. Generar API key y guardarla en `.env`, fuera del repositorio.
5. Verificar términos de uso y política de datos.
6. Probar una llamada mínima.
7. Registrar costo y fecha de la prueba.

## 9. Riesgos de recursos

| Riesgo | Impacto | Mitigación |
|---|---|---|
| Falta de tiempo de Rodrigo | Retraso | Ejecutar por bloques de 2–3 días |
| Hernán no envía los archivos | Diseño incompleto | Avanzar con supuestos propios y validar después |
| Costo mayor al previsto | Corrida incompleta | Límite duro y modo mock |
| Modelo gratuito con límites | Corrida cortada | Cachear y reducir agentes |
| Pérdida de datos | Resultados irrecuperables | Git + copia de datos crudos |
| Cambio de precios | Presupuesto desactualizado | Reestimar antes de cada corrida |

## 10. Decisión de avance

No se ejecuta la corrida paga hasta que:

- [ ] El diseño experimental esté cerrado.
- [ ] El arnés pase las pruebas.
- [ ] El costo estimado esté dentro del presupuesto.
- [ ] Exista una pregunta concreta que la corrida responda.
- [ ] Los datos crudos tengan un lugar seguro.

## Enlaces

- [[Proyecto - Simulacion agentica|Proyecto — Simulación agéntica]]
- [[01 - Plan de ejecucion|Plan de ejecución]]
- [[02 - Requisitos|Requisitos]]
- [[04 - Arquitectura tecnica|Arquitectura técnica]]
- [[05 - Prompts y perfiles|Prompts y perfiles]]
- [[05 - Finanzas y Tesoreria/Presupuesto - Fase 0 y 1|Presupuesto — Fase 0 y 1]]
