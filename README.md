# Study the Holocaust — AI Automation

**Proyecto final de AI Automation · Coderhouse**  
**Alumna:** Ximena Basualdo · **Fecha:** septiembre de 2026

## Objetivo

Asistente educativo de Study the Holocaust que combina generación de respuestas con recuperación de información (RAG), registro de consultas y revisión humana por correo. El ecosistema utiliza n8n, OpenAI, Supabase, Airtable y Gmail.

## Componentes

| Componente | Función |
|---|---|
| n8n | Orquestación de los workflows |
| OpenAI | Generación de respuestas y embeddings |
| Supabase | Almacenamiento y consulta de la base de conocimiento vectorial |
| Airtable — STH Content Pipeline | Registro de consultas y seguimiento de estados |
| Gmail | Solicitud de revisión y espera de una decisión humana |

## Flujos del proyecto

- **Agente educativo:** recibe una consulta, utiliza las herramientas de conocimiento y registra la interacción en `Consultas Agente`.
- **Indexación:** prepara contenido del sitio para su recuperación desde Supabase.
- **Gestión de errores:** registra fallos del agente en Airtable.
- **Revisión humana (HITL):** busca contenido en `Centro de Comando`, envía una solicitud por Gmail, espera la respuesta y deriva a aprobación o rechazo.

La revisión humana registra una decisión. La publicación automática de contenido no se presenta como una funcionalidad validada.

## Entregables y estado de preparación

Este repositorio está en preparación. Los estados siguientes distinguen lo construido de los archivos que todavía deben incorporarse.

| Criterio | Entregable | Estado en este repositorio |
|---|---|---|
| Arquitectura — 20% | PDF con triggers, decisiones, IA, APIs y destinos de datos | Pendiente de incorporar |
| Estructuras de datos — 20% | Tablas, relaciones y esquemas JSON de transferencia | [Manual de datos disponible](documentacion/Manual_Datos.md); integración al PDF pendiente |
| Costos — 20% | Matriz comparativa y justificación de modelos por tarea | Pendiente de incorporar |
| Seguridad y resiliencia — 20% | Minimización de datos, manejo de errores y HITL | Nota de prueba HITL disponible; documento completo pendiente |
| Dashboard — 20% | Enlace de lectura con KPIs y tasa de errores | Pendiente de incorporar y verificar |

## Evidencias de pruebas

La rama de rechazo del workflow `STH HITL Approval - FINAL` tiene una ejecución exitosa: **#11595, 21 de septiembre de 2026**, con recorrido por `FALSE → Update record1`.

Las dos capturas están disponibles en [evidencias/hitl](evidencias/hitl/): recorrido de rechazo en verde y estado final en Airtable.

[Consultar la documentación de la prueba de rechazo](documentacion/Prueba_HITL_Rechazo.md).

La evidencia de aprobación (TRUE) sigue pendiente de verificación. Las pruebas del agente y su ruta de error, realizadas durante el desarrollo, deben incorporarse con sus evidencias. No se considera completo el conjunto de cinco pruebas hasta inventariarlas.

## Pendientes de entrega

- [ ] Incorporar el PDF de arquitectura y la documentación de datos, costos y seguridad.
- [ ] Exportar y revisar los JSON actuales del agente, indexación y HITL.
- [x] Subir y revisar las dos capturas del rechazo HITL.
- [ ] Incorporar evidencia verificable de aprobación TRUE.
- [ ] Inventariar al menos cinco pruebas, incluido un camino de error.
- [ ] Incorporar y comprobar los enlaces de lectura de Airtable y del dashboard.
- [ ] Incorporar el enlace del video de demostración.
- [ ] Revisar archivos y capturas para excluir claves API, tokens y credenciales.

## Organización prevista

- `documentacion/`: documentación técnica y PDF de entrega.
- `workflows/`: exportaciones JSON revisadas.
- `evidencias/`: capturas y registro de pruebas.

## Referencia del proyecto

[Sitio Study the Holocaust](https://studytheholocaust.org/)

Los enlaces de la base de datos, dashboard y video se agregarán cuando estén verificados. No se reutilizan los enlaces del proyecto anterior Nexo Digital.
