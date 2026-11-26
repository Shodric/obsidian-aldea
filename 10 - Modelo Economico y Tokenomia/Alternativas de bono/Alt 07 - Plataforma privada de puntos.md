---
tipo: modelo
estado: propuesta
area: economia
alternativa: "07"
eje: gobernanza
factibilidad: alta
actualizado: 2026-11-20
---

# Alternativa 07 — Plataforma privada de puntos

> [!abstract] En una línea
> Cualquiera descarga la app, se registra, oferta y recibe puntos. No necesita municipio ni permiso previo: es el vehículo de menor fricción para el MVP.

## 1. Qué se planteó en la llamada

> «Después lo pensé en un sentido privado: simplemente se ofrece una **plataforma que todo el mundo se descarga en su app**. Vos descargás, das tu dato para que te localicen, ofertás lo que vas a ofertar y ya recibís unos puntos de intercambio. Entonces accedés al catálogo de todos los que están en la zona cercana, ves qué podés adquirir con tus puntos y empieza el intercambio.»
> — Hernán, §7

## 2. Cómo funciona

1. **Descarga y alta**: alias, contacto y zona. Sin DNI en el MVP.
2. **Oferta**: publica qué ofrece, con precio en créditos puesto de antemano.
3. **Emisión**: recibe créditos contra esa oferta, con piso y techo.
4. **Catálogo**: ve las ofertas de la zona y compra.
5. **Intercambio**: los créditos pasan al vendedor; el comprador asume una obligación.
6. **Cumplimiento**: confirma la entrega con un código; la obligación queda registrada.
7. **Vencimiento**: el crédito que no circula se quema; la obligación sigue.

## 3. Por qué se propuso

- **Sin dependencias políticas**: no hace falta ordenanza ni municipio.
- **Bajo costo de arranque**: una app y un grupo de 200–300 personas.
- **Autoalta**: el usuario entra cuando quiere.
- **Probable rápido**: se puede testear en el conurbano sin infraestructura pública.

## 4. Evaluación

| Dimensión | Valor | Fundamento |
|---|---|---|
| Técnica | **Alta** | App web/móvil y base de datos; sin blockchain en la v1 |
| Legal | Media-alta | Marketplace con puntos; el riesgo aparece si se convierte en moneda |
| Operativa | **Alta** | Autoservicio, sin coordinador por ciclo |
| Dependencias | **Baja** | Ninguna institución tiene que aprobar |
| Costo de prueba | Bajo-medio | Hosting, desarrollo y onboarding territorial |

**Factibilidad: Alta (4.5/5).** Es el vehículo más rápido y barato para probar el modelo.

## 5. El problema central

La plataforma privada resuelve el «quién nos deja», pero no resuelve el **arranque en frío**:

- Sin oferta suficiente, el usuario entra, mira y se va.
- Sin un ancla territorial (una feria, una cooperativa, un grupo de vecinos), el catálogo queda vacío.
- Sin confianza previa, nadie ofrece primero.

La app no crea comunidad: la comunidad usa la app. Esa es la diferencia entre un producto y un mercado.

## 6. Riesgos

| Riesgo | Señal | Mitigación |
|---|---|---|
| Mercado vacío | Pocas ofertas, pocas compras | Ancla territorial y onboarding curado |
| Desintermediación | La gente intercambia por WhatsApp | Precio fijo, reputación, garantía |
| Free riders | Compran y no entregan | Identidad, techo, sanción |
| Fatiga de apps | Baja retención | Notificaciones útiles, no spam |
| Deriva a moneda | Se usa para pagar fuera del circuito | Sin conversión, sin mercado secundario |

## 7. Rol en el MVP

**Es el vehículo.** Se combina con la Alternativa 04 como regla económica y con la 09 en versión liviana como contrato.

El primer despliegue no necesita blockchain ni token: alcanza con una base de datos, un catálogo y un registro de obligaciones. La cadena se evalúa después, solo si resuelve un problema real de confianza entre organizaciones.

## 8. Preguntas específicas

1. ¿Quién cura el catálogo y con qué criterio?
2. ¿Cómo se llega a la masa crítica inicial?
3. ¿Cuál es el ancla: feria, cooperativa, barrio, parroquia, club?
4. ¿Qué pasa si dos personas intercambian fuera de la app?
5. ¿La plataforma cobra comisión? (Propuesta: 0% en el MVP.)

## Enlaces

- [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Indice - Alternativas de bono|Índice — Alternativas de bono]]
- [[10 - Modelo Economico y Tokenomia/Alternativas de bono/Alt 04 - UTXO con vencimiento en posesion|Alternativa 04 — Vencimiento en posesión]]
- [[08 - Proyectos/Activos/Proyecto - MVP de trueque|Proyecto — MVP de trueque]]
