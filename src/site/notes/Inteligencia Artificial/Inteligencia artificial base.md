---
{"dg-publish":true,"permalink":"/inteligencia-artificial/inteligencia-artificial-base/","metatags":{"description":"Vídeos preferidos"},"pinned":true,"tags":["base","teste","Inteligencia-artificial"],"noteIcon":"default","updated":"2026-04-01T10:24:11.595-03:00","dg-note-properties":{"class":"mapa","tags":["base","teste","Inteligencia-artificial"]}}
---

## [[Inteligencia Artificial\|Inteligencia Artificial]]

```base
formulas:
  description: 'note["dg-metatags"].description'

properties:
  formula.description:
    displayName: "Descrição"

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
      - formula.description
    sort:
      - property: file.name
        direction: ASC
      - property: formula.description
        direction: ASC

```
