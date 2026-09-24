# Workflows finales exportados

Esta carpeta contiene los exports finales de n8n usados como respaldo técnico de la entrega.

## Archivos

- `Holocaust_Studies_Chat_Agent_Export_FINAL.json`: agente educativo con RAG, OpenAI, registro en Airtable y ruta de error.
- `STH_HITL_Export_FINAL.json`: flujo Human-in-the-loop con revisión por Gmail, aprobación/rechazo y actualización en Airtable.
- `Holocaust_Site_Index_Documents_Export_FINAL.json`: flujo de indexación controlada del sitio hacia Supabase.

## Estado

Los workflows se entregan exportados con `active=false` para evitar ejecuciones accidentales y preservar cuota. Las pruebas principales del agente y del HITL están documentadas en la carpeta `documentacion/`.
