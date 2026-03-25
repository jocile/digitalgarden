---
{"dg-publish":true,"permalink":"/videos-base/","metatags":{"description":"Vídeos preferidos"},"contentClasses":"cards","noteIcon":"default","updated":"2026-03-25T10:55:46.745-03:00","dg-note-properties":{"class":"mapa","cssclasses":["cards"]}}
---

#teste/funciona 

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
      - created
      - duration
      - watched
      - thumbnailUrl
    sort:
      - property: channel
        direction: ASC

```
