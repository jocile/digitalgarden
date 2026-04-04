---
{"dg-publish":true,"permalink":"/base-de-vagas/","metatags":{"description":"Oportunidades em emprego"},"contentClasses":"row-hover","tags":["vagas","teste"],"noteIcon":"default","updated":"2026-04-04T12:41:23.157-03:00","dg-note-properties":{"class":"mapa","cssclasses":["row-hover"],"tags":["vagas","teste"]}}
---


## Vagas na cidade de Sobral - CE

```base
filters:
  and:
    - file.folder == "clipper/brvagas.com.br"
    - note["dg-publish"] == true
views:
  - type: table
    name: Vagas
    order:
      - file.name
      - data-limite
    sort:
      - property: data-limite
        direction: ASC
  - type: cards
    name: cards
    order:
      - file.name
      - data-limite
      - Descricao

```
