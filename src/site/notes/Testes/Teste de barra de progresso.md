---
{"dg-publish":true,"permalink":"/testes/teste-de-barra-de-progresso/","tags":["teste/funciona","exemplo"],"updated":"2025-04-05T20:31:18.476-03:00"}
---


- [x] ativ-1
- [/] ativ-2
- [>] ativ-3

```dataviewj
= "<progress value='" + (length(filter(this.file.tasks.completed, (t) => t = true)) / length(this.file.tasks)) * 100 + "' max='100'></progress>" + "<br>" + round((length(filter(this.file.tasks.completed, (t) => t = true)) / length(this.file.tasks)) * 100) + "% completado"
```

[Progress bars - Minimal Documentation](https://minimal.guide/progress-bars)
