---
{"dg-publish":true,"permalink":"/tecnico/assistente-de-ti/memoria-ram/","title":"Chipsets de Placas-Mãe","metatags":{"description":"é um local de acesso rápido para arquivos e aplicações em uso durante uma sessão ativa"},"noteIcon":"1","updated":"2025-11-11T13:51:32.356-03:00"}
---

#Aulas #Hardware #Assistente-de-TI

# Relatório Técnico: Análise dos Fatores de Desempenho da Memória RAM

## 1.0 Introdução

A memória RAM (_Random Access Memory_) é um componente fundamental para o desempenho de sistemas computacionais modernos, atuando como um espaço de trabalho de alta velocidade para o processador. Diferentemente das memórias de armazenamento não voláteis, como discos rígidos (HDs) e unidades de estado sólido (SSDs), que retêm dados permanentemente, a memória RAM é volátil. Isso significa que todas as informações armazenadas nela são descartadas quando o computador é desligado, servindo como um local de acesso rápido para arquivos e aplicações em uso durante uma sessão ativa.

O objetivo central deste documento é realizar uma análise técnica aprofundada dos três principais fatores que determinam o desempenho da RAM: **frequência**, **latência** e **largura de banda**. Este relatório detalhará as fórmulas padrão da indústria para quantificar esses fatores e examinará, por meio de um estudo de caso prático, a interação entre eles e seu impacto real no desempenho do sistema.

A seguir, exploraremos os conceitos fundamentais que servem como alicerce para a compreensão do desempenho da memória, desmistificando os termos técnicos e estabelecendo uma base sólida para a análise subsequente.

## 2.0 Os Pilares do Desempenho da Memória RAM

A compreensão do desempenho da memória RAM começa com a definição clara de seus três pilares: frequência, latência e largura de banda. Cada um desses fatores desempenha um papel distinto, porém interconectado, na determinação da agilidade e da capacidade de resposta de um sistema.

### 2.1 Frequência (Clock)

A frequência, também conhecida como clock, é a medida da velocidade operacional da memória, expressa em Megahertz (MHz). Ela representa a quantidade de ciclos de operação que a memória consegue executar por segundo. De forma análoga, quanto maior a frequência, mais operações de transferência de dados podem ser realizadas em um determinado período, resultando em um desempenho superior.

Um aspecto crucial da tecnologia de memória moderna é o **DDR (**_**Double Data Rate**_**)**. Essa tecnologia permite que a memória transfira dois pacotes de dados por ciclo de clock. Por essa razão, a frequência efetiva anunciada comercialmente (ex: 3200 MHz) é o dobro da frequência real de operação do barramento (neste caso, aproximadamente 1600 MHz), pois o sistema aproveita tanto a subida quanto a descida do sinal de clock para transmitir informações.

### 2.2 Latência (CAS Latency - CL)

A latência refere-se ao tempo de atraso que a memória leva para responder a uma solicitação. O principal indicador desse fator é o **CAS Latency (CL)**, ou Latência de Acesso à Coluna. O valor de CL (ex: CL16, CL18, CL40) representa o número de ciclos de clock que a memória necessita aguardar antes de poder acessar e entregar os dados solicitados de uma coluna específica em seus bancos de dados. Para tornar o conceito mais tangível, imagine um segundo dividido em 3.2 bilhões de "passos" para uma memória de 3200 MHz. Um valor de CL18 significa que, após uma requisição, a memória deve aguardar 18 desses "passos" antes de iniciar a transferência do dado solicitado.

Em princípio, um valor de CL _menor_ é preferível, pois indica um tempo de espera mais curto para iniciar a transferência de dados. É importante notar que o CL é apenas a principal de uma série de outras latências (conhecidas como _timings_) que, em conjunto, afetam o desempenho geral da memória.

### 2.3 Largura de Banda e a Importância do Dual Channel

