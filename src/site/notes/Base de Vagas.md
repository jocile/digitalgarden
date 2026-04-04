---
{"dg-publish":true,"permalink":"/base-de-vagas/","metatags":{"description":"Oportunidades em emprego"},"tags":["vagas","teste"],"noteIcon":"default","updated":"2026-04-04T12:25:52.313-03:00","dg-note-properties":{"class":"mapa","tags":["vagas","teste"]}}
---


## Vagas na cidade de Sobral - CE

```base
filters:
  and:
    - file.folder == "clipper/brvagas.com.br"
    - "!link.isEmpty()"
views:
  - type: table
    name: Vagas
    order:
      - link
      - data-limite
    sort:
      - property: data-limite
        direction: ASC

```
