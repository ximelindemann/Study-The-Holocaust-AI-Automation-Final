# Correcciones pendientes de workflows

Este archivo documenta cambios preparados en copias de revision. No reemplaza una prueba real en n8n y no afirma que el flujo ya este validado en produccion.

## Archivos preparados

- `output/workflows_corregidos/Holocaust_Studies_Chat_Agent_Export_CORREGIDO_REVISION.json`
- `output/workflows_corregidos/STH_HITL_Export_CORREGIDO_REVISION.json`
- `output/workflows_corregidos/Holocaust_Site_Index_Documents_Export_REVISION.json`

Los exports originales anonimizados se mantienen intactos en `output/workflows/`.

## Agente educativo

Problema detectado: los nodos que escriben en Airtable tenian expresiones con doble signo igual. Eso puede hacer que n8n guarde texto literal o evalue mal el valor.

Ejemplos corregidos:

```js
={{ $('Chat').item.json.sessionId }}
={{ $('Chat').item.json.chatInput }}
={{ $('Holocaust Studies Agent').item.json.output }}
={{ $json.error?.message ?? $json.message ?? 'Error no especificado' }}
```

Tambien se reemplazo la fecha fija:

```js
2026-09-18T00:00:00
```

por:

```js
={{ $now.toISO() }}
```

Prueba pendiente:

- hacer una pregunta educativa al agente;
- verificar la respuesta en el chat;
- verificar que se cree un registro en Airtable `Consultas Agente`;
- capturar evidencia;
- documentar resultado.

## HITL

Problema detectado: el IF de aprobacion evaluaba texto en lugar del booleano real recibido desde Gmail `sendAndWait`.

Correccion preparada:

```js
={{ $json.data.approved }}
```

con operador booleano `true`.

Problema detectado: la rama TRUE enviaba `Estado` como texto JSON:

```js
["Aprobado"]
```

Correccion preparada:

```js
={{ ["Aprobado"] }}
```

Motivo: en Airtable, `Estado` en `Centro de Comando` es `multipleSelects`; por eso n8n debe mandar array, igual que en el rechazo ya probado.

Prueba pendiente:

- ejecutar una aprobacion controlada;
- verificar rama TRUE verde;
- verificar Airtable con `Estado = Aprobado`;
- verificar checkbox `Aprobado` marcado;
- capturar evidencia;
- documentar resultado.

## Indexacion

El export de indexacion se conserva como revision porque no conviene corregirlo automaticamente sin abrir n8n:

- hay que verificar credencial/modelo de embeddings;
- hay que confirmar si se indexa solo la homepage o mas paginas;
- hay que revisar deduplicacion antes de ejecutar multiples veces.

## Orden sugerido

1. Aplicar correcciones del agente en n8n.
2. Probar agente una sola vez con evidencia.
3. Aplicar correcciones HITL TRUE.
4. Probar aprobacion una sola vez con evidencia.
5. Completar dashboard y PDF final.
