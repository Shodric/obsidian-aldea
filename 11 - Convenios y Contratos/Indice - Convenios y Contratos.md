---
tipo: indice
area: legal
estado: activo
actualizado: 2026-11-20
---

# Índice — Convenios y Contratos

> [!info] Estado
> No hay convenios firmados. Esta carpeta registra los instrumentos en preparación y los vigentes.

## Registro

| Instrumento | Partes | Estado | Fecha | Vencimiento | Archivo |
|---|---|---|---|---|---|
| Contrato de membresía | Participante - Asociación | Borrador | — | — | Por confirmar |
| Términos de uso | Usuario - Plataforma | Borrador | — | — | Por confirmar |
| Política de privacidad | Usuario - Plataforma | Borrador | — | — | Por confirmar |
| Convenio municipal | Asociación - Municipio | A negociar | — | — | Por confirmar |
| Estatuto | Asociación | A redactar | — | — | Por confirmar |

## Convenios vigentes

```dataview
TABLE partes, estado, fecha, vencimiento
FROM "11 - Convenios y Contratos"
WHERE tipo = "convenio" OR tipo = "contrato"
SORT fecha DESC
```

## Cómo se registra

1. Crear una nota con el nombre del instrumento.
2. Completar partes, objeto, plazo y obligaciones.
3. Adjuntar el PDF en `16 - Archivo`.
4. Registrar fecha de firma y vencimiento.
5. Revisar 30 días antes del vencimiento.

## Enlaces

- [[13 - Legal y Cumplimiento/Contratos y DAO|Contratos y DAO]]
- [[13 - Legal y Cumplimiento/Marco regulatorio - Tokens y trueque en Argentina|Marco regulatorio]]
