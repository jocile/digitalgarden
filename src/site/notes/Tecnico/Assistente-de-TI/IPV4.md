---
{"dg-publish":true,"permalink":"/tecnico/assistente-de-ti/ipv-4/","metatags":{"description":"Em uma rede de computadores é necessário o endereçamento correto para que haja comunicação."},"noteIcon":2,"updated":"2025-12-01T11:16:09.695-03:00"}
---

#simulador

## Octetos e notação decimal com ponto

Os endereços IPv4 têm 32 bits de comprimento. Aqui está um endereço IPv4 em binário:  
**11010001101001011100100000000001**

Observe como é difícil ler este endereço. Imagine ter que configurar dispositivos com uma série de 32 bits! Por esse motivo, os 32 bits são agrupados em quatro bytes de 8 bits chamado octetos:  
**11010001.10100101.11001000.00000001**

Está melhor, mas ainda assim difícil de ler. É por isso que convertemos cada octeto em seu valor decimal, separados por um ponto decimal ou por um período. O IPv4 binário acima torna-se esta representação decimal com ponto  
**: 209.165.200.1**

**Observação:** por enquanto, você não precisa saber como converter entre sistemas de números binários e decimais

## Redes e hosts

O endereço lógico IPv4 de 32 bits é hierárquico e contém duas partes, a rede e o host Na figura, a porção de rede é azul e a porção de host é vermelha. As duas partes são necessárias em um endereço IPv4. Ambas as redes têm a máscara de sub-rede 255.255.255.0. Máscara de sub-rede é usada para identificar a rede à qual o host está conectado.

Como exemplo, um host com o endereço IPv4 192.168.5.11 e a máscara de sub-rede 255.255.255.0. Os três primeiros octetos (192.168.5) identificam a porção de rede do endereço e o último octeto (11) identifica o host. Isso é conhecido como endereçamento hierárquico porque a porção de rede indica a rede na qual está localizado cada endereço exclusivo de host. Os roteadores precisam saber apenas como alcançar cada rede, em vez de precisar saber a localização de cada host individual.

Com o endereçamento IPv4, poderão existir diversas redes lógicas em uma rede física se a porção de rede dos endereços de hosts de rede lógica for diferente. Por exemplo: três hosts em uma única rede local física têm a mesma porção de rede do endereço IPv4 (192.168.18) e outros três hosts têm porções de rede diferentes de seus endereços IPv4 (192.168.5). Os hosts com o mesmo número de rede em seus endereços IPv4 poderão se comunicar entre si, mas não com os outros hosts sem o uso de roteamento. Neste exemplo, há uma rede física e duas redes IPv4 lógicas.

Outro exemplo de rede hierárquica é o sistema telefônico. Em um número de telefone, o código de país, o código de área e a central telefônica representam o endereço de rede e os dígitos restantes representam um número de telefone local.

## Endereços IPv4 públicos e privados

Assim como existem diferentes maneiras de transmitir um pacote IPv4, existem também diferentes tipos de endereços IPv4. Alguns endereços IPv4 não podem ser usados para sair para a Internet, e outros são especificamente alocados para roteamento para a Internet. Alguns são usados para verificar uma conexão e outros são auto-atribuídos. Como administrador de rede, você acabará se familiarizando com os tipos de endereços IPv4, mas por enquanto, você deve pelo menos saber o que eles são e quando usá-los.

Endereços IPv4 públicos são endereços roteados globalmente entre os roteadores do provedor de serviços de Internet (ISP). No entanto, nem todos os endereços IPv4 disponíveis podem ser usados na Internet . Existem blocos de endereços (conhecidos como endereços privados) que são usados pela maioria das organizações para atribuir endereços IPv4 a hosts internos.

Em meados dos anos 90, com a introdução da World Wide Web (WWW), endereços IPv4 privados foram introduzidos devido ao esgotamento do espaço de endereços IPv4. Os endereços IPv4 privados não são exclusivos e podem ser usados internamente em qualquer rede.

