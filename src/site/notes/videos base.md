---
{"dg-publish":true,"permalink":"/videos-base/","metatags":{"description":"Vídeos preferidos"},"noteIcon":"default","updated":"2026-03-25T11:05:11.659-03:00","dg-note-properties":{"class":"mapa"}}
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
