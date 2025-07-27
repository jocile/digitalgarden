---
{"dg-publish":true,"permalink":"/tecnico/ferramentas/vscode/v-scode-html-com-pt-br/","metatags":{"description":"modificar o atalho no vscode onde cria a estrutura básica do HTML"},"noteIcon":1,"updated":"2025-07-26T20:16:29.838-03:00"}
---

#vscode

Pra modificar o atalho no vscode onde cria a estrutura básica do HTML é bem simples:

1. Entre em configurações (CTRL + ,) 
2. procure por Emmet
3. Em Emmet: Preferences clique em `edit settings.json`
4. Cole o seguinte código no final depois da chave `},` o seguinte:

```
"emmet.variables":{
 "lang":"pt-BR",
 "charset":"UTF-8"
}
```

[[Tecnico/Ferramentas/Vscode/IDE VScode\|IDE VScode]]
