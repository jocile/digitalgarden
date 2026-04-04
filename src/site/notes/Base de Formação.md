---
{"dg-publish":true,"permalink":"/base-de-formacao/","metatags":{"description":"Base de Formações"},"tags":["base"],"noteIcon":"default","updated":"2026-04-04T12:05:32.399-03:00","dg-note-properties":{"class":"mapa","tags":["base"]}}
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
      - habilidades
    sort:
      - property: horas-aula
        direction: ASC
  - type: cards
    name: Visualizaçao card
    filters:
      and:
        - file.folder == "Formacao"
        - class == "classe-formacao"
    order:
      - file.name
      - habilidades
    imageFit: contain

```