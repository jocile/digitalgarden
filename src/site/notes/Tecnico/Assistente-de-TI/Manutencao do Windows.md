---
{"dg-publish":true,"permalink":"/tecnico/assistente-de-ti/manutencao-do-windows/","metatags":{"description":"como resolver problemas do Windows e utilizar ferramentas técnicas"},"noteIcon":2,"updated":"2025-11-24T08:48:22.599-03:00"}
---

#aula #Windows

Para resolver problemas no sistema operacional Windows, podem ser efetuados diversos procedimentos e utilizadas várias ferramentas nativas. As principais abordagens incluem: 

## 1. Ferramentas Integradas de Solução de Problemas

O Windows possui solucionadores de problemas automáticos para diversas categorias de falhas: 

- **Acesso:** Vá em **Iniciar** > **Configurações** > **Sistema** (ou **Atualização e Segurança**, dependendo da versão do Windows) > **Solução de problemas** > **Outros solucionadores de problemas**.
- **Tipos de Problemas:** Existem ferramentas específicas para problemas de **Windows Update**, **conexão com a internet**, **áudio**, **impressora**, **aplicativos da Microsoft Store** e outros. 

## 2. Opções de Recuperação do Windows

Acessíveis a partir do Ambiente de Recuperação do Windows (Windows RE), geralmente reiniciando o computador a partir da tela de login enquanto mantém a tecla **Shift** pressionada: 

- **Restauração do Sistema:** Permite reverter o sistema operacional para um ponto no tempo anterior ao início do problema, sem afetar arquivos pessoais.
- **Reparo de Inicialização:** Tenta corrigir automaticamente problemas que impedem o Windows de carregar corretamente.
- **Restaurar o PC:** Oferece a opção de reinstalar o Windows, mantendo (ou removendo) seus arquivos pessoais.
- **Modo de Segurança:** Inicia o Windows com um conjunto mínimo de drivers e serviços, útil para diagnosticar problemas causados por softwares ou drivers de terceiros. 

