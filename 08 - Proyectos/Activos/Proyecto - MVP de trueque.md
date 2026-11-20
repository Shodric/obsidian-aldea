---
tipo: proyecto
estado: pendiente
fase: 2
area: proyectos
responsable: Rodrigo
inicio: por confirmar
fecha_objetivo: por confirmar
presupuesto_estimado: por confirmar
actualizado: 2026-11-20
---

# Proyecto — MVP de trueque

## Objetivo
Construir la primera versión funcional de Aldea: registro, oferta, catálogo, billetera con créditos que vencen, transferencia, confirmación de entrega y panel de administración. Debe ser simple, usable en un celular de gama baja y con la blockchain invisible para el usuario.

## Alcance
- Registro con seudónimo y contacto.
- Perfil con identidad verificada en una capa separada.
- Oferta con precio en créditos y categoría.
- Emisión contra oferta, con piso y techo.
- Catálogo geolocalizado con búsqueda y filtros.
- Billetera con saldo y tiempo restante por crédito.
- Transferencia de créditos con partición y renovación.
- Confirmación de entrega con código.
- Panel de administración: usuarios, ofertas, obligaciones, disputas.
- Notificaciones básicas (email o WhatsApp).

## Fuera de alcance
- Token de recompensa.
- Integración con bancos o billeteras fiduciarias.
- Gobernanza on-chain completa.
- Reputación compleja o scoring avanzado.
- Apps nativas iOS/Android (empezar web).
- Múltiples territorios.
- Facturación o integración fiscal.

## Actividades
1. Definir historias de usuario y flujos.
2. Diseñar la experiencia de registro y primera oferta.
3. Diseñar el modelo de datos y la lógica de vencimiento.
4. Elegir stack: base de datos vs. blockchain.
5. Construir el backend y la billetera.
6. Construir el frontend mobile-first.
7. Construir el panel de administración.
8. Probar con usuarios reales.
9. Iterar y preparar el piloto.

## Hitos

| Hito | Fecha objetivo | Estado |
|---|---|---|
| Alcance funcional cerrado | Por confirmar | Pendiente |
| Prototipo navegable | Por confirmar | Pendiente |
| Backend y billetera | Por confirmar | Pendiente |
| Frontend mobile-first | Por confirmar | Pendiente |
| Panel de administración | Por confirmar | Pendiente |
| Prueba con 10 usuarios | Por confirmar | Pendiente |
| MVP listo para piloto | Por confirmar | Pendiente |

## Tareas
- [ ] Escribir las historias de usuario.
- [ ] Diseñar el flujo de alta y oferta.
- [ ] Definir el modelo de datos.
- [ ] Decidir arquitectura (base de datos vs. blockchain).
- [ ] Implementar emisión y vencimiento.
- [ ] Implementar transferencia y partición.
- [ ] Implementar confirmación con código.
- [ ] Implementar panel de administración.
- [ ] Probar usabilidad con personas mayores o con poca alfabetización digital.
- [ ] Documentar la arquitectura y el despliegue.

## Dependencias
- Modelo del circuito aprobado.
- Dictamen legal preliminar.
- Definición de parámetros (vencimiento, precios, límites).
- Territorio y usuarios para probar.

## Riesgos
- Sobreingeniería y retraso.
- Mala usabilidad.
- Complejidad de la billetera.
- Costos de infraestructura.
- Cambios de reglas que obliguen a rehacer.

## Criterio de éxito
- Un usuario puede registrarse y publicar una oferta en menos de 5 minutos.
- Un intercambio completo se puede hacer sin ayuda.
- El vencimiento y la renovación funcionan correctamente.
- El panel permite resolver una disputa.
- La app funciona en un celular de gama baja con conexión lenta.

## Enlaces
- [[07 - Tecnologia y Producto/Producto - App MVP|Producto — App MVP]]
- [[07 - Tecnologia y Producto/Arquitectura - Creditos con vencimiento|Arquitectura]]
- [[07 - Tecnologia y Producto/Stack y decisiones tecnicas|Stack y decisiones técnicas]]
- [[12 - Procesos y SOPs/Indice - Procesos y SOPs|SOPs]]