A largura de banda é a métrica que define a velocidade efetiva de transmissão de dados entre a memória RAM e o processador, medida em megabytes por segundo (MB/s). Embora a frequência seja um componente chave para essa velocidade, a configuração dos canais de memória tem um impacto ainda mais crítico.

Um único módulo de memória opera com um barramento de comunicação de **64 bits (Single Channel)**. No entanto, as plataformas modernas são projetadas para utilizar múltiplos canais simultaneamente. Ao instalar dois módulos de memória idênticos nos slots corretos da placa-mãe, a configuração **Dual Channel** é ativada. Isso efetivamente dobra a largura do barramento para **128 bits**, duplicando a largura de banda teórica e permitindo que o processador acesse os dois módulos ao mesmo tempo. (Nota: As memórias DDR5 possuem uma arquitetura interna de dois canais de 32 bits por módulo para maior eficiência, mas para fins de cálculo de largura de banda sistêmica, a premissa de dois módulos criando um barramento de 128 bits permanece o princípio operativo.)

Em suma, a frequência (a velocidade dos ciclos), a latência (o número de ciclos de espera) e a largura de banda (o volume de dados transferidos, dependente da frequência e da configuração dos canais) formam uma tríade de desempenho. Um desequilíbrio em qualquer um desses pilares pode criar um gargalo, mas, como a análise subsequente demonstrará, o aumento da largura de banda através de altas frequências e Dual Channel tende a oferecer o impacto mais pronunciado nos sistemas contemporâneos.

## 3.0 Quantificando o Desempenho: Fórmulas Teóricas

Para traduzir os conceitos de frequência e latência em métricas tangíveis e comparáveis, a indústria utiliza fórmulas padrão. Estes cálculos permitem estimar o desempenho teórico de um sistema de memória antes mesmo de sua instalação. Esta seção apresenta as fórmulas para determinar a largura de banda teórica e a latência efetiva em nanossegundos.

### 3.1 Cálculo da Largura de Banda Teórica

A largura de banda teórica máxima quantifica a taxa de transferência de dados que um sistema de memória pode atingir. A fórmula leva em consideração a frequência efetiva da memória e a largura do barramento de dados.

|Componente|Fórmula|
|---|---|
|**Largura de Banda (MB/s)**|`(Frequência em MHz * Largura do Barramento em bits) / 8`|

**Exemplo Prático:** Para um kit de memória DDR4 de **3200 MHz** operando em **Dual Channel (128 bits)**: `(3200 * 128) / 8 = 51.200 MB/s`

Este resultado indica que, teoricamente, o sistema pode transferir até 51.200 megabytes por segundo.

### 3.2 Cálculo da Latência Efetiva em Nanossegundos

O valor de CL representa ciclos de clock, uma medida relativa que depende da frequência. Para comparar de forma justa memórias com frequências e latências diferentes, é crucial converter o CL em uma medida de tempo real: nanossegundos (ns). A lógica da fórmula calcula a duração de um único ciclo de clock em nanossegundos (`1000 / Frequência Real em MHz`) e a multiplica pelo número de ciclos (CL). Como a frequência efetiva (DDR) é o dobro da real, a fórmula se simplifica para o formato abaixo.

|Componente|Fórmula|
|---|---|
|**Latência Efetiva (ns)**|`(CL * 2000) / Frequência em MHz`|

**Exemplo Prático:** Para uma memória de **3200 MHz** com **CL18**: `(18 * 2000) / 3200 = 11,25 ns`

Este cálculo é crucial para comparar o tempo de resposta real entre diferentes módulos, revelando que uma memória de frequência mais alta pode, em alguns casos, ter uma latência efetiva maior que uma de frequência mais baixa com CL inferior.

## 4.0 Análise Comparativa: A Interação entre Frequência e Latência

Na prática, a seleção de uma memória RAM frequentemente envolve um dilema: a relação inversa que pode existir entre alta frequência e baixa latência (CL). Módulos com frequências muito elevadas tendem a apresentar valores de CL mais altos para manter a estabilidade. Para desvendar qual fator exerce maior impacto no desempenho real, foi realizado um estudo de caso comparando dois notebooks com especificações de memória distintas.

