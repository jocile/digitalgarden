---
{"dg-publish":true,"permalink":"/30-recursos/windows/hardlink/","metatags":{"description":"cria um clone direto que aponta para os dados físicos no disco do Windows"},"noteIcon":2,"updated":"2026-06-05T08:11:41.927-03:00","dg-note-properties":{"class":"tecnico","cssclasses":null,"topics":["Sistemas Operacionais","Windows"]}}
---

#Windows

# Links no Windows

>[!summary] 
> No Windows, o termo "links" ==pode se referir a atalhos de sites na Área de Trabalho, links de sistema (como links simbólicos), ou ao menu de links rápidos do sistema==.
> No Windows, ==o Hardlink cria um clone direto que aponta para os dados físicos no disco, enquanto o Symlink funciona como um atalho avançado que aponta para o caminho do arquivo original==.

## 📌 Diferenças Práticas

- Hardlink (Link Rígido)
    
    - Aponta para o conteúdo (dados) no disco.
    - Funciona apenas no mesmo disco/partição.
    - Se apagar o original, o link continua funcionando.
    - Programas antigos aceitam perfeitamente.
    
- Symlink (Link Simbólico)
    
    - Aponta para o caminho (texto) do arquivo.
    - Funciona entre discos e redes diferentes.
    - Se apagar o original, o link quebra (fica inválido).
    - Alguns programas antigos percebem que é um atalho.
    

### 🔄 Comparativo Direto

|Recurso|Hardlink|Symlink|
|---|---|---|
|Alvo|Arquivos apenas|Arquivos e Pastas|
|Entre Discos (C: para D:)|Não|Sim|
|Se mover o original|Continua funcionando|Quebra|
|Espaço em disco|Zero (compartilhado)|Ínfimo (bytes)|

## 🌐 Criar atalho para um site na Área de Trabalho

1. Copie a URL do site desejado no seu navegador.
2. Clique com o botão direito em um espaço vazio da Área de Trabalho.
3. Selecione Novo e depois clique em Atalho.
4. Cole o link do site no campo de endereço e clique em Avançar.
5. Escolha um nome para o atalho e clique em Concluir.

## 💻 Menu de Link Rápido (Funções do Sistema)

- Pressione as teclas `Windows + X` no teclado.
- Um menu pop-up abrirá com links diretos para o Gerenciador de Tarefas, Configurações e Terminal.

## 🛠️ Links Avançados do Sistema (Symlinks)

Para desenvolvedores e usuários avançados, o Windows suporta [Links Simbólicos (Symlinks)](https://learn.microsoft.com/pt-br/windows/win32/fileio/symbolic-links). Eles servem para espelhar pastas ou arquivos em caminhos diferentes sem duplicar o espaço em disco.

- Abra o Prompt de Comando como Administrador.
- Use o comando: `mklink /D "C:\Caminho\Do\Link" "C:\Caminho\Da\Pasta_Original"` 

Para fazer um programa pensar que o link é o próprio arquivo PDF original (sem duplicar o espaço em disco), você deve ==criar um Hard Link (Link Rígido) ou um Symbolic Link (Link Simbólico) pelo Prompt de Comando==.

### 🛠️ Como criar o link passo a passo

1. Pressione a tecla Windows.
2. Digite cmd.
3. Clique com o botão direito em "Prompt de Comando" e escolha Executar como Administrador.
4. Use o comando `mklink` seguindo a estrutura abaixo:

```bash
mklink /H "C:\Caminho\Onde\Fica\O_Link.pdf" "C:\Caminho\Do\Arquivo_Original.pdf"
```

### 💡 Detalhes importantes do comando:

- `/H`: Cria um Link Rígido. O Windows tratará o link exatamente como o arquivo real. Se você abrir, editar ou o programa ler o link, estará mexendo no original.
- Aspas `""`: Use aspas obrigatórias se os caminhos das pastas tiverem espaços no nome.
- Exclusão: Se você apagar o link depois, o arquivo original continua intacto.

Você prefere automatizar isso criando um script para usar com um clique:

### 📝 Passo 1: Criar o arquivo do Script

1. Abra o Bloco de Notas do Windows.
2. Copie e cole o código abaixo exatamente como está:

```bash
@echo off
set /p "link_path=Entre com o caminho da pasta ONDE O LINK SERA CRIADO e pressione Enter: "
set /p "orig_path=Entre com o caminho do ARQUIVO PDF ORIGINAL e pressione Enter: "
set /p "link_name=Digite o nome que o link tera (ex: documento.pdf): "

:: Remove aspas duplicadas que o Windows coloca ao arrastar pastas
set "link_path=%link_path:"=%"
set "orig_path=%orig_path:"=%"

:: Executa o comando de link rígido
mklink /H "%link_path%\%link_name%" "%orig_path%"

echo.
echo Link criado com sucesso!
pause
```

1. Clique em Arquivo > Salvar como.
2. No campo "Tipo", mude para Todos os arquivos (_._).
3. Defina o nome como `criar_link.bat` e salve na sua Área de Trabalho.

### 🚀 Passo 2: Como usar o Script

Como o comando `mklink` exige privilégios elevados do Windows, você deve rodar o script como administrador:

1. Clique com o botão direito no arquivo `criar_link.bat`.
2. Selecione Executar como Administrador.
3. Siga as instruções da tela preta (arrastar as pastas e arquivos direto para a janela do prompt facilita o preenchimento dos caminhos).

## Referências

- [Links simbólicos - Win32 apps \| Microsoft Learn](https://learn.microsoft.com/pt-br/windows/win32/fileio/symbolic-links)
- [COMO COLOCAR ATALHO DE UM SITE NA ÁREA DE TRABALHO DO WINDOWS 10 - YouTube](https://www.youtube.com/watch?v=W9rVvd660oA)
- [Como usar o menu Link rápido no Windows 11 - Categoria do produto \| HP Support - YouTube](https://www.youtube.com/watch?v=_0z0cBK8ih0)
- [Windows: aprenda a organizar as pastas e arquivos através de links simbólicos \| G1 - Tecnologia e Games - Tira-dúvidas de Tecnologia](https://g1.globo.com/tecnologia/blog/tira-duvidas-de-tecnologia/post/windows-aprenda-organizar-pastas-e-arquivos-atraves-de-links-simbolicos.html)
- [Links Simbólicos no Windows » Blog do MOL](https://mauriciodelima.com.br/como-usar-links-simbolicos-no-windows-11/)
- [Links simbólicos no Linux: entenda como funcionam os "portais" entre pastas e arquivos](https://diolinux.com.br/tutoriais/links-simbolicos-no-linux.html)
- [Exportar ou importar associações de aplicativo padrão \| Microsoft Learn](https://learn.microsoft.com/pt-br/windows-hardware/manufacture/desktop/export-or-import-default-application-associations?view=windows-11)
