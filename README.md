# Study the Holocaust - AI Automation Final

Proyecto final de AI Automation para Coderhouse.

## Resumen

Ecosistema de automatización con IA para Study the Holocaust. El sistema combina n8n, Airtable, OpenAI, Supabase RAG y revisión humana por Gmail para responder consultas educativas, registrar interacciones y controlar decisiones editoriales antes de cualquier acción crítica.

## Componentes

- `Holocaust Studies Chat Agent -FINAL`: agente educativo con GPT-5 nano, recuperación RAG y registro en Airtable.
- `STH HITL Approval - FINAL`: flujo de revisión humana por Gmail con ramas de aprobación y rechazo.
- `Holocaust Site - Index Documents`: indexación controlada del sitio hacia Supabase/documents.
- `STH Content Pipeline`: base de Airtable con Centro de Comando, Consultas Agente y Dashboard Público STH.

## Evidencia validada

- HITL rechazo: ejecución n8n `11595`, estado final `Rechazado`.
- Agente educativo: ejecución n8n `11597`, consulta sobre Kristallnacht y registro `Procesado`.
- HITL aprobación: ejecución n8n `11600`, estado final `Aprobado` y checkbox activado.
- Dashboard ejecutivo: 14 consultas totales, 9 procesadas, 2 errores, tasa de error 14,29 %, 1 contenido aprobado y 2 rechazados.

## Enlaces

- Sitio educativo: https://studytheholocaust.org/
- Dashboard público Airtable: https://airtable.com/appnkoN6JcAcSAVDg/shrYxSBg2VbQ6KLvz
- PDF final: [documentacion/Entrega_Final_STH_Final.pdf](documentacion/Entrega_Final_STH_Final.pdf)

## Workflows finales

Los exports finales están en `workflows_corregidos/` y se mantienen con `active=false` para evitar consumo de cuota o ejecuciones accidentales.

- [Agente educativo final](workflows_corregidos/Holocaust_Studies_Chat_Agent_Export_FINAL.json): incluye `maxTokens = 600`, RAG, registro exitoso y ruta local de error.
- [HITL final](workflows_corregidos/STH_HITL_Export_FINAL.json): incluye Schedule explícito cada 30 minutos, reserva previa `Esperando Aprobacion`, ramas TRUE/FALSE y actualización final de Airtable.
- [Indexación final](workflows_corregidos/Holocaust_Site_Index_Documents_Export_FINAL.json): indexación controlada del sitio hacia Supabase.

También se conservan los exports anonimizados originales en `workflows/` como respaldo histórico.

## Documentación

- [PDF final de entrega](documentacion/Entrega_Final_STH_Final.pdf)
- [Prueba agente Kristallnacht](documentacion/Prueba_Agente_Kristallnacht.md)
- [Prueba HITL aprobación](documentacion/Prueba_HITL_Aprobacion.md)
- [Prueba HITL rechazo](documentacion/Prueba_HITL_Rechazo.md)