### 4.1 Estudo de Caso: Análise Teórica vs. Prática

Os sistemas de teste foram um notebook ROG Zephyrus e um Samsung Galaxy Book3, ambos equipados com memórias de última geração, mas com perfis de frequência e latência opostos.

|Característica|Notebook 1 (ROG Zephyrus)|Notebook 2 (Samsung Galaxy Book3)|
|---|---|---|
|**Tecnologia**|DDR5|LPDDR5|
|**Frequência**|4800 MHz|6000 MHz|
|**Latência (CL)**|CL40|CL60|

Aplicando as fórmulas da seção anterior, obtemos os seguintes resultados teóricos:

|Métrica Teórica|Notebook 1 (4800 MHz CL40)|Notebook 2 (6000 MHz CL60)|Vantagem|
|---|---|---|---|
|**Largura de Banda (MB/s)**|76.800|96.000|**Notebook 2**|
|**Latência Efetiva (ns)**|16,64|20,00|**Notebook 1**|

A análise teórica aponta para um cenário contraditório: o Notebook 2 possui uma largura de banda teórica significativamente maior, enquanto o Notebook 1 apresenta uma latência efetiva teoricamente inferior. Para determinar o vencedor no mundo real, foi utilizado o benchmark **Aida64 Extreme**.

|Métrica de Benchmark|Notebook 1 (ROG Zephyrus)|Notebook 2 (Samsung Galaxy Book3)|Vantagem|
|---|---|---|---|
|**Leitura (MB/s)**|61.600|69.300|**Notebook 2**|
|**Escrita (MB/s)**|57.600|85.700|**Notebook 2**|
|**Cópia (MB/s)**|54.800|73.500|**Notebook 2**|
|**Latência Geral (ns)**|95,3|90,0|**Notebook 2**|

### 4.2 Análise e Conclusões do Estudo de Caso

A análise dos dados empíricos leva a uma conclusão inequívoca: o Notebook 2, equipado com a memória de **6000 MHz**, superou o Notebook 1 em **todas** as métricas de desempenho real. Isso inclui não apenas as taxas de transferência (leitura, escrita e cópia), mas também a latência geral medida pelo benchmark, que foi inferior (90,0 ns) apesar de seu valor CL nominalmente maior (CL60). É crucial observar que os valores de benchmark, embora sigam a tendência teórica, são naturalmente inferiores aos máximos calculados. A largura de banda teórica representa um pico ideal, enquanto os testes práticos medem o desempenho em cenários reais que envolvem múltiplas latências e ineficiências do sistema.

É importante ressaltar que os sistemas de teste possuem processadores distintos (um Core i7 e um Core i9 de gerações diferentes), o que representa uma variável de confusão. No entanto, embora a diferença de CPU seja um fator, os resultados do benchmark de memória sugerem fortemente que o aumento massivo na frequência e na largura de banda foi o principal impulsionador do desempenho superior da memória, superando a desvantagem do valor CL nominalmente mais alto.

O estudo de caso demonstra que, em sistemas modernos, o ganho de desempenho proporcionado por uma frequência significativamente maior tende a superar a desvantagem de uma latência CL mais elevada, pois o impacto na largura de banda total é mais pronunciado. O impacto do desempenho da RAM, contudo, também varia de acordo com a arquitetura do processador e o tipo de aplicação.

## 5.0 Impacto Sistêmico e Recomendações

O desempenho da memória RAM não existe no vácuo; ele interage diretamente com a arquitetura do processador e as demandas do software. A análise final deste relatório examina como diferentes plataformas de CPU e tipos de aplicações respondem a memórias de alta performance, culminando em um conjunto de recomendações práticas para a seleção e otimização de sistemas.

### 5.1 Influência da Arquitetura do Processador e da Aplicação

