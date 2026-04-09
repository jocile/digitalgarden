---
{"dg-publish":true,"permalink":"/22-teologia/novo-testamento/novo-testamento/","metatags":{"description":"Evangelhos, Atos, cartas e Apocalipse "},"pinned":true,"contentClasses":"cards","noteIcon":2,"updated":"2026-03-26T15:43:18.939-03:00","dg-note-properties":{"class":"mapa","cssclasses":["cards"],"topics":null}}
---


# Novo Testamento

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

