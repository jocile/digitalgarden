---
{"dg-publish":true,"permalink":"/base-de-videos/","metatags":{"description":"Vídeos preferidos"},"contentClasses":"row-alt row-hover","tags":["videos","base"],"noteIcon":"default","updated":"2026-04-04T12:16:19.535-03:00","dg-note-properties":{"class":"mapa","cssclasses":["row-alt","row-hover"],"tags":["videos","base"]}}
---


## Vídeos preferidos

```base
filters:
  and:
    - file.folder == "clipper/youtube.com"
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
  - type: cards
    name: Cards
    order:
      - file.name
      - file.tags
    image: note.thumbnailUrl
    imageFit: contain

```
