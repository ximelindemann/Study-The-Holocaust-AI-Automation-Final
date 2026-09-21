# Prueba HITL — Rechazo humano

**Fecha:** 21 de septiembre de 2026.  
**Workflow:** STH HITL Approval - FINAL.  
**Ejecución:** #11595 — Succeeded.  
**Base / tabla:** STH Content Pipeline / Centro de Comando.

## Recorrido

`Schedule Trigger → Search records → Send message and wait for response → If (false) → Update record1`

La prueba parte de un registro en `En revision`. El correo solicita una decisión humana; al elegir rechazar, el workflow continúa por la rama false.

## Configuración

| Campo de Update record1 | Valor |
|---|---|
| id, en modo Expression | `{{ $('Search records').first().json.id }}` |
| Estado, en modo Expression | `{{ ["Rechazado"] }}` |
| Aprobado | false / desactivado |
| Notas del Revisor | Rechazado por humano |

`Estado` es un campo Airtable de selección múltiple (`multipleSelects`). La opción `Rechazado` ya existe y se envía como array de nombres.

El uso de `.first()` corresponde al escenario probado con un único registro pendiente. El procesamiento de varios registros simultáneos requiere una validación adicional de la asociación entre cada decisión y su registro.

## Incidencia corregida

El ID evaluado incluía un signo igual literal al comienzo. Al quitarlo en el editor de expresiones, el valor volvió a ser un ID de registro válido. El campo Estado ya se evaluaba como array en esa inspección.

## Resultado y evidencia

La autora confirmó `WORKFLOW EXECUTED SUCCESSFULLY`. Posteriormente se verificó el estado Succeeded de la ejecución #11595 y el recorrido exitoso por la rama false.

Resultado esperado en Airtable: Estado Rechazado, Aprobado desactivado y Notas del Revisor Rechazado por humano.

La autora confirmó que guardó las dos capturas solicitadas. Está pendiente adjuntarlas y revisar visualmente la captura de Airtable para completar la evidencia del resultado persistido.

Esta prueba valida el recorrido de rechazo. No acredita por sí sola la rama de aprobación ni el conjunto completo de pruebas del proyecto.
