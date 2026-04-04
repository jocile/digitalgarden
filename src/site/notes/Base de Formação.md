---
{"dg-publish":true,"permalink":"/base-de-formacao/","metatags":{"description":"Base de Formações"},"tags":["vagas"],"noteIcon":"default","updated":"2026-04-04T12:24:17.409-03:00","dg-note-properties":{"class":"mapa","tags":["vagas"]}}
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
    name: Visualiação conclusão
    filters:
      and:
        - file.name != this.file.name
        - note["dg-publish"] == true
        - file.folder == "Formacao"
    order:
      - file.name
      - finished
      - habilidades
    sort:
      - property: finished
        direction: ASC
  - type: table
    name: Visualizaçao horas-aula
    filters:
      and:
        - file.folder == "Formacao"
        - '!note["horas-aula"].isEmpty()'
    order:
      - file.name
      - horas-aula
      - topics
    sort:
      - property: horas-aula
        direction: ASC

```