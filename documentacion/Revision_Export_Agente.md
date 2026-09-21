# Revisión del agente exportado

Fuente: `Holocaust Studies Chat Agent -FINAL.json`, descargado el 21 de septiembre de 2026. Inspección estática, sin ejecuciones ni publicación.

## Configuración comprobada

- Diez nodos: Chat, agente, modelo OpenAI, memoria, recuperación Supabase, embeddings, Wikipedia, registro normal en Airtable, Edit Fields y registro de errores.
- `active: false`: exportación inactiva.
- Modelo explícito: `gpt-5-nano`. Usar este dato como base para la matriz del agente, en lugar de asumir GPT-5.
- KB Embeddings no explicita un modelo en sus parámetros; verificar su valor en la interfaz antes de documentarlo como confirmado.
- Supabase recupera hasta cinco documentos de la tabla `documents`.
- Ruta normal: Chat → Agent → Create a record → Edit Fields.
- Segunda salida del agente conectada a Registrar Error en Airtable.

## Observaciones pendientes de corregir en la instancia

1. Varias expresiones de Airtable y Edit Fields comienzan por `=={{`. En la exportación n8n, un solo `=` marca la expresión; el segundo puede quedar como texto literal en el resultado. Revisar Id Consultas, Session ID, Pregunta, Respuesta, Error y output.
2. Ambos nodos Airtable tienen Fecha/Hora fija en `2026-09-18T00:00:00`. Para registrar cada evento debe usarse una fecha dinámica acorde al formato del campo.
3. Conversation Memory tiene `contextWindowLength: 0`; no presentar retención de turnos como capacidad comprobada.
4. La exportación no acredita por sí sola que las pruebas previas se ejecutaran con exactamente esta versión.

## Copia para repositorio

[JSON anonimizado](../workflows/Holocaust_Studies_Chat_Agent_Export_Anonimizado.json).

Se eliminaron referencias de credenciales, webhookId, datos fijados y metadatos de instancia. Se conservaron los parámetros funcionales, las conexiones y el estado inactivo para mantener fidelidad al archivo recibido. Los IDs de nodos se mantienen porque forman parte de la estructura del workflow.

La copia requiere reconectar las credenciales de OpenAI, Supabase y Airtable al importar. No se modificó la instancia de n8n ni el archivo original de Descargas. Esta copia es un export revisado, no una versión funcional corregida o validada por ejecución.
