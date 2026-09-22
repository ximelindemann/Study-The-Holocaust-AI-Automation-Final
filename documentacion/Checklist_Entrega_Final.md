# Checklist de entrega final - Study the Holocaust

Estado al 22/09/2026. Este documento separa lo ya acreditado de lo pendiente para no presentar como terminado algo que todavia necesita prueba.

## 1. Repositorio y archivos base

- [x] Repositorio nuevo creado: `ximelindemann/Study-The-Holocaust-AI-Automation-Final`.
- [x] README inicial subido.
- [x] Exports de n8n anonimizados y sin credenciales:
  - `Holocaust_Studies_Chat_Agent_Export_Anonimizado.json`
  - `STH_HITL_Export_Anonimizado.json`
  - `Holocaust_Site_Index_Documents_Export_Anonimizado.json`
- [x] Capturas de la prueba HITL de rechazo subidas.
- [x] PDF de revision armado.
- [ ] PDF final actualizado luego de cerrar pruebas.
- [ ] README final actualizado con estado real, enlaces y evidencias definitivas.

## 2. Agente educativo

- [x] Export del agente inspeccionado.
- [x] Modelo identificado en el export: `gpt-5-nano`.
- [x] RAG identificado: Supabase vector store, tabla `documents`, `topK = 5`.
- [x] Registro de exito y salida de error identificados en Airtable.
- [x] Corregir expresiones con doble igual `=={{ ... }}` en nodos de Airtable.
- [x] Reemplazar fechas fijas `2026-09-18T00:00:00` por fecha dinamica.
- [x] Quitar configuracion invalida `builtInTools` del nodo OpenAI.
- [x] Probar pregunta educativa real. Ejecucion `11597`.
- [x] Verificar respuesta generada internamente por el agente.
- [x] Verificar registro creado en Airtable `Consultas Agente`.
- [x] Capturar evidencia visual del agente: workflow en verde y `Edit Fields` con output textual.
- [x] Documentar el caso de prueba en GitHub: `documentacion/Prueba_Agente_Kristallnacht.md`.

## 3. HITL - rechazo

- [x] Campo `Estado` verificado en Airtable como `multipleSelects`.
- [x] Opcion `Rechazado` verificada en Airtable.
- [x] Mapeo correcto para rechazo identificado: `{{ ["Rechazado"] }}`.
- [x] Prueba de rechazo ejecutada correctamente.
- [x] Captura del workflow con rama FALSE verde.
- [x] Captura de Airtable con registro rechazado.
- [ ] Completar documentacion con ID de ejecucion, fecha y resultado final.

## 4. HITL - aprobacion

- [x] Opcion `Aprobado` verificada en Airtable.
- [x] Problema del export identificado: IF compara texto en vez de booleano.
- [x] Problema del export identificado: TRUE manda `Estado` como texto JSON.
- [x] Corregir IF para evaluar booleano real: `{{ $json.data.approved }}`.
- [x] Corregir TRUE para mandar array: `{{ ["Aprobado"] }}`.
- [x] Ejecutar prueba controlada de aprobacion. Ejecucion `11600`.
- [x] Verificar rama TRUE verde.
- [x] Verificar Airtable con `Estado = Aprobado` y checkbox `Aprobado` marcado.
- [x] Capturar evidencia.
- [x] Documentar prueba en GitHub: `documentacion/Prueba_HITL_Aprobacion.md`.

## 5. Indexacion del sitio

- [x] Export de indexacion inspeccionado.
- [x] URL principal identificada: `https://studytheholocaust.org/`.
- [x] Proceso identificado: HTTP GET, extraccion HTML, limpieza, embeddings y Supabase.
- [ ] Verificar credenciales/modelo de embeddings en n8n antes de ejecutar.
- [ ] Confirmar si se indexa solo homepage o mas paginas.
- [ ] Probar una indexacion controlada si hace falta para evidencia.
- [ ] Documentar limites de indexacion y deduplicacion.

## 6. Pruebas minimas recomendadas

- [x] Prueba 1: HITL rechazo.
- [x] Prueba 2: HITL aprobacion.
- [x] Prueba 3: agente responde pregunta educativa.
- [x] Prueba 4: agente registra consulta en Airtable.
- [ ] Prueba 5: caso de seguridad/error documentado.
- [ ] Prueba 6 opcional: indexacion o recuperacion RAG documentada.

## 7. Costos y eficiencia

- [x] TP6 revisado como antecedente aprobado con 100%.
- [x] Correccion docente incorporada: sumar explicitamente `US$ 0,0045` por primera escritura de cache antes de redondear.
- [x] Costos del agente calculados como escenario ilustrativo con `gpt-5-nano` vs `gpt-5-mini`.
- [ ] Revisar si hay costos de herramientas, busqueda web, n8n, Airtable o Supabase que deban mencionarse como excluidos.

## 8. Seguridad, datos y resiliencia

- [x] Exports publicos sin credenciales.
- [x] Workflow activo marcado como `false` en exports.
- [x] Error path del agente identificado.
- [x] Registro normal del agente corregido y probado.
- [ ] Corregir/probar registro de errores del agente.
- [ ] Documentar que no se publica automaticamente sin aprobacion humana.
- [ ] Definir vista compartida sin datos sensibles.
- [ ] Documentar riesgo de duplicados en HITL si el Schedule queda activo sin bloqueo de estado.

## 9. Dashboard / vista publica

- [ ] Crear o documentar vista de solo lectura.
- [ ] Incluir metricas minimas:
  - consultas procesadas;
  - consultas con error;
  - tasa de error;
  - contenidos en revision;
  - contenidos aprobados;
  - contenidos rechazados.
- [ ] Agregar enlace o captura.
- [ ] Incorporar al README y PDF final.

## 10. Video de entrega

- [ ] Preparar guion de 3 minutos.
- [ ] Mostrar GitHub.
- [ ] Mostrar PDF final.
- [ ] Mostrar agente funcionando.
- [ ] Mostrar Airtable con registro de consulta.
- [ ] Mostrar HITL rechazo y aprobacion.
- [ ] Explicar costos y controles de seguridad.
- [ ] Subir o enlazar video.

## Orden recomendado de cierre

1. Subir capturas nuevas del agente y HITL aprobacion a GitHub.
2. Completar prueba/documentacion de error o seguridad.
3. Completar dashboard o vista de lectura.
4. Actualizar PDF final.
5. Actualizar README y GitHub.
6. Grabar video.
