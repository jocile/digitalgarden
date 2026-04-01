---
{"dg-publish":true,"permalink":"/videos-base/","metatags":{"description":"Vídeos preferidos"},"tags":["videos","teste/funciona","base"],"noteIcon":"default","updated":"2026-04-01T09:58:03.043-03:00","dg-note-properties":{"class":"mapa","tags":["videos","teste/funciona","base"]}}
---


## Vídeos preferidos

```base
views:
  - type: table
    name: Videos
    filters:
      and:
        - file.folder == "clipper/youtube.com"
    order:
      - file.name
      - channel
      - duration
      - watched
    sort:
      - property: channel
        direction: ASC

```
