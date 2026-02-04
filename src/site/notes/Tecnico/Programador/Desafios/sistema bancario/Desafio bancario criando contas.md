---
{"dg-publish":true,"permalink":"/tecnico/programador/desafios/sistema-bancario/desafio-bancario-criando-contas/","metatags":{"description":"criação de contas bancárias utilizando funções e um menu interativo"},"noteIcon":2,"updated":"2026-02-04T07:38:46.943-03:00"}
---

#Lógica #Python #desafio 

# Criando contas bancárias

Com base nos fundamentos de organização, **modularização** e controle de fluxo apresentados nas fontes, aqui está uma proposta de atividade prática voltada para a **criação de contas bancárias** utilizando **funções** e um **menu interativo**.

Esta atividade exercita a **decomposição de problemas** em sub-rotinas específicas e o gerenciamento de diferentes tipos de dados.

---

## Fase 1 Sistema de abertura de contas

### Atividade Prática: Sistema de Abertura de Contas Bancárias

**Objetivo:** Desenvolver um algoritmo que permita cadastrar três tipos de contas (Corrente, Poupança e Pessoa Jurídica) através de um menu, utilizando funções para isolar a lógica de criação de cada uma.

#### 1. Definição das Funções (Responsabilidades Isoladas)

Cada tipo de conta possui requisitos diferentes. O aluno deve criar funções específicas para capturar esses dados e retornar um resumo:

- **`criar_corrente(nome, saldo_inicial)`**: Recebe o nome e o valor de abertura, retornando uma confirmação.
- **`criar_poupanca(nome, saldo_inicial)`**: Além dos dados básicos, pode incluir a definição de uma data de aniversário da conta.
- **`criar_pj(nome_fantasia, cnpj, saldo_inicial)`**: Exige um parâmetro extra (**CNPJ**), demonstrando como funções podem lidar com diferentes quantidades de informações.



## Fase 2 Criando registros em dicionários

Para integrar **funções** com **dicionários** na organização de dados bancários, você deve utilizar o dicionário como a unidade de armazenamento de informações e as funções como os motores de processamento e criação desses dados. Abaixo, apresento o passo a passo para essa integração:

1. **Estruture a conta como um Dicionário:** Utilize a estrutura de **chave e valor** para representar cada conta bancária individual. Chaves descritivas como "titular", "tipo_conta" e "saldo" devem ser usadas para rotular os dados, facilitando a identificação do que cada valor representa.
2. **Crie uma Função de Cadastro:** Utilize a palavra reservada **`def`** para criar uma função que receba os dados do cliente como **parâmetros**. Dentro desta função, a lógica deve construir um dicionário e utilizá-lo como o valor de **`return`** para devolver a conta estruturada ao programa principal.
3. **Gerencie uma Lista de Contas (Estrutura Composta):** Para organizar múltiplos clientes, armazene cada dicionário de conta dentro de uma **lista**. Você pode usar a função **`append`** para inserir novos dicionários de contas nessa lista conforme elas forem criadas.
4. **Desenvolva Funções de Processamento:** Crie funções que recebam a lista de contas ou um dicionário específico como argumento para realizar operações financeiras. Por exemplo, uma função pode percorrer a lista usando um laço **`for`**, acessar a chave "saldo" de cada dicionário e calcular o montante total sob gestão do banco.
5. **Isole as Responsabilidades:** Seguindo o **paradigma funcional**, cada tarefa (abrir conta, depositar, calcular juros) deve ser uma função isolada. Isso garante que, se uma regra bancária mudar, você precise alterar o código apenas dentro da função correspondente, facilitando a **manutenção** e o **reuso** do software.



## Fase 3 Listando os registros

Para listar e visualizar as contas cadastradas de forma organizada, a melhor prática é utilizar uma **estrutura de repetição (laço `for`)** para percorrer os dados e a função **`print()`** para exibir os valores de cada campo.

Considerando que você está utilizando uma **estrutura de dados composta** (uma lista que armazena vários dicionários de contas), o procedimento técnico é o seguinte:

1. **Utilize um laço `for`:** Ele permite que o programa passe por cada "caixa" (dicionário) dentro da sua lista de contas, uma por uma.
2. **Acesse os valores pelas chaves:** Dentro do laço, você deve referenciar as **chaves** específicas do dicionário (como `"titular"`, `"saldo"` ou `"tipo_conta"`) entre colchetes para capturar apenas a informação desejada.
3. **Formate a visualização com `f-strings`:** Para que a lista não seja apenas um amontoado de dados brutos, utilize a formatação `f"Texto {variável}"`. Isso permite intercalar descrições com os dados das contas, tornando a leitura intuitiva para o usuário.



## Fase 4 Removendo o registro

Sim, **é possível criar uma função que remova contas de um dicionário**. O processo de manipulação de dados é fundamentado no uso de **funções** (declaradas com a palavra-chave `def`) para isolar responsabilidades e automatizar tarefas.

Embora os exemplos detalhados de remoção nas fontes (como os métodos `remove` e `pop`) sejam demonstrados especificamente para **listas**, a lógica de programação apresentada permite a criação de funções customizadas para gerenciar qualquer estrutura de dados.

Para integrar essa funcionalidade ao sistema de dados bancários discutido anteriormente, você deve seguir estes princípios:

- **Paradigma Funcional:** Você pode definir uma função específica, por exemplo `remover_conta`, que receba o dicionário (ou a lista de dicionários) e o identificador da conta (como o nome do titular) como **parâmetros**.
- **Modularização:** Ao isolar a exclusão em uma função, você facilita a **manutenção do código** e evita erros semânticos no fluxo principal do programa.
- **Uso de Estruturas de Controle:** Dentro da função, você pode usar uma **estrutura de decisão** (`if`) para verificar se a conta existe antes de tentar removê-la, evitando que o programa gere erros de execução.
- **Estruturas Compostas:** Como vimos que dados bancários podem ser organizados em uma **lista de dicionários**, a função de remoção percorreria essa lista (usando um laço `for`), identificaria o dicionário correspondente e utilizaria comandos de remoção para excluí-lo da coleção.

Essa prática segue a recomendação das fontes de **decompor problemas complexos** em partes menores e reutilizáveis, garantindo que o software seja robusto e fácil de evoluir.



## Referências

- [Desafio Sistema Bancário - Google Colab](https://colab.research.google.com/drive/1DFPg5VakbWUVJ1RYquyTBBKTE9MKWSJX?usp=sharing)
- [[Aulas de Logica\|Aulas de Logica]]
