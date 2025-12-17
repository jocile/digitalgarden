---
{"dg-publish":true,"permalink":"/tecnico/assistente-de-ti/instalando-o-windows/","title":"Instalação do Windows","metatags":{"description":"Como instalar o Windows em uma máquina virtual."},"noteIcon":"default","updated":"2025-11-25T14:04:18.146-03:00"}
---

## Instalação do Windows

Este artigo explica sobre como instalar o Windows 11 usando uma imagem ISO em uma máquina virtual. Vamos usar o VirtualBox como exemplo de software de virtualização.

### Atividade: Instalação do Windows 11 em uma Máquina Virtual

#### Objetivo

Como criar e configurar uma máquina virtual e instalar o Windows 11 usando uma imagem ISO.

#### Materiais Necessários

- Computador com acesso à internet
- Software VirtualBox instalado
- Imagem ISO do Windows 11

#### Passo a Passo

1. **Baixar e Instalar o VirtualBox:**    
    - Acesse o site oficial do VirtualBox e baixe a versão mais recente.
    - Siga as instruções de instalação para instalar o VirtualBox no seu computador.
2. **Baixar a Imagem ISO do Windows 11:**    
    - Acesse o site oficial da Microsoft e baixe a imagem ISO do Windows 11.
3. **Criar uma Nova Máquina Virtual:**    
    - Abra o VirtualBox e clique em “Novo” para criar uma nova máquina virtual.
    - Dê um nome à máquina virtual (por exemplo, “Windows 11”).
    - Selecione o tipo de sistema operacional como “Microsoft Windows” e a versão como “Windows 11 (64-bit)”.
4. **Configurar a Máquina Virtual:**    
    - **Memória:** Alocar pelo menos 4 GB de RAM (4096 MB) para a máquina virtual.
    - **Disco Rígido:** Crie um novo disco rígido virtual (VDI) e aloque pelo menos 64 GB de espaço.
5. **Selecionar a Imagem ISO:**    
    - Com a máquina virtual selecionada, clique em “Configurações” e vá para a aba “Armazenamento”.
    - No controlador IDE, clique no ícone de disco e selecione “Escolher um disco” para adicionar a imagem ISO do Windows 11.
6. **Iniciar a Máquina Virtual:**    
    - Clique em “Iniciar” para ligar a máquina virtual.
    - A instalação do Windows 11 começará automaticamente a partir da imagem ISO.
7. **Instalar o Windows 11:**    
    - Siga as instruções na tela para instalar o Windows 11.
    - Selecione o idioma, formato de hora e moeda, e layout do teclado.
    - Clique em “Instalar agora” e insira a chave do produto, se necessário.
    - Escolha a opção “Custom: Install Windows only (advanced)”.
    - Selecione o disco onde o Windows 11 será instalado e clique em “Next”.
8. **Configurar o Windows 11:**    
    - Após a instalação, siga as instruções para configurar o Windows 11 (criar uma conta, definir preferências, etc.).
9. **Instalar Adições de Convidado (Guest Additions):**    
    - Após a instalação do Windows 11, vá para o menu “Dispositivos” no VirtualBox e selecione “Inserir imagem de CD das Adições de Convidado”.
    - Siga as instruções para instalar as Adições de Convidado, que melhoram o desempenho e a integração da máquina virtual.
10. **Finalizar e Testar:**    
    - Reinicie a máquina virtual e verifique se o Windows 11 está funcionando corretamente.
    - Explore as funcionalidades básicas do Windows 11 com os alunos.

#### Dicas Adicionais

- Certifique-se de que o computador host tenha recursos suficientes para suportar a máquina virtual.
- Incentive os alunos a fazer perguntas e explorar diferentes configurações no VirtualBox.

## Referências

- [Como obter o Windows 11 para o seu PC compatível | Microsoft](https://www.microsoft.com/pt-br/windows/get-windows-11)
- [Windows - Centro de Download da Microsoft](https://www.microsoft.com/pt-br/download/windows)
- [Pesquisar resultados para 'windows' - Suporte da Microsoft](https://support.microsoft.com/search/results?query=windows&isEnrichedQuery=false)
