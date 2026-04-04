---
{"dg-publish":true,"permalink":"/base-de-formacao/","metatags":{"description":"Base de Formações"},"contentClasses":"row-hover","tags":["vagas"],"noteIcon":"default","updated":"2026-04-04T12:47:41.826-03:00","dg-note-properties":{"class":"mapa","cssclasses":["row-hover"],"tags":["vagas"]}}
---


# Formação

```base
filters:
  and:
    - file.name != this.file.name
    - file.folder == "Formacao"
    - '!note["horas-aula"].isEmpty()'
formulas:
  description: note["dg-metatags"].description
properties:
  formula.description:
    displayName: Descrição
views:
  - type: table
    name: Visualiação conclusão
    order:
      - file.name
      - finished
      - habilidades
    sort:
      - property: finished
        direction: ASC
  - type: table
    name: Visualizaçao horas-aula
    order:
      - file.name
      - horas-aula
      - topics
    sort:
      - property: horas-aula
        direction: ASC
  - type: cards
    name: Cards
    order:
      - file.name
      - habilidades

```