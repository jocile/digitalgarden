---
{"dg-publish":true,"permalink":"/tecnico/react/nvm-controle-de-versoes-do-node/","metatags":{"description":"gerenciador de versões do Node.js."},"noteIcon":3,"updated":"2025-09-26T15:38:40.263-03:00","dg-note-properties":{"topics":["Ferramentas","Gerenciadores de versões"]}}
---

#JavaScript #Webdesign #React #Nextjs

## NVM

O **NVM (Node Version Manager)** é uma ferramenta útil para gerenciar várias versões do **Node.js** em sua máquina. Com o NVM, você pode alternar facilmente entre diferentes versões do Node.js, dependendo dos requisitos de seus projetos. Aqui estão os passos básicos para usar o NVM:

1. **Instalação do NVM**:
    - Antes de instalar o NVM, é recomendado desinstalar qualquer versão do Node.js que esteja presente em sua máquina para evitar conflitos.
    - No terminal, execute um dos seguintes comandos para instalar o NVM:
        - Usando **curl**:

            ```bash
            curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
            ```

        - Ou usando **Wget**:

            ```bash
            wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
            ```

    - Isso clonará o repositório do NVM e o instalará no diretório `~/.nvm/`, onde você poderá gerenciar várias versões do Node.js.

2. **Listar versões instaladas**:
    - Para ver as versões do Node.js instaladas em sua máquina, execute:

        ```bash
        nvm ls
        ```

3. **Listar versões disponíveis para instalação**:
    - Este comando lista todas as versões disponíveis para download e instalação:

        ```bash
        nvm list available
        ```

4. **Instalar uma versão específica do Node.js**:
    - Escolha uma versão da lista e instale-a com o seguinte comando (substitua `<VERSAO_NODE_JS>` pela versão desejada):

        ```bash
        nvm install <VERSAO_NODE_JS>
        ```

    - Escolha uma versão LTS (long term suport) mais recente e instale-a com o seguinte comando:

        ```bash
        nvm install LTS
        ```

5. **Alternar entre versões do Node.js**:
    - Para usar uma versão específica do Node.js, execute o seguinte comando (substitua `vX.X.X` pela versão desejada):

        ```bash
        nvm use vX.X.X
        ```

    - Ou use a versão LTS mais recente:

        ```bash
        nvm use LTS
        ```

    - Para usar a versão mais recente, digite `node` no lugar da versão:

        ```bash
        nvm use node
        ```

Lembre-se de que o NVM funciona em **MacOS** e **Linux**. Se você estiver no **Windows**, existe um projeto chamado **nvm-windows** que oferece funcionalidades semelhantes e é recomendado pela **NPM**, **Google** e **Microsoft**¹²³. Espero que isso ajude você a gerenciar suas versões do Node.js de forma mais eficiente! 🚀

### Instalação

Se você está usando o **Windows**, o **NVM (Node Version Manager)** não é nativamente suportado, mas você pode usar uma alternativa chamada **nvm-windows**. Aqui estão os passos para instalar e usar o **nvm-windows**:

1. **Instalação do nvm-windows**:
    - Primeiro, acesse o [repositório do nvm-windows no GitHub](https://github.com/coreybutler/nvm-windows) e baixe o instalador executável (`.exe`).
    - Execute o instalador e siga as instruções para concluir a instalação.

2. **Verificar a instalação**:
    - Abra um novo terminal (Prompt de Comando ou PowerShell) e digite:

        ```bash
        nvm version
        ```

    - Isso deve exibir a versão instalada do **nvm-windows**.

3. **Instalar uma versão específica do Node.js**:
    - Para listar as versões disponíveis para instalação, execute:

        ```bash
        nvm list available
        ```

    - Escolha uma versão e instale-a com o seguinte comando (substitua `<VERSAO_NODE_JS>` pela versão desejada):

        ```bash
        nvm install <VERSAO_NODE_JS>
        ```

4. **Alternar entre versões do Node.js**:
    - Para usar uma versão específica do Node.js, execute o seguinte comando (substitua `vX.X.X` pela versão desejada):

        ```bash
        nvm use vX.X.X
        ```

    - Para usar a versão mais recente, digite:

        ```bash
        nvm use node
        ```

Lembre-se de que o **nvm-windows** é uma alternativa para o Windows e não oferece todas as funcionalidades do NVM original. No entanto, ele permite que você gerencie diferentes versões do Node.js em seu ambiente Windows. Boa sorte com o desenvolvimento em Node.js! 🚀

### Referências

Origem: conversa com o Bing, 03/03/2024\
(1) Instalando e gerenciando várias versões do Node.js com NVM. <https://www.treinaweb.com.br/blog/instalando-e-gerenciando-varias-versoes-do-node-js-com-nvm/>.\
(2) Instalando e gerenciando várias versões do Node.js com NVM. <https://bing.com/search?q=Como+usar+o+nvm+para+controle+de+vers%c3%b5es+do+node+js>.\
(3) Gerenciando múltiplas versões do Node.js com NVM - Revelo. <https://community.revelo.com.br/gerenciando-multiplas-versoes-do-node-js-com-nvm/>.\
(4) Gerenciar várias versões do Node.js com NVM - Hugo Andrade. <https://hugoandrade.com.br/gerenciar-varias-versoes-do-node-js-com-nvm/>.\
(5) Gerenciando multiplas versões do Node.js no macOS com o NVM. <https://www.maiconschmitz.com.br/blog/2020/07/06/gerenciando-multiplas-versoes-do-nodejs-no-macos-com-nvm/>.\
(6) undefined. <https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh>.