Testes comparativos demonstram que diferentes arquiteturas de processador respondem de maneiras distintas a variações na velocidade da RAM.

- **Plataformas Intel:** A arquitetura da Intel demonstrou maior sensibilidade à velocidade da memória, resultando em ganhos de desempenho mais substanciais, variando de **7% a 18%** em benchmarks e jogos. Aplicações sensíveis à latência, como jogos competitivos de alta taxa de quadros, foram as que mais se beneficiaram.
- **Plataformas AMD:** Arquiteturas AMD Ryzen mais recentes (série 5000) mostraram-se menos sensíveis a variações na frequência da RAM. Isso se deve, em grande parte, à implementação de um cache L3 de grande capacidade, que atua como um buffer de alta velocidade entre os núcleos da CPU e a memória principal. Quando o dado requisitado está presente no cache (um "cache hit"), a CPU evita um acesso muito mais lento à RAM. Um cache maior aumenta a probabilidade de "cache hits", reduzindo a dependência geral do sistema na velocidade da memória para muitas cargas de trabalho.

O tipo de carga de trabalho (_workload_) também é um fator determinante:

- **Renderização:** Tarefas como renderização no software Blender mostraram um impacto inexistente ou marginal com o aumento da frequência da RAM.
- **Jogos:** Jogos competitivos, como _Rainbow Six Siege_, rodando em altas taxas de quadros, foram os que mais se beneficiaram de memórias de alta frequência, com ganhos de desempenho que chegaram a dois dígitos percentuais.

### 5.2 Diretrizes Estratégicas para Seleção e Otimização

Com base na análise técnica e nos resultados práticos, as seguintes diretrizes são apresentadas como prioridades estratégicas para projetistas e otimizadores de sistemas:

- **Prioridade Máxima: Dual Channel** Sempre opte por uma configuração de **Dual Channel** (utilizando dois ou quatro módulos de memória). Esta é a otimização mais impactante, pois dobra a largura de banda disponível e proporciona um dos maiores ganhos de desempenho possíveis com baixo custo.
- **Frequência vs. Latência** Em sistemas modernos (DDR4 e DDR5), priorize a **frequência mais alta** que a plataforma (placa-mãe e processador) suporta de forma estável. O benefício em largura de banda geralmente supera um valor de CL marginalmente menor, pois as arquiteturas de CPU modernas são projetadas para processar grandes volumes de dados em paralelo, tornando a taxa de transferência (largura de banda) um gargalo mais significativo do que a latência de primeiro acesso (CL).
- **Análise Justa** Ao comparar módulos com frequências e latências diferentes, não se baseie apenas nos valores de CL. Utilize o cálculo de **latência efetiva em nanossegundos** para obter uma medida real e justa do tempo de resposta.
- **Compatibilidade do Sistema** Verifique sempre as especificações da placa-mãe e do processador para garantir a compatibilidade com a frequência e a tecnologia da memória. Considere a arquitetura da CPU para avaliar o ganho de desempenho potencial, sendo que plataformas Intel tendem a se beneficiar mais em cenários específicos, como jogos de alta performance.

Em conclusão, embora frequência e latência sejam cruciais, o foco das arquiteturas computacionais contemporâneas no processamento paralelo e na transferência de grandes volumes de dados posiciona a largura de banda como o fator preponderante. Portanto, a estratégia mais eficaz para desbloquear o potencial de desempenho de um sistema é maximizar sua largura de banda por meio de altas frequências e, fundamentalmente, uma configuração de memória multi-channel. O impacto dessa abordagem é mais acentuado em cargas de trabalho sensíveis à latência, como jogos de alta taxa de quadros, especialmente em plataformas projetadas para alavancar essa vantagem.

## 6.0 A 3volução da memória RAM

A trajetória evolutiva das tecnologias de memória **DDR (Double Data Rate)**, ou **taxa de transferência dupla**, é marcada por uma busca contínua por maior velocidade de operação, mais capacidade de armazenamento e, notavelmente, maior eficiência energética.

