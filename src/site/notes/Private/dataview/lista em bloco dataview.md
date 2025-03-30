---
{"dg-publish":true,"dg-path":"Teste/lista em bloco dataview.md","permalink":"/teste/lista-em-bloco-dataview/","contentClasses":"list-cards","updated":"2025-03-30T20:09:41.056-03:00"}
---


>[!summary]- Teologia
> ```dataview
>  LIST " (" + dateformat(file.mtime, "dd.MM.yy") + ")"  + "<br>"
>  + dg-metatags.description + "<br>"
>  + file.tags
>  FROM "Teologia"
>  WHERE dg-publish
>  SORT file.mtime DESC
