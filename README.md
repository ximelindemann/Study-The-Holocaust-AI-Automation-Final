# Study the Holocaust - AI Automation Final

Proyecto final de AI Automation para Coderhouse.

## Resumen

Ecosistema de automatización con IA para Study the Holocaust. El sistema combina n8n, Airtable, OpenAI, Supabase RAG y revisión humana por Gmail para responder consultas educativas, registrar interacciones y controlar decisiones editoriales antes de cualquier acción crítica.

## Componentes

- `Holocaust Studies Chat Agent -FINAL`: agente educativo con GPT-5 nano, recuperación RAG y registro en Airtable.
- `STH HITL Approval - FINAL`: flujo de revisión humana por Gmail con ramas de aprobación y rechazo.
- `Holocaust Site - Index Documents`: indexación controlada del sitio hacia Supabase/documents.
- `STH Content Pipeline`: base de Airtable con Centro de Comando, Consultas Agente y Dashboard Público STH.

## Evidencia validada

- HITL rechazo: ejecución n8n `11595`, estado final `Rechazado`.
- Agente educativo: ejecución n8n `11597`, consulta sobre Kristallnacht y registro `Procesado`.
- HITL aprobación: ejecución n8n `11600`, estado final `Aprobado` y checkbox activado.
- Dashboard ejecutivo: 14 consultas totales, 9 procesadas, 2 errores, tasa de error 14,29 %, 1 contenido aprobado y 2 rechazados.

## Enlaces

- Sitio educativo: https://studytheholocaust.org/
- Dashboard público Airtable: https://airtable.com/appnkoN6JcAcSAVDg/shrYxSBg2VbQ6KLvz
- Video demo 3 minutos: pendiente de grabación.

## Workflows finales

Los exports finales están en `workflows_corregidos/` y se mantienen con `active=false` para evitar consumo de cuota o ejecuciones accidentales.

- [Agente educativo final](workflows_corregidos/Holocaust_Studies_Chat_Agent_Export_FINAL.json): incluye `maxTokens = 600`, RAG, registro exitoso y ruta local de error.
- [HITL final](workflows_corregidos/STH_HITL_Export_FINAL.json): incluye Schedule explícito cada 30 minutos, reserva previa `Esperando Aprobacion`, ramas TRUE/FALSE y actualización final de Airtable.
- [Indexación final](workflows_corregidos/Holocaust_Site_Index_Documents_Export_FINAL.json): indexación controlada del sitio hacia Supabase.

También se conservan los exports anonimizados originales en `workflows/` como respaldo histórico.

## Documentación de cierre

- [Checklist de entrega final](documentacion/Checklist_Entrega_Final.md)
- [Auditoría contra consigna completa](documentacion/Auditoria_Consigna_Completa.md)
- [Matriz de rúbrica](documentacion/Matriz_Rubrica_Entrega_Final.md)
- [Plan técnico n8n sin ejecutar](documentacion/Plan_Cambios_N8N_Sin_Ejecutar.md)
- [Prueba agente Kristallnacht](documentacion/Prueba_Agente_Kristallnacht.md)
- [Prueba HITL aprobación](documentacion/Prueba_HITL_Aprobacion.md)
- [Prueba HITL rechazo](documentacion/Prueba_HITL_Rechazo.md)

## Estado contra rúbrica

| Criterio | Estado |
|---|---|
| Mapa de Arquitectura del Sistema | Cubierto en PDF/documentación: triggers, routers, IA, Gmail, Airtable, Supabase y destinos. |
| Manual Operativo de Estructuras de Datos | Cubierto con tablas, relaciones y contratos JSON. |
| Estrategia de Optimización de Costos y Recursos | Cubierto con matriz comparativa y elección de modelos por tarea. |
| Seguridad, Privacidad y Resiliencia | Cubierto con minimización, HITL, error handling local, workflows desactivados y plan técnico de cierre. |
| Dashboard de Control Ejecutivo | Cubierto con enlace público de Airtable y KPIs operativos. |

## Pendientes reales antes de la entrega final

- Subir el PDF final actualizado al repositorio si la plataforma exige verlo desde GitHub. La versión final ya fue generada localmente como `Entrega_Final_STH_Final.pdf`.
- Grabar y enlazar el video obligatorio de 3 minutos.
- Si se activan workflows reales en n8n, replicar/confirmar en la UI los cambios ya presentes en los exports finales y no repetir pruebas TRUE/FALSE ya validadas.

## Regla de uso

No repetir ejecuciones ya aprobadas. Antes de consumir cuota nueva, revisar historial de n8n para reutilizar evidencias existentes. Los workflows quedan despublicados hasta terminar controles finales.