O conceito central da tecnologia DDR é que ela consegue transmitir dados duas vezes por ciclo de operação (ou seja, em cada semiciclo), o que justifica o rótulo de frequência ser o dobro da frequência de operação real identificada pelo sistema.

A evolução pode ser rastreada através das seguintes gerações:

![Memória RAM-1762876128847.png](/img/user/Tecnico/Assistente-de-TI/Mem%C3%B3ria%20RAM-1762876128847.png)

### 6.1. DDR1 (DDR SD RAM)

- **Lançamento:** Foi lançada por volta dos anos 2000.
- **Voltagem:** Operava com uma voltagem de aproximadamente **2,5V a 2,6V**.
- **Pinos:** Utilizava 184 pinos nos módulos de desktop e 200 pinos nos módulos de notebook.
- **Frequência e Largura de Banda:** As frequências iam de 200 até **400 MHz efetivos**, entregando até **3,2 GB/segundo** de largura de banda.
- **Capacidade e Recursos:** Módulos normalmente alcançavam o máximo de 1 GB e utilizavam um buffer de pré-busca (pre-fetch buffer) **2N**.
- **Impacto:** Foi revolucionária em comparação com a SD RAM, mas apresentava **alto consumo de energia e calor excessivo**.

### 6.2. DDR2

- **Lançamento:** Chegou em 2003, focando em mais desempenho e eficiência energética.
- **Voltagem:** Caiu para **1,8V**, o que representou uma redução significativa no consumo em relação à DDR1.
- **Pinos:** Subiu para 240 (desktop) e manteve 200 (notebook).
- **Incompatibilidade:** O entalhe mudou de posição para evitar que fosse encaixada em placas-mãe DDR1.
- **Frequência e Largura de Banda:** As frequências **dobraram**, variando de 400 até **1066 MHz**, atingindo cerca de **8,5 GB/segundo** de largura de banda.
- **Capacidade e Recursos:** Cada módulo podia chegar a até 4 GB. Trouxe o buffer de pré-busca **4N** e a terminação _On-Die Termination_ (que ajudava a limpar sinais e reduzir interferências).
- **Desvantagem:** Ficou marcada por ter **latências mais altas** em alguns casos, o que podia anular parte do ganho de velocidade bruta.

### 6.3. DDR3

- **Lançamento:** Apareceu em 2007.
- **Voltagem:** Caiu novamente, com padrão de **1,5V** e conversões de baixo consumo em 1,35V.
- **Pinos:** Permaneceu em 240, mas com o entalhe movido mais uma vez.
- **Frequência e Largura de Banda:** Variava de 800 até **2133 MHz**, empurrando a largura de banda para mais de **17 GB/segundo**.
- **Capacidade e Recursos:** Suportava até **16 GB por módulo**. Introduziu o buffer de pré-busca **8N** e a topologia _Flyby_, que organizava melhor os sinais entre os chips.
- **Eficiência e Duração:** Ofereceu cerca de **30% mais eficiência energética** do que a DDR2. Foi a geração que **mais durou**, dominando por quase uma década e popularizando PCs gamers acessíveis.

### 6.4. DDR4

- **Lançamento:** Lançada em 2014.
- **Voltagem:** Reduziu ainda mais a voltagem, para **1,2V**.
- **Pinos:** Aumentou para **288**, e o entalhe foi novamente alterado.
- **Frequência e Largura de Banda:** Começava em 1600 MHz e ia oficialmente até 3200 MHz (embora entusiastas atingissem frequências muito maiores com overclock extremo). A largura de banda ultrapassava **25 GB/segundo**.
- **Capacidade e Recursos:** Trouxe grupos de bancos para processamento paralelo e verificação de erro CRC, permitindo módulos gigantescos, chegando a até **128 GB por pente** em versões para servidores.
- **Impacto:** Consolidou-se nos processadores Intel Sky Lake e AMD Ryzen de primeira geração, e foi a geração que marcou a **era dos RGBs** nas memórias RAM. É, juntamente com a DDR3, uma das tecnologias mais populares.

