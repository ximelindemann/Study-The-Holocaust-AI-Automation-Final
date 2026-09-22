# Study the Holocaust — AI Automation

**Proyecto final de AI Automation · Coderhouse**  
**Alumna:** Ximena Basualdo · **Fecha:** septiembre de 2026

## Documento principal

[Leer el PDF de arquitectura y documentación (10 páginas)](documentacion/Entrega_Final_STH_Revision.pdf).

Versión de revisión del 21/09/2026. El PDF documenta arquitectura, estructuras de datos, costos, seguridad y evidencias iniciales. Debe actualizarse a versión final con las pruebas nuevas del 22/09/2026 antes de entregar.

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

- **Agente educativo:** recibe una consulta, usa la base de conocimiento del sitio y registra la interacción en `Consultas Agente`.
- **Indexación:** prepara contenido del sitio para su recuperación desde Supabase.
- **Gestión de errores:** registra fallos del agente en Airtable para revisión.
- **Revisión humana (HITL):** busca contenido en `Centro de Comando`, envía una solicitud por Gmail, espera aprobación o rechazo y actualiza Airtable.

La revisión humana registra una decisión. La publicación automática de contenido no se presenta como una funcionalidad validada.

## Estado contra rúbrica

| Criterio | Entregable | Estado actual |
|---|---|---|
| Arquitectura — 20% | PDF con triggers, decisiones, IA, APIs y destinos de datos | Cubierto en PDF de revisión; falta actualizar versión final con pruebas nuevas |
| Estructuras de datos — 20% | Tablas, relaciones y esquemas JSON de transferencia | Cubierto en [Manual de datos](documentacion/Manual_Datos.md) y PDF |
| Costos — 20% | Matriz comparativa y justificación de modelos por tarea | Cubierto con [TP6 corregido](documentacion/Costos_Eficiencia_TP6_Corregido.md); falta reflejar estado final en PDF |
| Seguridad y resiliencia — 20% | Minimización de datos, manejo de errores y HITL | HITL rechazo y aprobación probados; falta prueba documentada de error/seguridad del agente |
| Dashboard — 20% | Vista o dashboard con KPIs y tasa de errores | Pendiente de incorporar y verificar |

[Checklist viva de cierre](documentacion/Checklist_Entrega_Final.md): separa lo ya acreditado, lo pendiente y el orden recomendado para terminar.

## Evidencias de pruebas

| Prueba | Workflow | Ejecución | Resultado | Documento |
|---|---|---:|---|---|
| Agente responde pregunta educativa sobre Kristallnacht | `Holocaust Studies Chat Agent -FINAL` | `11597` | Success; respuesta generada, RAG consultado y registro en Airtable | [Prueba agente](documentacion/Prueba_Agente_Kristallnacht.md) |
| HITL rechazo | `STH HITL Approval - FINAL` | `11595` | Success; rama FALSE y registro `Rechazado` | [Prueba HITL rechazo](documentacion/Prueba_HITL_Rechazo.md) |
| HITL aprobación | `STH HITL Approval - FINAL` | `11600` | Success; rama TRUE, `Estado = Aprobado`, `Aprobado = true` | [Prueba HITL aprobación](documentacion/Prueba_HITL_Aprobacion.md) |

Durante la prueba de aprobación, una ejecución automática adicional (`11601`) se disparó mientras el workflow estuvo publicado; no actualizó datos porque `Search records` devolvió cero registros.

Los workflows fueron despublicados después de las pruebas para evitar consumo innecesario.

## Workflows incorporados

- [Agente: export anonimizado](workflows/Holocaust_Studies_Chat_Agent_Export_Anonimizado.json) · [Revisión](documentacion/Revision_Export_Agente.md).
- [HITL: export anonimizado](workflows/STH_HITL_Export_Anonimizado.json) · [Revisión](documentacion/Revision_Export_HITL.md).
- [Indexación: export anonimizado](workflows/Holocaust_Site_Index_Documents_Export_Anonimizado.json) · [Revisión](documentacion/Revision_Export_Indexacion.md).

Las correcciones aplicadas o preparadas están documentadas en [Correcciones pendientes de workflows](documentacion/Correcciones_Pendientes_Workflows.md), [Parches de revisión](documentacion/Parches_Workflows_Revision.diff) y [workflows_corregidos](workflows_corregidos/README.md).

## Evidencias visuales

- [Evidencias HITL](evidencias/hitl/): rechazo documentado con workflow y Airtable.
- Capturas nuevas del agente y de aprobación TRUE fueron generadas el 22/09/2026 y deben incorporarse a `evidencias/` antes de cerrar la entrega final.

## Pendientes antes de entregar

- [ ] Subir capturas nuevas del agente y HITL aprobación a `evidencias/`.
- [ ] Completar una prueba adicional de error o seguridad del agente.
- [ ] Incorporar vista/dashboard con KPIs: consultas procesadas, errores, tasa de error, aprobados, rechazados y en revisión.
- [ ] Actualizar el PDF de revisión a PDF final.
- [ ] Actualizar exports finales si se decide reemplazar los anonimizados de revisión.
- [ ] Agregar enlace del dashboard/base de lectura si corresponde.
- [ ] Incorporar enlace del video de demostración.
- [ ] Revisar capturas finales para excluir claves API, tokens o credenciales.

## Organización

- `documentacion/`: documentación técnica, checklist, pruebas, parches y PDF.
- `workflows/`: exportaciones JSON anonimizadas.
- `workflows_corregidos/`: notas sobre versiones corregidas de revisión.
- `evidencias/`: capturas y material de prueba.

## Referencia del proyecto

[Sitio Study the Holocaust](https://studytheholocaust.org/)

No se reutilizan enlaces ni archivos del proyecto anterior Nexo Digital.
