---
{"dg-publish":true,"permalink":"/assistente-de-ti/calculos-eletricos/","title":"Cálculos elétricos","metatags":{"description":"Como dimensionar equipamentos elétricos"},"tags":["eletricidade"],"noteIcon":1,"updated":"2025-04-21T18:36:14.514-03:00"}
---

# Cálculos elétricos

Como calcular o dimensionamento de potência de uma fonte de computador gamer.

## Dimensionamento de fonte de computador

Para calcular o dimensionamento de potência de uma fonte de computador gamer, siga os seguintes passos:

### 1. Identificar os Componentes Principais

- **Processador (CPU):** Marca e modelo da CPU ou especificações técnicas.
- **Unidade de Processamento Gráfico (GPU):** Marca e modelo da GPU ou especificações técnicas.
- **Memória RAM:** Tamanho da memória em GB e velocidade de clock.
- **Discos Rígidos (HDD) e Discos Solid State Drive (SSD):** Capacidade dos discos e velocidade de leitura/escrita.

### 2. Determinar as Especificações Técnicas

Para cada componente, identifique:

- **Tensão de operação:** Maior tensão necessária para o componente funcionar.
- **Consumo de potência:** Valor máximo de poder que o componente utiliza.
- **Frequência de clock:** Velocidade de operação do componente.

### 3. Especificações da Fonte de Potência

Comparar as especificações das fontes de potência disponíveis, como:

- **Capacidade de saída contínua (Continuous Power Output):** Valor máximo que a fonte pode fornecer.
- **Eficiência:** Relação entre a entrada de energia e a saída de energia.
- **Qualidade:** Certificação de qualidade (típica ou platinum,ouro).

### 4. Cálculo do Consumo Total

Somar o consumo de potência de todos os componentes conectados:

`Consumo total = Consumo da CPU + Consumo da GPU + Consumo da memória RAM + Consumo dos discos`

### 5. Considerar Margem de Segurança

Recomendar que a potência da fonte seja aproximadamente 10% maior do que o consumo total calculado para garantir um funcionamento adequado sem cortesia de energia.

### 6. Recomendação Final

Selecione uma fonte de potência que atenda às especificações dos componentes e garanta um suprimento confiável de energia para o sistema.

### Exemplo

- Se o consumo total for 500W, recomende uma fonte com potência mínima de 550W.

---

Essa dimensionamento garantirá que sua fonte de computador gamer funcione eficientemente e possua estabilidade no fornecimento de energia.

Lembrando que para placas de vídeo top o ideal é uma linha +12v com 26A, e para SLI com 34A.

Na hora da compra do estabilizador/nobreak que aguente a capacidade da fonte, para isso utilizem o cálculo a seguir:

`VA = Watts/0.65*`

Exemplo: `VA = 430/0.65`
`VA = 661,...`

* Valor médio de eficiência dos estabilizadores/nobreaks (65%)

Calculando o fator de potência do seu estabilizador/nobreak. Então o 0,65 NÃO é válido.

`VA = Watts/FP` (fator de potência).

Se você tiver um estabilizador de `1000VA` e uma fonte de `430W`:

```
a) FP = 0,35:
1000 = W/0,35
W = 350W
350 < 430, então o estabilizador não vai servir.

b) FP = 0,65:
1000 = W/0,65
W = 650W
350 > 430, então o estabilizador vai servir.

c) FP = 0,8:
1000 = W/0,8
W = 800W
800 > 430, então o estabilizador vai servir.
```

Eu costumo fazer a seguinte conta: Para não sobrecarregar o seu estabilizador, coloque a potência máxima consumida pelo seu micro como `70%` da potência máxima oferecida pelo seu estabilizador.

Por exemplo, se eu for comprar um estabilizador de boa procedência, ele terá o fator de potência acima ou igual a 0,7:

```
Fonte = 480W
Monitor = 100W (pior das hipóteses).
Impressora jato de tinta = 30W
Cxs. de som padrões = 5W
Soma dos demais acessórios (modem, joystick ff, entre outros) = 30W

Total = 645W
```

Ok, então o meu PC consumirá 645W no máximo.

Agente não pode simplesmente pegar um estabilizador de 645W, pois ele estaria na carga máxima.

Então, regrinha de 3 básica:

```
645 -> 70%
x -> 100%
x =~ 921W

Lembram do FP do nosso estabilizador? Era 0,7:
VA = W/FP
VA = 921/0,7
VA = 1316VA
```


Então, um estabilizador bom para a minha configuração é o que possuir a potência mais próxima do `1316VA`.

Por isso, antes de comprar um estabilizador/nobreak, procure o fator de potência no manual. E prefira boas marcas como `APC/SMS/Enermax`.

## Referências

- [PSU Calculator \| Cooler Master](https://www.coolermaster.com/pt-br/power-supply-calculator/)
- [MSI Power Supply Calculator](https://www.msi.com/power-supply-calculator)
- [Power Supply calculator - calc for silent PSUs from be quiet!](https://www.bequiet.com/en/psucalculator)
- [PC Power Supply Calculator – PSU Wattage Calculator \| Newegg](https://www.newegg.com/tools/power-supply-calculator)
- [PSU Calculator \| PC Power Supply Wattage Calculator \| CORAIR](https://www.corsair.com/ww/en/s/power-supply-calculator?srsltid=AfmBOoqWb5jDi9r5jtCfjLdQaRoM4-R-rBMVIhbJDuqnr4nfinGwfZNK)
- [Power Supply Unit (PSU) Calculator \| PC Builds](https://pc-builds.com/power-supply-calculator/)
- [ASUS PSU Calculator \| Republic of Gamers \| ASUS](https://rog.asus.com/event/psu/asus-power-supply-calculator/br/index.html)
- [PSU Calculator \| PC Power Supply Wattage Calculator \| CORSAIR](https://www.corsair.com/pt/pt/s/power-supply-calculator)
- [Cálculo de Watts para compra de fonte para seu PC! \| Fórum Adrenaline - Um dos maiores e mais ativos fóruns do Brasil](https://forum.adrenaline.com.br/threads/calculo-de-watts-para-compra-de-fonte-para-seu-pc.102650/)