### 6.5. DDR5

- **Lançamento:** Chegou ao mercado consumidor em **2021**.
- **Voltagem:** Atingiu o ponto mais baixo, com apenas **1,1V**.
- **Pinos:** Manteve 288 pinos, mas com alteração no entalhe.
- **Frequência e Largura de Banda:** As velocidades base começam em **4800 MHz** e já ultrapassam 9600 MHz em módulos de ponta. A largura de banda mínima começa acima de **38 GB/segundo**.
- **Capacidade e Recursos:** As capacidades são massivas, existindo módulos de até **512 GB de RAM por peça** em servidores. As novidades incluem o buffer de pré-busca **16N**, **canais duplos** dentro de cada módulo, ECC _on-die_ (para mais confiabilidade e correção automática de erros) e circuitos de gerenciamento de energia integrados.
- **Compatibilidade:** Foi adotada inicialmente pelos Intel Alder Lake e depois pelos AMD Ryzen 7000.
- **Desvantagem:** O preço é alto e há a geração de calor excessivo em velocidades extremas.

**Resumo da Evolução:**

|Tecnologia|Ano (aprox.)|Voltagem (V)|Pinos (DIMM)|Frequência (MHz)|Largura de Banda (GB/s)|
|:--|:--|:--|:--|:--|:--|
|**DDR1**|2000|2.5–2.6|184|200–400|Até 3.2|
|**DDR2**|2003|1.8|240|400–1066|Cerca de 8.5|
|**DDR3**|2007|1.5|240|800–2133|Mais de 17|
|**DDR4**|2014|1.2|288|1600–3200+|Mais de 25|
|**DDR5**|2021|1.1|288|4800–9600+|Mínimo de 38+|

Essa trajetória demonstra uma tendência clara: **cada nova geração DDR busca diminuir a voltagem para aumentar a eficiência energética, enquanto eleva as frequências e a capacidade máxima por módulo, aumentando drasticamente a largura de banda**.

Apesar do aumento teórico de velocidade, é importante notar que o ganho de performance em jogos ou em usos gerais nem sempre é proporcional ao salto tecnológico, pois outros componentes, como a arquitetura do processador e as latências (CL), também influenciam o desempenho final.

##  7.0 Perfil de performance XMP e EXPO

XMP (Extreme Memory Profile) e EXPO são tecnologias de perfis de memória que permitem que os módulos de RAM operem em suas **velocidades e configurações corretas/máximas**, conforme anunciado pelo fabricante.

Em essência, a memória RAM não funciona sozinha na frequência máxima que está escrita na caixa. Se você não ativar o perfil apropriado, sua memória pode rodar em uma frequência muito mais baixa (por exemplo, 2400 MHz ou 4800 MHz), o que penaliza o desempenho do sistema.

Os perfis contêm **conjuntos de ajustes de frequência e _timings_** (latências) que você ativa na BIOS para liberar a velocidade pela qual você pagou.

### 7.1. XMP (Extreme Memory Profile)

O XMP é o perfil historicamente utilizado, principalmente, em plataformas **Intel**.

- **Significado:** XMP significa **Extreme Memory Profile**.
- **Compatibilidade:** Originalmente projetado para placas Intel, o XMP também pode funcionar em sistemas AMD, especialmente em plataformas mais antigas.
- **Variações:** Algumas placas-mãe, como as da ASUS para AMD, podem se referir ao perfil XMP como **DOCP (DRAM Overclocking Profile)**. Há também o perfil **AMP (AMD Memory Profile)**, que é a versão para placas AMD. Os módulos podem, inclusive, oferecer diferentes perfis (Perfil 1, Perfil 2, Perfil 3) com clocks e latências variadas.

### 7.2. EXPO

O EXPO é o perfil mais recente e foi desenvolvido especificamente para **plataformas AMD**.

