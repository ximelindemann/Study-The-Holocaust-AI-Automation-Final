# Costos y eficiencia — TP6 corregido

## Alcance y fuente

Este apartado incorpora la mejora solicitada por el docente sobre `TP6_PreEntrega6_XimeBasualdo.pdf`, páginas 6 y 7. La autora informó una calificación de 100%. Se conservan los supuestos y las tarifas del ejercicio académico; no se presentan como precios actuales verificados ni como gasto medido del agente OpenAI en producción.

Caso: clasificación por lotes de 500 fuentes históricas para Study the Holocaust con Claude Sonnet 4.6, según el TP6. La clasificación por lotes es una propuesta de eficiencia para preparación de contenido; no se acredita su ejecución en los workflows actuales.

## Supuestos del TP6

| Parámetro | Valor |
|---|---:|
| Fuentes | 500 |
| Prefijo fijo por solicitud | 1.200 tokens |
| Contenido variable por solicitud | 800 tokens |
| Salida por solicitud | 400 tokens |
| Input total | 1.000.000 tokens |
| Output total | 200.000 tokens |
| Input estándar | US$3,00 por millón de tokens |
| Output estándar | US$15,00 por millón de tokens |
| Escritura de caché | US$3,75 por millón de tokens |
| Lectura de caché | US$0,30 por millón de tokens |
| Descuento Batch asumido | 50% |

## Corrección solicitada por el docente

> En el subtotal combinado, sumá de forma explícita el costo de la primera escritura del prefijo en caché (US$ 0,0045) antes de redondear el resultado final, para que el cálculo contemple todas las operaciones.

## Matriz corregida siguiendo la aproximación del TP6

| Operación | Cálculo | Resultado sin redondeo intermedio |
|---|---|---:|
| Input base | 1,00 × US$3,00 | US$3,00 |
| Output base | 0,20 × US$15,00 | US$3,00 |
| Total sin optimización | US$3,00 + US$3,00 | **US$6,00** |
| Input variable | 0,40 × US$3,00 | US$1,20 |
| Lecturas de prefijo, aproximación del TP6 | 0,60 × US$0,30 | US$0,18 |
| Primera escritura del prefijo | 0,0012 × US$3,75 | **US$0,0045** |
| Output | 0,20 × US$15,00 | US$3,00 |
| Subtotal con caché, incluida la escritura | 1,20 + 0,18 + 0,0045 + 3,00 | **US$4,3845** |
| Batch sobre el subtotal ajustado | US$4,3845 × 0,50 | **US$2,19225** |
| Total final, redondeado a centavos | Redondear solo al final | **US$2,19** |
| Ahorro absoluto | US$6,00 − US$2,19225 | **US$3,80775** |
| Ahorro porcentual | (3,80775 / 6,00) × 100 | **63,4625% ≈ 63,46%** |

La primera escritura ya no se omite por ser pequeña. El resultado a centavos se mantiene en US$2,19, pero la cuenta expone el costo solicitado por el docente. Los descuentos de Batch y caché se aplican sobre sus bases correspondientes, no se suman sus porcentajes.

### Precisión del conteo de lecturas

La tabla anterior conserva la aproximación de 500 lecturas de prefijo del TP6 para mostrar exactamente la corrección solicitada. Con un conteo estricto de **1 escritura y 499 lecturas**, las lecturas serían 499 × 1.200 / 1.000.000 × US$0,30 = US$0,17964. El subtotal sería US$4,38414 y el total combinado US$2,19207, que también redondea a **US$2,19**. Ambas variantes suponen reutilización efectiva del caché; no son ahorros observados en facturación.

## Aplicación a la entrega final

| Tarea | Estrategia | Estado |
|---|---|---|
| Clasificación editorial de muchas fuentes | Batch y prefijo fijo reutilizable, siguiendo el diseño del TP6 | Escenario académico estimado |
| Conversación del agente educativo | Respuesta interactiva con OpenAI | Costo por consulta pendiente de documentar con modelo y uso reales |
| Indexación RAG | Embeddings y almacenamiento en Supabase | Costo pendiente de inventario de volumen y modelo |
| HITL | Gmail y actualización de Airtable después de una decisión humana | Rechazo probado; contabilizar ejecuciones y planes de servicios aparte |

US$2,19 corresponde al lote académico de clasificación. No es el costo total mensual del ecosistema: no incluye planes de n8n, Airtable o Supabase, ni consultas interactivas, indexación, reintentos o revisiones humanas.

Para cerrar el criterio de costos del proyecto completo falta contrastar el modelo del agente con el JSON exportado, agregar tarifas verificadas y declarar los volúmenes de uso. Este documento queda listo como antecedente corregido para integrar al PDF final.
