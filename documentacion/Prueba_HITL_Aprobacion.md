# Prueba HITL - aprobacion humana

## Estado

Prueba ejecutada correctamente.

## Workflow

- Nombre: `STH HITL Approval - FINAL`
- ID: `JAt9PduSufOWwV0J`
- Ejecucion principal: `11600`
- Fecha/hora de inicio: `2026-09-22T20:29:47.879Z`
- Fecha/hora de fin: `2026-09-22T20:30:00.815Z`
- Estado: `success`
- Modo: `manual`

## Registro probado

- Airtable table: `Centro de Comando`
- Record ID: `recpbDJmlxMkvahbM`
- Idea Semilla: `El papel de los Judenrate en los guetos`
- Estado inicial: `En revision`
- Aprobado inicial: desmarcado

## Resultado de la decision humana

El correo de revision fue aprobado por la usuaria. El nodo Gmail devolvio:

```json
{
  "data": {
    "approved": true,
    "respondedAt": "2026-09-22T20:29:59.936Z"
  }
}
```

## Ruta ejecutada

Nodos verificados:

- `Search records`: encontro el registro `recpbDJmlxMkvahbM`.
- `Send message and wait for response`: recibio aprobacion humana.
- `If`: evaluo `approved = true`.
- `Update record`: ejecuto la rama TRUE.
- `Update record1`: no se ejecuto.

## Resultado en Airtable

El registro quedo actualizado como:

```json
{
  "Aprobado": true,
  "Estado": ["Aprobado"],
  "Idea Semilla": "El papel de los Judenrate en los guetos"
}
```

## Ejecucion secundaria observada

Al estar publicado durante la prueba, se genero una ejecucion adicional por trigger:

- Ejecucion: `11601`
- Estado: `success`
- Resultado: `Search records` devolvio cero registros.

No actualizo ningun registro.

## Conclusiones

- [x] La rama TRUE funciona.
- [x] El IF evalua correctamente `approved = true`.
- [x] Airtable acepta `Estado = ["Aprobado"]`.
- [x] El checkbox `Aprobado` queda marcado.
- [x] El workflow fue despublicado despues de la prueba para evitar consumo.
