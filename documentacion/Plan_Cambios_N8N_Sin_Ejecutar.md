# Plan de cambios n8n sin ejecutar workflows

Fecha: 23/09/2026.

Objetivo: cerrar requisitos técnicos sin repetir pruebas ya aprobadas y sin consumir ejecuciones hasta que sea estrictamente necesario.

## Estado verificado

- HITL FALSE/Rechazo: ejecución `11595`.
- Agente educativo: ejecución `11597`.
- HITL TRUE/Aprobación: ejecución `11600`.
- Dashboard público Airtable creado y probado sin login.

## Cambios ya preparados en exports finales

### 1. Límite de salida del modelo

Archivo: `workflows_corregidos/Holocaust_Studies_Chat_Agent_Export_FINAL.json`.

Nodo: `OpenAI Chat Model`.

Cambio preparado:

```json
"options": {"maxTokens": 600}
```

### 2. Prevención de duplicados en HITL

Archivo: `workflows_corregidos/STH_HITL_Export_FINAL.json`.

Cambio preparado:

1. `Search records` busca `{Estado} = "En revision"`.
2. Nuevo nodo `Reservar registro HITL` cambia el estado a `["Esperando Aprobacion "]` antes de Gmail.
3. Gmail `sendAndWait` espera la decisión humana.
4. TRUE/FALSE actualizan a `Aprobado` o `Rechazado`.

### 3. Schedule explícito

El Schedule final queda configurado cada 30 minutos en el export, pero el workflow sigue con `active=false`.

## Regla antes de ejecutar

Antes de consumir cuota:

1. Revisar historial de n8n.
2. Reutilizar ejecuciones existentes si cubren la consigna.
3. No repetir TRUE, FALSE ni consulta educativa ya validadas.
4. Replicar/confirmar estos cambios en la UI de n8n antes de activar workflows reales.
