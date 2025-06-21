---
{"dg-publish":true,"permalink":"/tecnico/ferramentas/sysinternals/","title":"Ferramentas do Sysinternals","metatags":{"description":"Como instalar o Windows em uma máquina virtual."},"noteIcon":2,"updated":"2025-06-20T21:08:18.925-03:00"}
---

#Ferramentas 

## Introdução às Ferramentas do Sysinternals

Esses utilitários são projetados para ajudar no entendimento do funcionamento interno do Windows, seja para troubleshooting ou simplesmente para explorar como o sistema opera.

### Troubleshooting

Troubleshooting, em português, refere-se ao ==processo de diagnóstico e resolução de problemas em sistemas, equipamentos ou processos==. É uma abordagem sistemática para identificar a causa raiz de um problema e implementar uma solução eficaz, visando restaurar a funcionalidade normal. 

Em termos mais simples, troubleshooting é a ação de procurar e corrigir falhas. Pode ser aplicado em diversas áreas, como informática, engenharia, eletrônica e até mesmo no cotidiano, ao tentar resolver problemas em um carro ou eletrodoméstico, por exemplo. 

Etapas comuns no processo de troubleshooting:

- **Identificação do problema:** Reconhecer que algo não está funcionando corretamente. 
- **Coleta de informações:** Reunir dados sobre o problema, como mensagens de erro, sintomas observados e configurações relevantes. 
- **Análise:** Avaliar as informações coletadas para identificar possíveis causas. 
- **Diagnóstico:** Determinar a causa raiz do problema. 
- **Solução:** Implementar uma ação para corrigir o problema. 
- **Verificação:** Confirmar se a solução implementada resolveu o problema. 

O troubleshooting é uma habilidade crucial para profissionais de diversas áreas, pois permite que eles resolvam problemas de forma eficiente e eficaz, minimizando o tempo de inatividade e garantindo o bom funcionamento de sistemas e equipamentos.

### História e Objetivo

O Sysinternals nasceu em 1996, inicialmente chamado de **NT Internals**, criado junto com Bryce Cogswell. O objetivo desde então foi sempre o mesmo: disponibilizar ferramentas e informações para que você possa compreender melhor como o Windows funciona ou ajudar no troubleshooting quando ele apresentar problemas.

As principais características das ferramentas do Sysinternals são:
- **Únicas:** São executáveis de uma única arquivo.
- **Intuitivas:** Fáceis de usar e entender.
- **Seguras:** Não deixam resíduos no seu sistema após uso.

Originalmente, as ferramentas suportavam Windows 95, 98 e NT. Hoje em dia, elas funcionam para todas as versões do Windows (32-bit, 64-bit e ARM 64-bit).

A seguir a descrição das principais ferramentas do SysInternals.

---

### ZoomIt

**ZoomIt** é uma das minhas favoritas por ser muito útil quando você está apresentando algo na tela ou tentando analisar detalhes. Ela permite ampliar a tela com zoom estático:

#### Zoom Estático

Você pode clicar e arrastar para aumentar uma área específica da tela, como se estivesse usando um zoom manual em uma imagem.

Além disso, você pode usar o teclado para desenhar formas livremente ou específicas (setas, quadrados, círculos) na ampliação:

#### Desenho Livre e Formas Específicas

- Pressione **G** para verde.
- Pressione **Y** para amarelo.
- Pressione **B** para azul.
- Você pode até deixar a tela totalmente preta (com o comando `T`) e desenhar sobre ela.

O que torna ZoomIt ainda mais incrível é a capacidade de **zoom vivo**, permitindo interagir com a ampliação enquanto você está zoomando:

#### Zoom Vivo

Amplie, mova e clique na tela durante o processo para uma experiência muito mais dinâmica.

---

### Process Explorer

Muitos consideram o **Process Explorer** como um "Task Manager de primeira linha" ou até mesmo como super Task Manager. Ele fornece informações detalhadas sobre os processos em execução no seu sistema.

#### Principais Funcionalidades