>[!info] A solução a longo prazo para o esgotamento de endereços IPv4 foi o IPv6.

<table class="" tabindex="0" style="min-width: 800px">
                <!--?lit$944484145$--><!---->
                    <tr class="table-row nth-child-0 ">
                    <!--?lit$944484145$--><!---->
                                <th scope="col" rowspan="1" colspan="1" class="table-data table-heading nth-child-0 ">
                                   <!--?lit$944484145$-->Endereço de rede e prefixo
                                    <!--?lit$944484145$-->
                                </th>
                                <!----><!---->
                                <th scope="col" rowspan="1" colspan="1" class="table-data table-heading nth-child-1 ">
                                   <!--?lit$944484145$-->RFC 1918 Intervalo de endereços privados
                                    <!--?lit$944484145$-->
                                </th>
                                <!---->
                   </tr>  
                    <!----><!---->
                    <tr class="table-row nth-child-1 ">
                    <!--?lit$944484145$--><!---->
                                <td tabindex="0" rowspan="1" colspan="1" class="table-data nth-child-0 " width="200">
                                <!--?lit$944484145$-->10.0.0.0/8
                                 <!--?lit$944484145$-->
                                </td>
                                <!----><!---->
                                <td tabindex="0" rowspan="1" colspan="1" class="table-data nth-child-1 " width="">
                                <!--?lit$944484145$-->10.0.0.0 - 10.255.255.255
                                 <!--?lit$944484145$-->
                                </td>
                                <!---->
                   </tr>  
                    <!----><!---->
                    <tr class="table-row nth-child-2 ">
                    <!--?lit$944484145$--><!---->
                                <td tabindex="0" rowspan="1" colspan="1" class="table-data nth-child-0 " width="200">
                                <!--?lit$944484145$-->172.16.0.0/12
                                 <!--?lit$944484145$-->
                                </td>
                                <!----><!---->
                                <td tabindex="0" rowspan="1" colspan="1" class="table-data nth-child-1 " width="">
                                <!--?lit$944484145$-->172.16.0.0 - 172.31.255.255
                                 <!--?lit$944484145$-->
                                </td>
                                <!---->
                   </tr>  
                    <!----><!---->
                    <tr class="table-row nth-child-3 ">
                    <!--?lit$944484145$--><!---->
                                <td tabindex="0" rowspan="1" colspan="1" class="table-data nth-child-0 " width="200">
                                <!--?lit$944484145$-->192.168.0.0/16
                                 <!--?lit$944484145$-->
                                </td>
                                <!----><!---->
                                <td tabindex="0" rowspan="1" colspan="1" class="table-data nth-child-1 " width="">
                                <!--?lit$944484145$-->192.168.0.0 - 192.168.255.255
                                 <!--?lit$944484145$-->
                                </td>
                                <!---->
                   </tr>  
                    <!---->
                </table>

## Endereços IPv4 de Uso Especial

Os endereços de loopback (127.0.0.0 / 8 ou 127.0.0.1 a 127.255.255.254) são comumente identificados apenas como 127.0.0.1. Eles são endereços especiais usados por um host para direcionar tráfego para ele mesmo Por exemplo, o comando ping, é comumente usado para testar conexões com outros hosts. Mas você também pode usar o comando ping para testar a configuração de IP do seu próprio dispositivo.

Os endereços locais de link (169.254.0.0 / 16 ou 169.254.0.1 a 169.254.255.254) são mais conhecidos como endereços APIPA ( endereçamento IP privado automático ) ou endereços auto-atribuídos. Eles são usados por um cliente Windows para se autoconfigurar caso o cliente não consiga obter um endereçamento IP por outros métodos. Endereços de link local podem ser usados em uma conexão ponto a ponto, mas não são comumente usados para esse fim.

## Endereçamento Classful Legado

