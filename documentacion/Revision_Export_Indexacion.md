# Revisión del workflow de indexación

Fuente: Holocaust Site — Index Documents.json, descargado el 21 de septiembre de 2026. Inspección estática; no se ejecutó ni se modificó el workflow en n8n.

## Recorrido comprobado

Disparador manual → descarga de https://studytheholocaust.org/ → extracción del body sin script, style, nav, header ni footer → limpieza de texto → almacenamiento en Supabase, tabla documents.

El almacenamiento recibe documentos de Load Page Content, fragmentados mediante Split Into Chunks, y vectores del nodo OpenAI Embeddings. Los documentos agregan source=https://studytheholocaust.org/ como metadato. El solapamiento explícito es de 150 caracteres; el tamaño de fragmento no aparece explícito en la exportación.

## Alcance

El archivo descarga una única URL. No contiene un recorrido de todos los enlaces del sitio, por lo que no acredita la indexación completa de todos los módulos o artículos. La tabla documents es la misma que consulta el agente; la coincidencia de proyecto Supabase debe verificarse al reconectar credenciales.

## Pendientes antes de ejecutar

- OpenAI Embeddings referencia en el original la credencial n8n free OpenAI API credits. Confirmar y seleccionar una credencial propia disponible antes de una futura indexación.
- El modelo de embeddings no está explícito en el JSON: verificarlo y mantener compatibilidad con el modelo de consulta y la dimensión del índice.
- El almacenamiento utiliza insert. No se observa deduplicación o sustitución explícita de documentos; reindexar podría agregar duplicados.
- No se observa ruta de error específica en este workflow.

## Copia para repositorio

[JSON anonimizado](../workflows/Holocaust_Site_Index_Documents_Export_Anonimizado.json). Se eliminaron referencias de credenciales, datos fijados y metadatos de instancia. Se mantuvieron la lógica original y active=false. Requiere reconectar OpenAI y Supabase al importar.

Este archivo aporta evidencia de diseño de la indexación, no de una ejecución exitosa reciente.