- Mostrar relatórios hierárquicos de processos (pai e filho).
- Exibir o comando (`cmdline`) e o caminho (\`Path\`) do processo.
- Listar as proteções do processo, incluindo a verificação da Proteção de Fluxo de Execução (Control Flow Guard - CFG).

#### Como Usar

Quando você abre o **Process Explorer**, visualiza uma árvore de processos que mostra os relacionamentos parent-child.

Para identificar qual processo está usando um arquivo específico (como ZoomIt.exe), você pode usar a função "Find" e procurar por `ZoomIt`:

#### Busca do Arquivo Handler

- Vá para **Encontrar** > **Manipulador de Arquivos DLL...**
- Digite o nome do arquivo que deseja encontrar (ex: ZoomIt).
- O resultado mostrará qual processo tem abertura ou manipulação sobre esse arquivo.

No menu "Mais", você pode ver as abas "**Handles**" e "**DLLs**", mostrando os recursos de sistema abertos pelo processo e os módulos carregados, respectivamente.

---

### Process Monitor

O **Process Monitor (ProcMon)** é uma ferramenta extremamente poderosa para monitoringamento do sistema. É considerada por muitos como a número 1 em troubleshooting no Windows.

#### Principais Funcionalidades

- Captura eventos de arquivo, registro e rede.
- Mostra a estrutura completa da pilha de threads (thread stacks).
- Possui filtragem flexível para capturar apenas os eventos relevantes.
- Capta milhões de eventos durante sua execução.

#### Exemplo Prático

Suponha que você encontre o seguinte erro ao copiar arquivos do Sysinternals Suite:

> *"Ação não pode ser concluída porque a pasta ou arquivo está aberta em outro programa Feche a pasta ou o arquivo e tente novamente."*

Você pode usar o **Process Monitor** para descobrir por que isso está acontecendo:

1. Abra o ProcMon.
2. Vá para  Filter > path > begin with > c:\pasta > include
3. Clique no botão de adicionar (**+**) e selecione a pasta onde você deseja monitorar (ex: `C:\Tools`).
4. Você verá uma lista detalhada dos erros relacionados àquele diretório.

Neste exemplo, o erro era que eu estava tentando copiar ZoomIt.exe, mas ele já estava aberto pelo próprio processo ZoomIt.exe:

#### Resolução do Exemplo Prático

- Você identificou que o ZoomIt.exe no diretório `C:\Tools` estava sendo executado.
- A solução foi simplesmente fechar a janela do ZoomIt.exe. O erro desapareceu e a cópia pôde prosseguir.

---

### Autoruns

**Autoruns** é um dos programas mais populares da Sysinternals porque oferece uma visão abrangente de tudo que está configurado para iniciar automaticamente no seu sistema.

#### Principais Funcionalidades

- Lista centenas de locais possíveis onde software pode ser configurado para iniciar automaticamente.
- Agrupa as informações em categorias (ex: Explorer, Logons, Startup, etc).
- Mostra detalhes como nome do executável, caminho, tamanho e data/hora da última modificação.

#### Como Usar

Você pode usar a opção "**Opções**" para filtrar entradas específicas. Por exemplo, você pode esconder todas as entradas de Microsoft ou de Windows:

#### Opções de Autoruns

- Vá para **Edit** > **Options...**
- Na aba "General", desmarque a opção "**Microsoft Entries**" ou "**Windows Entries**".

Se você vir algo desconhecido, pode pesquisar online ou enviar o arquivo para análise no VirusTotal (um serviço gratuito de 67 fornecedoras de software antivírus):

#### Verificação com VirusTotal

- Clique com o botão direito na entrada específica e selecione "**Submit File...**".

---

### Proctum

Este é um nome curioso para a ferramenta: **Proctum**, que originalmente era chamada de **ProcDump**. Vamos esclarecer:

#### ProcDump (Proctum)

A ferramenta correta é o **ProcDump**, e não há relação com "procto" ou procedimentos médicos.

O ProcDump é ideal para capturar dumps de memória (**crash dump**) quando um processo está falhando ou exibindo comportamento anômalo. Ele permite definir triggers, como:

- Capturar o dump quando a CPU estiver acima de X%.
- Capturar o dump quando uma exceção ocorrer no processo.

#### Exemplo Prático

Para monitorar um processo chamado `CPUstress.exe` e capturar seu dump sempre que ele usar mais de 20% da CPU por mais de 10 segundos, você usaria este comando (no prompt de comando):

```cmd
ProcDump -c -ma20 -e -x C:\Temp\dump.cpu "C:\Path\To\CPUstress.exe"
```

Isso permitiria que você analisasse o dump posteriormente para entender a causa da sobrecarga.

---

### PS Tools

**PS Tools** é um conjunto de utilitários (mais de 15 atualmente) que começaram com **PsList**, inicialmente criado para mostrar processos via linha de comando. Os nomes seguem o padrão "Ps" porque são executáveis de uma única arquivo e podem ser usados tanto local quanto remotamente.

#### Principais Ferramentas da PS Tools

- `PsInfo`: Mostra informações detalhadas do sistema.
- `PsList`: Lista processos (popularíssimo).
- `PsKill`: Finaliza processos remotos ou locais.
- `PsExec`: Executa programas remotamente interativamente.

---

### PSExec

O **PSExec** é a ferramenta mais usada da coleção PS Tools, mas não porque seja uma ferramenta única. A grandeza vem do seu propósito: executar qualquer programa local ou remoto no Windows de forma totalmente remota e interativa.

#### Como Usar

Para executar `cmd.exe` remotamente em um computador chamado "mr-game", você faria o seguinte (no prompt de comando, executando como administrador):

```cmd
PsExec \\mr-game -u username -p password cmd.exe
```

Isso iniciará uma sessão interativa com o prompt do sistema remoto `mr-game`.

---

### Sysmon

**Sysmon (System Monitor)** foi criado em 2014 para monitorar eventos de segurança críticos no Windows. Ele rastreia processos, conexões de rede e muito mais, registrando esses eventos no log do Windows Event Viewer.

#### Principais Funcionalidades

- Captura eventos de sistema relevantes (processos criados/terminados, conexões de rede) com detalhes.
- Rastreia atividades suspeitas como tentativas de acesso ao registro ou pasta raiz (`C:\Windows`).
- Possui filtragem avançada para ignorar ruídos indesejados e focar apenas em ocorrências relevantes.

#### Exemplo Prático

Quando você executa o Sysmon, ele já coleta eventos importantes. No Event Viewer, você verá entradas como:
- **Evento de Criação do Processo:** Mostra detalhes sobre cada processo que é iniciado (nome, caminho, usuário, ID pai).
- **Evento de Encerramento do Processo:** Registra quando um processo termina.

---

### Linux

Embora o Sysinternals seja focado no Windows, existem algumas ferramentas para Linux. No entanto, devido à evolução rápida do kernel do Linux, essas ferramentas se tornaram desatualizadas e foram preteridas há alguns anos.

Recentemente, lançamos três novos utilitários para o Linux:
1. **ProcDump:** Captura dumps de processos.
2. **Process Monitor (para Linux):** Monitorea chamadas do sistema em linha de comando (`strace`-like).
3. **Sysmon for Linux:** Oferece esquema de log compatível com Sysmon do Windows, facilitando a análise unificada.

---

### Conclusão

Espero que esta visão geral sobre as ferramentas do Sysinternals tenha sido útil e interessante! Elas são verdadeiras joias para qualquer administrador de sistemas ou técnico no Brasil. Recomendo fortemente que você explore cada uma delas em seus próprios ambientes.

#### Próximos Passos

- Baixe o **Sysinternals Suite** completo do site oficial - [Sysinternals - Microsoft Learn](https://learn.microsoft.com/pt-br/sysinternals/)
- Use as ferramentas descritas nesta apresentação para entender melhor seu sistema Windows.
- Procure os vídeos da [TechEd](https://www.youtube.com/results?search_query=teched+sysinternals) e [Ignite](https://www.youtube.com/results?search_query=Ignite+sysinternals) onde casos reais são resolvidos com estas ferramentas.

#### Recursos Adicionais

- **Livro Oficial:** [Troubleshooting with the Windows Sysinternals Tools - Sysinternals - Microsoft Learn](https://learn.microsoft.com/en-us/sysinternals/resources/troubleshooting-book).
- **Artigo Online:** [Sysinternals - Microsoft Learn](https://learn.microsoft.com/pt-br/sysinternals/) Visite o site do Sysinternals para mais informações e tutoriais.
- [Sysinternals Overview - Microsoft, tools, utilities, demos - YouTube](https://www.youtube.com/watch?v=6RqFPrCcWfY)
- [Sysinternals - YouTube](https://www.youtube.com/playlist?list=PLLhSArDiaW6IgzMYEMaEf_BF2yQN40fIm)