Em 1981, os endereços IPv4 foram atribuídos usando o endereço classful, conforme definido na RFC 790 ( [RFC 790 - Assigned numbers](https://tools.ietf.org/html/rfc790) ), Números Atribuídos Os clientes receberam um endereço de rede com base em uma das três classes, A, B ou C. A RFC dividiu os intervalos de unicast em classes específicas da seguinte maneira:

- **Classe A (0.0.0.0/8 to 127.0.0.0/8)** – Projetado para suportar redes extremamente grandes com mais de 16 milhões de endereços de host. A Classe A usou um prefixo fixo /8 com o primeiro octeto para indicar o endereço de rede e os três octetos restantes para endereços de host (mais de 16 milhões de endereços de host por rede).
- **Classe B (128.0.0.0 / 16 - 191.255.0.0 / 16)** - Projetada para oferecer suporte às necessidades de redes de tamanho moderado a grande com até aproximadamente 65.000 endereços de host. A Classe B usou um prefixo fixo /16 com os dois octetos de alta ordem para indicar o endereço de rede e os dois octetos restantes para endereços de host (mais de 65.000 endereços de host por rede).
- **Classe C (192.0.0.0 / 24 - 223.255.255.0 / 24)** - Projetado para oferecer suporte a pequenas redes com no máximo 254 hosts. A Classe C usou um prefixo fixo / 24 com os três primeiros octetos para indicar a rede e o octeto restante para os endereços de host (apenas 254 endereços de host por rede).

**Observação:** Há também um bloco multicast Classe D consistindo de 224.0.0.0 a 239.0.0.0 e um bloco de endereço experimental Classe E consistindo de 240.0.0.0 - 255.0.0.0.

Na época, com um número limitado de computadores usando a internet, o endereçamento clássico era um meio eficaz para alocar endereços. Como mostrado na figura, as redes de classe A e B têm um número muito grande de endereços de host e Classe C tem muito poucos. As redes de classe A representaram 50% das redes IPv4. Isso fez com que a maioria dos endereços IPv4 disponíveis não fossem utilizados.

Em meados da década de 1990, com a introdução da World Wide Web (WWW), o endereçamento clássico foi obsoleto para alocar de forma mais eficiente o espaço de endereços IPv4 limitado. A alocação de endereço de classe foi substituída por endereçamento sem classe, que é usado hoje. O endereçamento sem classe ignora as regras das classes (A, B, C). Endereços de rede IPv4 públicos (endereços de rede e máscaras de sub-rede) são alocados com base no número de endereços que podem ser justificados.

## Atribuição de Endereços IP

Endereços IPv4 públicos são endereços roteados globalmente pela Internet. Endereços IPv4 públicos devem ser exclusivos.

Os endereços IPv4 e IPv6 são gerenciados pela IANA (Internet Assigned Numbers Authority). A IANA gerencia e aloca blocos de endereços IP aos registros regionais de Internet (RIRs).

Os RIRs são responsáveis por alocar endereços IP aos ISPs que fornecem blocos de endereços IPv4 para organizações e ISPs menores. As organizações também podem obter seus endereços diretamente de um RIR (sujeito às políticas desse RIR).

### Registros Regionais da Internet

- **AfriNIC**(Centro de Informação de Redes Africanas) - Região da África
- **APNIC**(Centro de informações de redes da Ásia-Pacífico) - Região Ásia/Pacífico
- **ARIN**(Registro Americano de Números da Internet) - Região da América do Norte
- **LACNIC**(Registro regional de endereços IP da América Latina e do Caribe) - América Latina e algumas ilhas do Caribe
- **RIPE NCC**(Centro de coordenação da rede Réseaux IP Européens) - Europa, Oriente Médio e Ásia Central

## Referências

- [INFRAESTRUTURA DE REDES \| Jocile](https://jocile.github.io/aulas/categories/infraestrutura-de-redes/)
