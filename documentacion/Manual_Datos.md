# Manual operativo de datos — Study the Holocaust

Esquema consultado directamente en Airtable el 21 de septiembre de 2026. Esta versión documenta la estructura real; su incorporación al PDF final queda pendiente.

## Base y relaciones

Base: **STH Content Pipeline**. Contiene **Centro de Comando** y **Consultas Agente**. Los campos `Consultas Agente` y `Contenido vinculado` son enlaces recíprocos entre ambas tablas y permiten múltiples registros. La existencia de la relación no acredita que todos los workflows la completen automáticamente.

## Centro de Comando

Campo principal: Idea Semilla.

| Campo | Tipo exacto de Airtable | Opciones / relación |
|---|---|---|
| Idea Semilla | singleLineText | — |
| Estado | multipleSelects | `Idea`, `Borrador`, `Revisión HITL`, `Aprobado`, `Publicado`, `Rechazado`, `Esperando Aprobacion `, `En `, `En revision` |
| Borrador Generado | singleLineText | — |
| Aprobado | checkbox | — |
| Canal de Publicación | multipleSelects | `Blog STH`, `Twitter/X`, `Instagram`, `Newsletter` |
| Fecha de Ejecución | createdTime | — |
| Notas del Revisor | singleLineText | — |
| Consultas Agente | multipleRecordLinks | Consultas Agente |

## Consultas Agente

Campo principal: Id Consultas.

| Campo | Tipo exacto de Airtable | Opciones / relación |
|---|---|---|
| Id Consultas | singleLineText | — |
| Fecha/Hora | dateTime | — |
| Session ID | singleLineText | — |
| Pregunta | multilineText | — |
| Respuesta | multilineText | — |
| Fuente usada | singleSelect | Sin opciones configuradas |
| Estado | singleSelect | `Procesado`, `En revision`, `Aprobado`, `Rechazad`, `Error` |
| Requiere revisión | checkbox | — |
| Error | multilineText | — |
| Contenido vinculado | multipleRecordLinks | Centro de Comando |
| Canal | singleSelect | `Web`, `Gmail` |

## Reglas de transferencia

- `Estado` en Centro de Comando es selección múltiple: el valor de rechazo se envía como `["Rechazado"]`.
- `Estado` en Consultas Agente es selección simple: un estado se envía como texto, por ejemplo `"Procesado"`.
- Los checkbox usan booleanos, no las cadenas `"true"` o `"false"`.
- Los enlaces entre tablas usan IDs de registros; no confundirlos con el campo de texto `Id Consultas`.
- `Fecha de Ejecución` es `createdTime`: indica la creación del registro, no cada ejecución del workflow.
- Conservar el nombre exacto de las opciones, incluidos los espacios, hasta efectuar una normalización coordinada con los workflows.

## Ejemplo de actualización HITL

Objeto de campos ilustrativo para el rechazo; no representa el JSON completo del workflow:

```json
{
  "fields": {
    "Estado": ["Rechazado"],
    "Aprobado": false,
    "Notas del Revisor": "Rechazado por humano"
  }
}
```

La actualización utiliza el ID del registro encontrado por Search records. El ensayo validado utilizó un solo registro pendiente. Ver [prueba de rechazo](Prueba_HITL_Rechazo.md).

## Lecturas y escrituras documentadas

| Flujo | Tabla | Operación |
|---|---|---|
| Agente educativo | Consultas Agente | Registro de la consulta y respuesta; pendiente contrastar el mapeo con el JSON final |
| Gestión de errores | Consultas Agente | Registro del error; evidencia histórica pendiente de incorporar |
| HITL | Centro de Comando | Búsqueda de contenido pendiente y actualización posterior al rechazo |

## Observaciones para el cierre

- En Centro de Comando existen las opciones `Esperando Aprobacion ` y `En ` con espacio final. Se conservan tal como aparecen en el esquema.
- En Consultas Agente la opción de rechazo se llama exactamente `Rechazad`, sin la letra final. No equivale a `Rechazado` de Centro de Comando.
- `Fuente usada` no tiene opciones configuradas; no se acredita trazabilidad por fuente a partir de ese campo vacío.
- Tener disponibles opciones como Aprobado o Publicado no demuestra una ejecución o publicación efectiva.
- Revisar enlaces de lectura y ejemplos finales antes de entregar. No publicar identificadores de sesión reales, consultas privadas ni credenciales en las evidencias.
