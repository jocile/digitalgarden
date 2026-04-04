---
{"dg-publish":true,"permalink":"/formacao-base/","metatags":{"description":"Base de Formações"},"pinned":true,"tags":["teste/nao-funciona","base"],"noteIcon":2,"updated":"2026-04-04T10:55:21.817-03:00","dg-note-properties":{"class":"mapa","tags":["teste/nao-funciona","base"]}}
---


# Formação

```base
formulas:
  description: note["dg-metatags"].description
properties:
  formula.description:
    displayName: Descrição
views:
  - type: table
    name: Tabela
    filters:
      and:
        - file.name != this.file.name
        - note["dg-publish"] == true
        - file.folder == "Formacao"
    order:
      - file.name
      - horas-aula
      - status
      - link
      - finished
    sort:
      - property: finished
        direction: ASC
      - property: file.name
        direction: ASC
  - type: table
    name: Visualizaçao padrão

```