>[!tip] Para entrar no modo de recuperação :
> Na tela login Clique em Reiniciar segurando a tecla `Shift`, depois em **solução de problemas**, **opções avançadas** e em **Prompt de Comando**.
> [Ambiente de Recuperação do Windows - Suporte da Microsoft](https://support.microsoft.com/pt-br/windows/ambiente-de-recupera%C3%A7%C3%A3o-do-windows-0eb14733-6301-41cb-8d26-06a12b42770b)

## 3. Comandos via Prompt de Comando (CMD) ou PowerShell 

A execução desses comandos como administrador podem corrigir problemas de arquivos e imagem do sistema: 

- **SFC (System File Checker):** O comando `sfc /scannow` verifica a integridade dos arquivos protegidos do sistema Windows e substitui arquivos corrompidos por cópias corretas.
- **DISM (Deployment Image Servicing and Management):** Ferramenta mais avançada para reparar a imagem do sistema operacional. Comandos comuns incluem `DISM /Online /Cleanup-Image /RestoreHealth` para corrigir corrupções usando arquivos confiáveis do Windows Update.
- **CHKDSK (Check Disk):** O comando `chkdsk` (seguido da letra da unidade e parâmetros, por exemplo, `chkdsk C: /f /r`) verifica e repara erros no sistema de arquivos do disco rígido. 

>[!info] Digite os seguintes comandos no Power Shell (prompt de comando) como administrador, ou caso o Windows tenha problemas para iniciar, use o modo de recuperação.

>[!important] Depois de cada procedimento reinicie o sistema!

### Manutenção de arquivos do Windows

- Verificar se a imagem do Windows está corrompida antes de iniciar um reparo:

```shell
dism /online /cleanup-image /CheckHealth
```

Ou o seguinte:

```shell
dism /online /cleanup-image /SCANHEALTH
```

- Baixar e substituir por originais, todos arquivos do sistema que estiverem corrompidos:

```shell
DISM /Online /Cleanup-image /Restorehealth
```

- Verifica arquivos do sistema que estiverem corrompidos e substitui pelos que estão armazenados em cache:

```shell
sfc /scannow
```

- Verifica a unidade de armazenamento C em busca de erros e setores defeituosos para reparar.

```shell
chkdsk c: /f /r
```

### Resolvendo problemas de inicialização do Windows

- Verifica a limitação de quantidade de memória disponível quando o computador é inicializado, caso o identificador não for válido significa que a limitação foi desativada:

```shell
bcdedit /deletevalue {default} truncatememory
```

- Diagnosticar e resolver problemas na inicialização:

```shell
bootrec /scanos
```

- Reconstruir a base de dados BCD, que tem informações de inicialização

```shell
bootrec /rebuildbcd
```

- Repara o registro mestre de inicialização MBR:

```shell
bootrec /fixmbr
```

- Recria o setor de inicialização do sistema:

```shell
bootrec /fixboot
```

>[!info] Caso nenhum desses comandos não resolva o problema, procure a opção **restaurar o PC** na solução de problemas do modo de recuperação, mas não esqueça de fazer o [backup dos arquivos](https://www.youtube.com/watch?v=B83Xf-VCitk), pois a restauração vai reinstalar o Windows!

### Redefinir a senha: 

- Acesse o prompt no modo de recuperação:

```shell
cd windows\system32
ren utilman.exe utilman_backup.exe
ren cmd.exe utilman.exe
```

- Feche o prompt e clique em continuar para reiniciar, quando iniciar a tela de login, clique no ícone ao lado do botão de reiniciar que vai ativar novamente o prompt de comando, entre com o comando para abrir o gerenciador de contas:

```shell
control userpasswords2
```

>[!warning] Não clique em remover, somente em redefinir!

- Acesse novamente o prompt no modo de segurança e restaure os arquivos originais:

```shell
cd windows\system32
ren utilman.exe cmd.exe
ren utilman_backup.exe utilman.exe 
```

### Manutenção de rede

- Reseta as conexões de rede para resolver problemas de WiFi:

```shell
NETSH WINSOCK RESET
```

- Reseta o cache de DNS:

```shell
IPCONFIC /FLUSHDNS
```

- Revela todas as redes salvas:

```shell
netsh wlan show profiles
```

- Revela a senha do WiFi:

```shell
netsh wlan show profile name="NOME_DA_REDE" key=clear
```

## 4. Manutenção Preventiva e Outras Ações

- **Atualizações:** Manter o Windows e os drivers de dispositivo atualizados é fundamental para a segurança e estabilidade.
- **Reinicialização Simples:** Às vezes, reiniciar o computador e abrir apenas os aplicativos necessários resolve problemas temporários de desempenho.
- **Limpeza de Disco:** Usar a ferramenta Limpeza de Disco (`cleanmgr`) para remover arquivos temporários e desnecessários
- **Debloat:** Remover todos os programas desnecessários e parar a execução de serviços automáticos que não estão sendo utilizados ([[Tecnico/Assistente-de-TI/Otimizacao do Windows\|Otimizacao do Windows]]).

### Ferramentas de manutenção do Windows

| Nome                                                                                   | Descrição                                                                                                                                          |
| -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Winscript](https://github.com/flick9000/winscript)                                    | Cria scripts de automação para debloat, privacidade, performance e instalação de aplicativos.                                                      |
| [Sysinternal](https://learn.microsoft.com/pt-br/sysinternals/)                         | pacote de utilitários avançados do sistema e informações técnicas para  gerenciar, solucionar problemas e diagnosticar seus sistemas e aplicativos |
| [Revo Uninstaller](https://www.revouninstaller.com/br/revo-uninstaller-free-download/) | Remova programas indesejados e entradas inválidas do Registro facilmente                                                                           |
| [UniGetUI](https://marticliment.com/unigetui/)                                         | Gerenciador de pacotes e versões para a instalação e atualização de aplicativos                                                                    |
| [Wise Duplicate Finder](https://www.wisecleaner.com/wise-duplicate-finder.html)        | Localiza arquivos duplicados por nome, tamanho e conteúdo para liberar espaço de armazenamento.                                                    |
| [Winaero Tweaker](https://winaerotweaker.com/)                                         | Ultilitário para personalização, debloat, e configuração avançada do Windows.                                                                      |
| [PC Manager](https://apps.microsoft.com/detail/9pm860492szd?hl=pt-BR&gl=BR)            | otimização, limpeza de armazenamento, gerenciamento de arquivos e proteção                                                                         |
| [DISM++](https://mestresdainformatica.com.br/dism-ferramenta-do-windows/)              | otimização para o Windows com limpeza de disco, gerenciamento de aplicativos e configurações do sistema                                            |
| [Malwarebytes](https://mestresdainformatica.com.br/baixar-malwarebytes-gratis-no-pc/)  | Antivírus e Malwares                                                                                                                               |

## Referências

- [Explorar as ferramentas de suporte e diagnóstico - Training \| Microsoft Learn](https://learn.microsoft.com/pt-br/training/modules/explore-support-diagnostic-tools/?source=recommendations)
- [[Tecnico/Assistente-de-TI/Otimizacao do Windows\|Otimizacao do Windows]]
- [FAÇA ISSO E RESOLVA TODOS OS ERROS E PROBLEMAS DO WINDOWS 11/10/8/7 e Melhore o Desempenho do PC - YouTube](https://www.youtube.com/watch?v=EROGi4w6C4w)
- [10 Comandos do WINDOWS que podem SALVAR o seu Computador! - YouTube](https://www.youtube.com/watch?v=CANUQvBzZ1I)
- [Como Recuperar SENHA do Windows 11/10 SEM Programas \[Guia Fácil e Seguro!\] - YouTube](https://www.youtube.com/watch?v=rS3lPDJNdiw)
- [Como Corrigir PROBLEMAS do Windows com a Ferramenta de Reparo Integrada - YouTube](https://www.youtube.com/watch?v=tya-K-s3M4U)
- [Comando DISM /Online /Cleanup-Image /ScanHealth ou /RestoreHealth não reconhecido Windows 10 - Microsoft Q&A](https://learn.microsoft.com/pt-br/answers/questions/3197198/comando-dism-online-cleanup-image-scanhealth-ou-re)
- [COMO CRIAR UM BACKUP DE SEGURANÇA DO WINDOWS (Passo a Passo) - YouTube](https://www.youtube.com/watch?v=tdE1Ffn2epY)
- [Opções de recuperação no Windows - Suporte da Microsoft](https://support.microsoft.com/pt-br/windows/op%C3%A7%C3%B5es-de-recupera%C3%A7%C3%A3o-no-windows-31ce2444-7de3-818c-d626-e3b5a3024da5)
