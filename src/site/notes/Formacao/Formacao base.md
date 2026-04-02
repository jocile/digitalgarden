---
{"dg-publish":true,"permalink":"/formacao/formacao-base/","metatags":{"description":"Base de Formações"},"pinned":true,"tags":["teste","base"],"noteIcon":2,"updated":"2026-04-02T16:42:34.653-03:00","dg-note-properties":{"class":"mapa","tags":["teste","base"]}}
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
        - file.folder == this.file.folder
        - file.name != this.file.name
        - note["dg-publish"] == true
    order:
      - file.name
      - horas-aula
      - status
      - link
      - finished
    sort:
      - property: file.name
        direction: ASC
      - property: formula.description
        direction: ASC
  - type: table
    name: Visualizaçao padrão

```