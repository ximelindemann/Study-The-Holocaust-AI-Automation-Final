# Revisión estática del export HITL

Fuente: STH HITL Approval - FINAL.json, descargado el 21 de septiembre de 2026. Workflow inactivo, con seis nodos. No se ejecutó ni se publicó durante esta revisión.

## Hallazgo en el IF

El archivo tiene `leftValue: "=={{ $json.data.approved }}"`, operador `string / equals` y `rightValue: "is true"`. Esto compara texto, no evalúa el booleano de Gmail. La prueba de rechazo exitosa confirma el recorrido y actualización por FALSE, pero no demuestra una clasificación correcta de ambos valores de aprobación.

Corrección requerida en la interfaz: expresión `{{ $json.data.approved }}`, tipo Boolean, operador is true. En el archivo exportado, la expresión debe llevar un solo marcador inicial `=`.

## Rama TRUE

Update record tiene Aprobado en true e ID dinámico correcto. Estado está guardado como texto JSON `"[\"Aprobado\"]"`, no como una expresión que produce array. Requiere cambiar Estado al modo Expression con `{{ ["Aprobado"] }}` y verificar su resultado como array.

## Rama FALSE

Update record1 tiene ID dinámico con un solo marcador de expresión, Estado como `={{ ["Rechazado"] }}`, Aprobado false y Notas del Revisor Rechazado por humano. Coincide con la configuración del rechazo documentado.

## Operación y límites

Search records filtra `{Estado} = "En revision"`. Entre la búsqueda y el correo no hay un cambio de estado para bloquear registros mientras esperan decisión. Mantener sin publicar hasta revisar la prevención de duplicados. El uso de `.first()` se probó con un único registro pendiente y requiere revisión antes de procesar varios simultáneamente.

## Archivo incorporado

[Export anonimizado](../workflows/STH_HITL_Export_Anonimizado.json). Se conserva la configuración funcional recibida para trazabilidad. Se quitaron referencias de credenciales, webhookId, datos fijados y metadatos; el correo del revisor se sustituyó por un marcador. Al importar, reconectar credenciales y configurar el destinatario.

Las correcciones de IF y TRUE están identificadas, pero todavía no aplicadas en la instancia ni acreditadas por una prueba de aprobación.
