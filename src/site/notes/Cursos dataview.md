---
{"dg-publish":true,"dg-path":"Teste/Atualizacoes table cards dv.md","permalink":"/teste/atualizacoes-table-cards-dv/","title":"<% tp.file.title %>","metatags":{"description":"cursos dataview"},"hideInGraph":true,"contentClasses":"cards","tags":["teste/funciona","cards"],"updated":"2025-04-02T21:34:45.371-03:00"}
---


```dataviewjs
dv.table(["Cover","Titulo", "Descrição", "Carga", "Series", "Inscrição"],
dv.pages('"cursos"')
    .map(p => [
        (function() {
      switch (dv.func.typeof(p.cover)) {
        case "link":
          return dv.fileLink(`${p.cover.path}`, true, 100);
        case "string":
          return dv.fileLink(p.cover, true, "coverImg|100");
        default:
          return "";
        }
      })(),
		p.file.link,
		p.descrição, 
		p.carga,	   
		p["Series"] ? p["Series"] + " #" + p["number-in-series"] : "N/A",
	    p.inscrição
															  
			]) 
)
