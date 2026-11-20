---
tipo: politica
estado: borrador
area: gobernanza
actualizado: 2026-11-20
---

# Identidad y confianza

> [!warning] Documento en borrador
> El diseño de identidad debe validarse con legal y con pruebas de usabilidad. No se definió el proveedor ni el estándar.

## El problema

Aldea necesita **identidad** para sancionar y hacer cumplir los compromisos, pero el catálogo necesita **privacidad** para proteger a personas vulnerables. Si se pide DNI para todo, se excluye y se expone; si no se pide nada, no se puede sancionar.

## Principio: dos capas

| Capa | Qué contiene | Quién la ve | Para qué |
|---|---|---|---|
| **Pública** | Seudónimo, territorio, oferta, reputación | Todos | Catálogo e intercambio |
| **Privada** | Identidad verificada, contacto, documento | Comité/legal | Sanciones, contratos, disputas |

La capa pública nunca muestra el documento ni el domicilio exacto. La capa privada se cifra y se accede por roles.

## Verificación

### Nivel 0 — Registro básico
- Seudónimo y contacto (email o WhatsApp).
- Aceptación del reglamento.
- Suficiente para explorar el catálogo.

### Nivel 1 — Verificación para operar
- Documento o identidad digital.
- Teléfono verificado.
- Una cuenta por persona.
- Requerido para emitir créditos y comprar.

### Nivel 2 — Verificación para sanciones
- Identidad completa y domicilio.
- Solo se activa si hay una disputa o sanción.
- Acceso restringido al comité y legal.

## Prevención de sybil

- Un humano, una cuenta.
- Verificación de teléfono y documento.
- Detección de patrones: cuentas vinculadas, misma IP, mismos contactos.
- Revisión manual en casos dudosos.
- Límite de emisión por persona.

## Reputación

- **Contextual**: por categoría y por tipo de operación, no un puntaje único.
- **Pública**: cantidad de operaciones, cumplimiento, antigüedad.
- **Privada**: incidentes y sanciones, visibles solo para el comité.
- **Apelable**: el participante puede corregir errores.

## Confianza comunitaria

La identidad técnica no alcanza. La confianza se construye con:
- Presencia física y referentes barriales.
- Testimonios y casos reales.
- Transparencia en las reglas y las cuentas.
- Mediación justa y rápida.
- Reciprocidad: todos dan y reciben.

## Recuperación de cuenta

- Verificación por teléfono o email.
- Preguntas de seguridad.
- Apoyo presencial del comité.
- No se puede recuperar una cuenta sancionada sin cumplir el procedimiento.

## Datos que NO se piden

- Datos de salud.
- Orientación sexual.
- Religión.
- Ideología política.
- Datos biométricos (salvo que legal lo exija y haya consentimiento).

## Riesgos

- Exposición de datos por filtraciones.
- Suplantación de identidad.
- Discriminación por seudónimo o territorio.
- Exclusión de personas sin documento.
- Dependencia de un proveedor de identidad.

## Enlaces

- [[13 - Legal y Cumplimiento/Proteccion de datos y privacidad|Protección de datos]]
- [[07 - Tecnologia y Producto/Seguridad y privacidad|Seguridad y privacidad]]
- [[02 - Gobernanza y Comunidad/Reglas de membresia y sanciones|Reglas de membresía]]
