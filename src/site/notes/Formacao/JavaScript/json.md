---
{"dg-publish":true,"permalink":"/formacao/java-script/json/","metatags":{"description":"é um formato leve de intercâmbio de dados"},"noteIcon":2,"updated":"2026-02-14T00:59:02.441-03:00"}
---

#JavaScript #Webdesign

# Formato JSON

O **JSON**, que significa **JavaScript Object Notation** (Notação de Objetos JavaScript), é um formato leve de intercâmbio de dados. Criado por **Douglas Crockford** por volta de 2001, ele se tornou o padrão para a troca de informações entre navegadores e servidores, superando o uso do XML por ser mais simples de ler e nativo ao JavaScript.

Abaixo estão os pontos principais para entender o JSON

## 1. Natureza e Estrutura

- **Serialização:** O JSON é uma forma de **serializar** objetos, ou seja, converter objetos complexos em texto para que possam ser transmitidos pela rede.
- **Dicionário de Dados:** Sua estrutura básica é a de um **dicionário** (também chamado de mapa ou _hashtable_), composto por pares de **chave e valor**.
- **Sintaxe Familiar:** Por ser baseado na sintaxe de objetos do próprio JavaScript, um código JSON é um código JavaScript válido.

## 2. Tipos de Dados Suportados

O JSON permite representar informações combinando seis tipos de dados fundamentais:

- **Strings:** Sequências de caracteres entre aspas.
- **Números:** Valores inteiros ou decimais.
- **Booleanos:** Valores lógicos `true` ou `false`.
- **Listas (Arrays):** Sequências ordenadas de valores, delimitadas por colchetes `[]`.
- **Objetos:** Coleções de chaves e valores delimitadas por chaves `{}`.
- **Null:** Representa a ausência de valor.

## 3. Integração com JavaScript

Uma das maiores vantagens do JSON é a facilidade com que o JavaScript o manipula através de métodos nativos:

- **`JSON.parse()`:** Converte uma string formatada em JSON de volta para um objeto JavaScript utilizável.
- **`JSON.stringify()`:** Converte um objeto ou array JavaScript em uma string JSON. Este método é frequentemente usado para criar **cópias profundas** (_deep copies_) de arrays, garantindo que a nova cópia seja totalmente independente da original.

## 4. Uso com AJAX

Embora a sigla AJAX signifique "Asynchronous JavaScript and **XML**", o uso de **JSON** é atualmente onipresente nessas comunicações assíncronas. Bibliotecas como o **[[Formacao/JavaScript/JQuery\|JQuery]]** possuem métodos específicos, como o `$.getJSON()`, que automatizam a requisição de dados ao servidor e já entregam a resposta convertida em um objeto JavaScript pronto para uso.

**Exemplo de um objeto JSON:**

```json
{
  "titulo": "Dominando JavaScript com jQuery",
  "autor": "Plínio Balduino",
  "capitulos": ["Introdução", "AJAX", "JSON"],
  "disponivel": true
}
```

Exemplo XML:

```xml
<livro>
  <titulo>Dominando JavaScript com jQuery</titulo>
  <autor>Plínio Balduino</autor>
  <capitulos>
    <capitulo>Introdução</capitulo>
    <capitulo>AJAX</capitulo>
    <capitulo>JSON</capitulo>
  </capitulos>
  <disponivel>true</disponivel>
</livro>
```
