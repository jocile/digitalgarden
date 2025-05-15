---
{"dg-publish":true,"permalink":"/tecnico/assistente-de-ti/linux/","title":"Linux","noteIcon":2,"updated":"2025-05-15T09:48:32.628-03:00"}
---


# Conhecendo o Linux

O Linux é um dos sistema operacionais mais populares e é amplamente utilizado pelo segmento de servidores e desenvolvedores de software.

## O Kernel do Linux

![Image](https://user-images.githubusercontent.com/45495068/184768677-1b21862e-ac4a-4b9a-879c-4bf16d4a6a9d.png)

Inicialmente a comunidade internacional de desenvolvedores criou, em 1985 o [projeto GNU](https://www.gnu.org/gnu/gnu-history.pt-br.html), para e disponibilizar software gratuitamente, podendo ser usado por qualquer empresa com as seguintes liberdades:

- de copiá-lo e dá-lo a seus amigos e colegas;
- de modificar o programa como você desejar, por ter acesso total ao código-fonte;
- de distribuir versões melhoradas e, portanto, ajudar a construir a comunidade.

Então depois de ter desenvolvidos os principais componentes do Sistema Operacional, foi anexado o kernel do Linux - que é quem interage com o hardware, que havia começado a ser desenvolvido por Linus Torvalds, em 1991, quando estava na faculdade em Helsinki, na Finlândia, inspirado no Unix, outro sistema operacional criado nos anos 70.

Apesar de ser gratuito o Kernel do Linux é mantido por uma [fundação de empresas - Linux Fundation](https://linuxfoundation.org/our-members-are-our-superpower-2/).

## Vantagens do Linux

![Image](https://user-images.githubusercontent.com/45495068/184758726-b712e4f5-15a6-47ea-8f18-d230da7e3766.png)

Dentre as principais vantagens do Linux podemos destacar:

- Gratuito
- Instalação simples
- Comunidade de desenvolvedores ativa
- Liberdade de customização
- Segurança

## Interação com o usuário

Existem softwares para interagir com Kernel, que podem ser feitas de duas maneiras:

### Ambiente gráfico

Existem uma grande variedade de interfaces gráficas para o usuário (GUI) do Linux. Dentre elas destacam-se:

- KDE - (K Desktop Environment)
- GNOME (GNU Network Object Model Environment)
- Unity - interface padrão do Ubuntu
- Cinnamon - derivada (Fork) do Gnome
- Mate - possui grande versalidade de configurações da interface gráfica sendo uma continuação do Gnome2;
- XFCE - indicada para hardware com poucos recursos ou de baixa configuração;
- LXDE - foi desenvolvido para funcionar bem em computadores lentos e de baixa performance e para sistemas simplificados como netbooks e outros computadores pequenos (Raspberry Pi, Orange Pi e etc).

### Linha de comando

Em ambiente de servidores podemos interagir remotamente através de comandos, que podem ser organizados em forma de lista, chamada de script, para serem executados em lote, automatizando seu uso.\
Através do terminal de comandos podemos executar programas de uma forma mais direta e refinada, utilizando parâmetros de execução.

## Distribuições do Linux

Uma distribuição é um pacote que consiste no Kernel do Linux, um ambiente gráfico, e mais uma coleção de aplicativos mantidos por uma comunidade de desenvolvedores ou uma empresa. Seu objetivo é otimizar a utilização para um determinado tipo de uso ou grupo de usuários.

Exemplos de distribuições mais populares:

- Debian - focado em usuário final e facilidade de uso
- Ubuntu - baseado no Debian
- Red Hat - focado em servidores
- Fedora - versão gratuíta baseado no Red Hat
- Suse - focado em sistema corporativo

## Sistemas embarcados Linux

Sistemas embarcados são uma combinação de hardware e software projetados para cumprir uma função específica em algum dispositivo.

Suas maiores aplicações são:

- Android - para dispositivos móveis;
- Veículos - proporcionando menus de navegação multimídia;
- Smart TVs - navegação multimídia e aplicativos;
- Smart watches - navegação em relógio;
- Aplicações médicas;
- Aplicações militares;
- Microcomputadores como o Raspberry Pi.

## Diferença entre desktop e servidor

O modelo cliente servidor é uma estrutura de aplicação que distribui tarefas e cargas de trabalho entre os fornecedores de serviços e recursos de comunicação, que são designados servidores, e os requerentes destes serviços, chamados de clientes.  

Máquinas virtuais em grandes servidores podem executar esses servidores na nuvem, para atender os clientes em desktops de uso pessoal.  

Para cada tipo de uso existe um tipo de versão de sistema operacional, servidores podem executar banco de dados, enquanto que desktops podem executar pacotes de aplicativos gráficos e de escritório.

## Instalação do Linux

![Image](https://user-images.githubusercontent.com/45495068/184766973-b6a375e8-da79-4af9-ae2f-8caff191286b.png)

Figura: Ubuntu Studio em ubuntu.com/desktop/flavours

Existem diversos tipos de versões do Linux para as mais diversas finalidades e tipos de usuários e de hardware. Dentre as mais populares destacam-se as versões do Ubuntu no seu [site de downloads](https://ubuntu.com/download).

Dentre as versões disponíveis podemos encontrar:

- Ubuntu server - para servidores;
- Ubuntu cloud - para servidores em ambientes virtuais;
- Ubuntu flavours - versão desktop para diversos tipos de usuários, tipos de hardware e aplicações específicas;
- Ubuntu for IoT - para dispositivos e para operar na nuvem;
- Alternative - versões alternativas.

### Ambiente virtual VirtualBox

![Image](https://user-images.githubusercontent.com/45495068/184765998-04438bde-a369-41fd-bf6b-17bc72171b3e.png)

Figura: Ubuntu desktop no VirtualBox.

O VirtualBox é um software opensource que simula um computador onde podem ser instalados os sistemas operacionais em um ambiente virtual, com podemos usar mais de um sistema operacional simultaneamente, e assim testar programas de diversos sistemas sem afetar o sistema hospedeiro.

**Atividade: Instalação da Imagem Linux Ubuntu em Máquina Virtual com VirtualBox**

**Objetivo:** Instalar e configurar uma máquina virtual Windows 10 com o software VirtualBox, criando um ambiente para testes e treinamentos de sistemas operacionais.

### Passo a Passo

#### **Passo 1: Baixar e Instalar o Software VirtualBox**

- Acesse [www.virtualbox.org](http://www.virtualbox.org) e clique em "Downloads".
- Selecione a última versão estável para Windows.
- Clique no botão de download da versão adequada ao seu sistema operacional (32 ou 64 bits).
- Execute o arquivo baixado, clicando duas vezes nele e seguindo as instruções do instalador para instalar o VirtualBox.

#### **Passo 2: Baixar a Imagem do Linux Ubuntu**

- Acesse [www.ubuntu.com](http://www.ubuntu.com) e clique em "Downloads".
- Selecione o Ubuntu que você deseja usar para sua máquina virtual.
- Clique no botão de download da imagem adequada.

#### **Passo 3: Criar uma Máquina Virtual no VirtualBox**

1. Abra a interface gráfica do VirtualBox.
2. Clique em "Nova" (ou New, em inglês) na janela principal.
3. Selecione Ubuntu como sistema operacional e clique em Próximo.
4. Escolha uma memória RAM razoável para o ambiente virtual e defina as configurações da máquina.

#### **Passo 4: Adicionar a Imagem ao VirtualBox**

1. Irá precisar fazer isso manualmente, caso não encontre na aba "Distribuições" do software:
2. Para adicionar uma distribuição existente:
    - Clique em 'Arquivos' no topo da janela VirtualBox.
    - Vá para a pasta de configuração (por padrão é na sua área de trabalho, e você pode mudar isso).
3. Navegue até o local onde salvou o arquivo .iso (da imagem) do Ubuntu.

#### **Passo 5: Instalar a Imagem no VirtualBox**

- Com as configurações adequadas feitas anteriormente, selecione a máquina virtual criada e clique em "Abrir" ou simplesmente arrastem ela para o canto superior esquerdo da janela.
- Clique em "Distribuições", logo abaixo de onde escreveu os nomes das máquinas virtuais. 
- Vá até a pasta que você configurou anteriormente e localize seu arquivo .ova do Ubuntu.
- Após encontrar, clique nele para instalar.

#### **Passo 6: Executar o Ambiente Virtual**

1. Clique em "Iniciar" na máquina virtual criada com as configurações de inicialização adequadas (se precisar ajustar alguma coisa como memória ou CPU).
2. O linux tem o recurso "live" que executa sem necessitar de instalação, permitindo testar o sistema.
3. S desejar instalar, selecione a opção de instalação na tela inicial, isso permitirá tornar as alterações permanentes na máquina virtual.
4. Aguarde a instalação da imagem do Ubuntu terminar.
5. Se necessário, faça login manualmente no sistema após o término da instalação.

#### **Passo 7: Teste e Configure seu Ambiente**

- Ao iniciar o ambiente virtual, você verá uma janela de Login do Linux Ubuntu.
- O usuário padrão é "ubuntu" e a senha também será "ubuntu", mas lembre-se que essas informações podem mudar dependendo da configuração específica do sistema instalado.

>[!info] **Observações:**
>- O tempo para completar essa atividade pode variar com a velocidade do seu computador e a conexão à internet.
>- Alguns passos podem ser ajustados dependendo das configurações específicas que você deseja usar.

---

## Referências

- [Linux Fundation](https://linuxfoundation.org/)
- [Interfaces graficas do Linux. Certificação Linux](https://www.certificacaolinux.com.br/interfaces-graficas-do-linux/)
- [Ubuntu Linux. Certificação Linux](https://www.certificacaolinux.com.br/ubuntu-linux/)
- [História do projeto GNU](https://www.gnu.org/gnu/gnu-history.pt-br.html)
- [Introducao ao sistema operacional Linux. Bootcamp Linux Experience. Digital Inovation One](https://web.dio.me/track/5185f031-7dc5-466e-bffb-2db01bf7abb3)
- [Virtualbox porque utilizar. E-tinet](https://e-tinet.com/linux/virtualbox-porque-utilizar/)
- [Slide de Trabalho sobre Linux](https://pt.slideshare.net/davidpereira/trabalho-linux)
- [Exercícios sobre Linux](https://github.com/users/jocile/projects/10/views/1)
