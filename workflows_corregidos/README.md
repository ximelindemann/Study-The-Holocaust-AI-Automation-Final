# Workflows corregidos - revision

Esta carpeta describe copias de revision preparadas localmente. No reemplaza los exports anonimizados originales de `workflows/`.

## Archivos locales preparados

En el workspace local se generaron:

- `output/workflows_corregidos/Holocaust_Studies_Chat_Agent_Export_CORREGIDO_REVISION.json`
- `output/workflows_corregidos/STH_HITL_Export_CORREGIDO_REVISION.json`
- `output/workflows_corregidos/Holocaust_Site_Index_Documents_Export_REVISION.json`

## Cambios funcionales preparados

### Agente educativo

- Cambiar expresiones con doble igual `=={{ ... }}` a `={{ ... }}`.
- Reemplazar fechas fijas `2026-09-18T00:00:00` por `={{ $now.toISO() }}`.
- Mantener el registro de exito y el registro de error, pero probarlos antes de declararlos cerrados.

### HITL

- Cambiar el IF de aprobacion para evaluar un booleano real:

```js
={{ $json.data.approved }}
```

- Cambiar `Estado` de la rama TRUE para enviar array a Airtable:

```js
={{ ["Aprobado"] }}
```

El motivo es que `Estado` en Airtable, tabla `Centro de Comando`, es `multipleSelects`.

## Estado

Estas correcciones estan preparadas para aplicar y probar en n8n. Todavia falta:

- prueba real del agente;
- prueba real del TRUE;
- captura de evidencias;
- actualizacion del PDF final.