- **Uso:** É o perfil padrão para os sistemas AMD mais modernos, como aqueles que utilizam o **socket AM5** (Ryzen 7000 e posteriores).
- **Função:** Assim como o XMP, ele permite que o usuário ative os ajustes necessários para que a memória DDR5 atinja seu "ponto ideal" (Sweet Spot), como, por exemplo, 6000 MHz com latência CL30 nas plataformas AM5.

### 7.3 Ativação e Implicações

A ativação desses perfis é considerada **essencial** para garantir que você aproveite toda a _performance_ da memória que adquiriu.

1. **Como Ativar:** A ativação é feita diretamente na **BIOS** (ou UEFI) da placa-mãe.
2. **Localização:** Você geralmente encontra a opção nas seções de _overclock_ ou "AI Twicker". Em placas-mãe mais modernas, a opção para selecionar o perfil XMP ou EXPO pode estar disponível logo na página inicial da BIOS, exigindo apenas alguns cliques.
3. **Garantia:** Embora tecnicamente a ativação do XMP/EXPO seja considerada um _overclock_, o uso desses perfis **não costuma anular a garantia** da memória ou do processador. Isso porque os componentes são certificados para operar nessas frequências, e o fabricante da placa-mãe geralmente lista as memórias compatíveis (QVL - Qualified Vendor List) que foram testadas nesses clocks.

Em resumo, se você comprar uma memória que anuncia, por exemplo, 6000 MHz, você **precisa** ir na BIOS e ligar o perfil XMP, EXPO, ou DOCP para que ela pare de rodar no _clock_ base mais baixo e entregue a velocidade total.

---

## Referências

- [O que é memória RAM? Tudo sobre!](https://www.adrenaline.com.br/hardware/o-que-e-memoria-ram/)
- [Todas as Memórias DDR Explicadas em 8 Minutos - YouTube](https://www.youtube.com/watch?v=6ZotxnvGNTQ)
- [Notebooklm - Memórias RAM](https://notebooklm.google.com/notebook/bc219c8d-17ae-4fab-a333-d8056b2c63c8)
- [APRENDA O MAIS IMPORTANTE DA MEMÓRIA RAM E COMPRE SEMPRE O MELHOR - YouTube](https://www.youtube.com/watch?v=yXgmkPQOn5Q)
- [SAIBA EXATAMENTE QUAL MEMÓRIA RAM COMPRAR - INTEL - AMD RYZEN AM4 E AM5 - AS MELHORES OPÇÕES EM 2025 - YouTube](https://www.youtube.com/watch?v=FtyKU6kV4gE)
- [Memória RAM - Escola de Hardware - Episódio 3 - YouTube](https://www.youtube.com/watch?v=TtpOVyhIiP8)
- [GUIA COMPLETO de MEMÓRIA RAM: TUDO o que VOCÊ PRECISA SABER ANTES de COMPRAR! - YouTube](https://www.youtube.com/watch?v=MUxPXgaZ_K8)


> [!help] Páginas semelhantes
> Talvez estas páginas também interessem:
>  - [[Tecnico/Assistente-de-TI/Chipsets de Placas-Mae\|Chipsets de Placas-Mae]]
> - [[Tecnico/Assistente-de-TI/Concurso da UFC 2025\|Concurso da UFC 2025]]
> - [[Tecnico/Assistente-de-TI/Estacao-de-trabalho\|Estacao-de-trabalho]]
> - [[Tecnico/Assistente-de-TI/Placa-Mae\|Placa-Mae]]
> - [[Tecnico/Assistente-de-TI/Processadores\|Processadores]]
> - [[Tecnico/Assistente-de-TI/Simulador-de-montagem\|Simulador-de-montagem]]
> - [[Tecnico/Assistente-de-TI/Prática Orçamento para Compra de Peças do Computador\|Prática Orçamento para Compra de Peças do Computador]]
> - [[Tecnico/Assistente-de-TI/Placa de video\|Placa de video]]
> 
{ .block-language-dataview}
