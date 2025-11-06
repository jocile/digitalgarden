---
{"dg-publish":true,"permalink":"/tecnico/assistente-de-ti/calculando-a-fonte/","title":"Cálculos elétricos","metatags":{"description":"Como dimensionar equipamentos elétricos"},"tags":["eletricidade"],"noteIcon":1,"updated":"2025-11-05T15:00:10.033-03:00"}
---


Crie uma atividade que calcule uma fonte de computador para atender a seguinte demanda:

|           | Componente         | Consumo W |
| --------- | ------------------ | --------- |
| CPU       | Intel Core I5 4670 | 84        |
| Placa-mãe | ATX                | 70        |
| SSD       | 256GB              | 15        |
| RAM       | 8GB DDR5           | 3         |

## Atividade de Cálculo de Fonte de Computador

### Objetivo

Determinar a potência mínima necessária para uma fonte de alimentação (PSU) que atenda a uma configuração de computador específica.

### Componentes e Consumo

Considere os seguintes componentes e seus consumos estimados em watts (W):

| Componente         | Consumo W |
|--------------------|-----------|
| CPU               | 84        |
| Placa-mãe         | 70        |
| SSD               | 15        |
| RAM               | 3         |

### Instruções

1. **Calcule o consumo total dos componentes listados** somando os valores da coluna "Consumo W".
    - CPU: 84 W
    - Placa-mãe: 70 W
    - SSD: 15 W
    - RAM: 3 W

2. **Adicione um fator de segurança**. Um valor comum é adicionar 20% sobre o consumo total. Isso garante que a fonte possa lidar com picos de energia e outros componentes não listados (como GPU, cooler, unidades de disco rígido tradicionais, etc.).

    Para calcular o consumo total com segurança:

    ```
    Consumo Total com Segurança = (Consumo Total dos Componentes) + (20% do Consumo Total dos Componentes)
    ```

    Ou, de forma mais direta:

    ```
    Consumo Total com Segurança = Consumo Total dos Componentes * 1.2
    ```

### Espaço para Cálculo

- **Consumo Total dos Componentes (sem segurança):**

    ```
    CPU: 84 W
    Placa-mãe: 70 W
    SSD: 15 W
    RAM: 3 W
    Total: ________ W
    ```

- **Consumo Total com Segurança (20%):**

    ```
    Total com Segurança = Total dos Componentes * 1.2
    Total com Segurança = ________ W * 1.2 = ________ W
    ```

### Resposta

- Qual é o **consumo total mínimo** que a fonte de alimentação deve fornecer, considerando o fator de segurança?

    ________ W

### Nota Importante

Os valores de consumo fornecidos (especialmente para SSD e RAM) podem ser simplificações ou valores máximos estimados. Valores reais podem variar. Recomenda-se pesquisar especificações mais detalhadas dos componentes para cálculos mais precisos.

## Referências

- [Calculador de Fonte](https://www.coolermaster.com/pt-br/power-supply-calculator/)
