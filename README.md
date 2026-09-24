# Study the Holocaust - AI Automation Final

Proyecto final de AI Automation para Coderhouse.

## Resumen

Ecosistema de automatización con IA para Study the Holocaust. El sistema combina n8n, Airtable, OpenAI, Supabase RAG y revisión humana por Gmail para responder consultas educativas, registrar interacciones y controlar decisiones editoriales antes de cualquier acción crítica.

## Componentes

- `Holocaust Studies Chat Agent`: agente educativo con recuperación RAG, procesamiento con OpenAI y registro en Airtable.
- `STH HITL Approval`: flujo de validación humana por Gmail con ramas de aprobación y rechazo.
- `Holocaust Site - Index Documents`: indexación controlada del sitio hacia Supabase.
- `STH Content Pipeline`: base de Airtable con registro operativo y dashboard ejecutivo.

## Evidencia validada

- Agente educativo: ejecución n8n `11597`, consulta sobre Kristallnacht y registro `Procesado`.
- HITL aprobación: ejecución n8n `11600`, estado final `Aprobado` y checkbox activado.
- HITL rechazo: ejecución n8n `11595`, estado final `Rechazado`.
- Dashboard ejecutivo: 14 consultas totales, 9 procesadas, 2 errores, tasa de error 14,29 %, 1 contenido aprobado y 2 rechazados.

## Enlaces de entrega

- Sitio educativo: https://studytheholocaust.org/
- Dashboard público Airtable: https://airtable.com/appnkoN6JcAcSAVDg/shrYxSBg2VbQ6KLvz
- PDF final: [documentacion/Entrega_Final_STH_Final.pdf](documentacion/Entrega_Final_STH_Final.pdf)
- Video demo: https://drive.google.com/file/d/15m4qi5_nIlbBOGR7EOyzhYhp2hMRgSnk/view?usp=sharing

## Exports técnicos

Los exports de n8n están incluidos como respaldo técnico de la entrega.

- [Agente educativo](workflows/Holocaust_Studies_Chat_Agent_Export_Anonimizado.json): agente con RAG, OpenAI y registro en Airtable.
- [Validación humana HITL](workflows/STH_HITL_Export_Anonimizado.json): flujo de aprobación/rechazo con Gmail y Airtable.
- [Indexación del sitio](workflows/Holocaust_Site_Index_Documents_Export_Anonimizado.json): flujo de carga de contenido hacia Supabase.

## Documentación

- [PDF final de entrega](documentacion/Entrega_Final_STH_Final.pdf)
- [Evidencia agente educativo](documentacion/Evidencia_Agente_Educativo.md)
- [Evidencia HITL aprobación](documentacion/Evidencia_HITL_Aprobacion.md)
- [Evidencia HITL rechazo](documentacion/Evidencia_HITL_Rechazo.md)
