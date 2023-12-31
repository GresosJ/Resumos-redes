# Capitulo 6 - Link Layer

 1. Terminology & Context
 2. Error detection, correction
 3. Multiple Acess Protocols
 4. LANs

## Terminology

- Hosts e routers: nodes
- Canais de comunicação que conectam os nós adjacentes ao longo do caminho de comunicação: links
    - wired links;
    - wireless links;
    - LANs.
- Pacote de  nivel 2 de camada : frame, encapsula o datagrama;

## Context

Respondabilidade é diferente do nível do IP. Transfere um datagrama de um node para outro que seja fisicamente adjacente.

__Framing__: encapsula o que o nivel 3 passa numa unidade de dados nivel 2 (frame). Endereço MAC é também endereço físico. 

__Controlo de fluxo__: Serviço generico que pode existir no nivel 2. Regula a cadência entre nós adjacentes. Um que envia e outro que recebe. 

__Controlo de erros__: 2 tarefaas: deteção e correção de erros. Posso receber uma entrega não fíavel e simplesmente descartar, sem corrigir. Códigos de correção são muito pouco usados porque possuem overhead muito grande. Utilizam-se então códigos de retransmissão. Redes cabeladas têm muitos poucos erros e é possivel que nem tenham coidgo de detenção de erros. Redes WI-FI, como o meio é muito mais suscetível a erros, o código de detenção de erros está sempre presente. 

__Half-duplex e Full-duplex__: Half-duplex são bidirecionais alternadas (ou transmite um ou transmite outra) e Full-duplex são simultâneas. 

__Error detection__: Deteção de erros é feita através de um código de deteção de erros. O emissor adiciona bits de deteção de erros ao frame. O receptor recebe o frame e verifica se os bits de deteção de erros estão corretos. Se não estiverem, o frame é descartado.

![Error detection](img/error-detection.png)

## Error detection, correction

EDC = Error Detection and Correction bits (redundant bits) = Datos protegidos por error checking, podem incluor header fields

Tem noção que o error detection não é 100% fiável! Estes protocolos podem não detetar erros, mas é raro. Longos EDC são mais fiáveis que curtos.

## Multiple Acess Protocols

Existem dois tipos de links

- Point-to-point :
    - PPP para dial-up; HLDC point-to-point ou multiponto;
    - Point-to-point link entre Ethernet switch e host;
- Broadcast (shared wire or medium):
    - Ethernet antigo;
    - upstream HFC (Hybrid Fiber Coax);
    - 802.11 wireless LAN;

Único canal compartilhado de broadcast. Duas ou mais transmissões simultâneas por nós = interferência. Irá decorrer colisão se dois ou mais nós transmitirem ao mesmo tempo.

__Multiple Acess Protocol__ : É um algoritmo que determina como os nós compartilham o canal. A comunicação sobre o compartilhamento de canal deve ser no próprio canal.

_Um ideal Multiple Acess Protocol_

Um protocolo de acesso múltiplo ideal

Dado: canal de transmissão de taxa R bps

 1. Quando um nó deseja transmitir, ele pode enviar na taxa R
 2. Quando M nodos querem transmitir, cada um pode enviar na taxa média R/M
 3. Totalmente descentralizado:
    - nenhum nó especial para coordenar as transmissões
    - sem sincronização de relógios, slots
 4. simples

 ## MAC protocols

O maior desafio é quando há um meio de difusão: um meio partilhado em que qualquer estação pode aceder ao meio e uma vez acedendo ao meio, todas as outras têm a possibilidade de ouvir e receber a trama que está a ser transmitida.

__Colisão__ - se um nodo recebe 2 ou mais sinais ao mesmo tempo. As trama vão ser recebidas com erro. Para regulamentar este acesso, utilizam-se protocolos de acesso multiplo. Uma regra base é que este controlo siga feito usando o próprio canal de comunicação. "Inbad channel"

__Taxonomia__ - esquema de classificação dos protocolos. 3 classes génericas:
    - *Channel Partition* - canal é dividido em pequenas unidades. Os protocolos alocam pequenos traços de capacidade da ligação para uso exclusivo de um determinado nodo.
    - *Random acess* -  canal não é dividido e, não sendo dividido, há a possibilidade de ocorrem colisões. Vai haver uma forma de recuperar dessas colisões.
    - *Taking turns* - passagem de "tokens" de uns nodos para outros.

### Channel Partition

__TDMA__: Método livre de contentação. A capacidade do canal é, numa primeira estância, dividida em "time frames", e cada time frame dividido em slots. O acesso vai sendo feito dentro de cada time frame. Cada estação obtém a um time slot fixo, que normalmente corresponde ao tempo de transmissão de pacote. Slots que não sejam usados por estações não são reusados por outras estações. Vão para um estado de "idle".

__FDMA__:  O canal é dividido em múltiplas frequencias e cada estação é atribuida uma frequência.

A escolha entre *TDMA* e *FDMA* depende do contexto da aplicação e das condições da rede.

| TDMA | FDMA |
| --- | --- |
|Existem requisitos estritos para latência e atraso | Onde simplicidade e flexibilidade são mais importantes|
|O canal é suscetível a interferências | Há um grande número de usuários que precisam ser suportados|

### Random Acess

Quando uma estação acede ao meio, tem a capacidade de utilizar toda a capacidade existente para transmitir. Preocupam-se em tentar detetar ou tentar evitar as colisões.

__Slotted ALOHA__: O tempo é dividido em slots de tempo. Cada slot corresponde ao tempo de transmissão de um pacote. Quando uma estação tem um pacote para transmitir, ela transmite no início do próximo slot. Se não houver colisões, a estação pode enviar o próximo pacote no próximo slot. Se houver colisões, a estação retransmite o pacote no próximo slot com probabilidade p, onde p é escolhido de forma a maximizar a eficiência do canal.

__Pure ALOHA__: Não considera slots, logo não tem sincronização. A probabilidade de colisões aumenta uma vez que uma trama enviada em t0 pode colidir com uma trama enviada em t0 - 1 e t0 + 1. Eficiência de 18%.

__CSMA__: Neste método escuta-se o meio antes de começar a transmitir. Para a analogia humana é "Se alguém fala, eu não vou interromper". Pode ocorrer colisões devido ao "delay". Um  nodo B pode começar a transmitir e um nodo D pode começar a transmitir uma vez que aindaa não ouviu o B. Há uma interferencia do sinal vermelho com o sinal amarelo que corrompe a trama.

![CSMA](img/csma.png)

__CSMA/CD (Colision Detection)__: Num meio partilhado *cabelado* é possivel detetar colisões porque a rede que está a transmitir faz sinal simultaneamente a análise ao meio e apercebe-se que o sinal que está a colococar no meio deixa de ser igual aquele que está a transmitir. E, portanto, em redes cabeladas, é facilmente detetada a colisão. Em redes wi-fi não é facil devido ao fading, redes escondidas, etc. Por isso é que se usa o CSMA/CA. Em meios cabelados, as estações quando uma colisão é detetada, as estações reforçam a colisão (geram um ruido para a linha) e abortam a colisão. Depois de abortar, fazem backoff.

### Taking Turns

__Polling__ : O nodo mestre "convida" a os nodos *escravos* a transmitir. Fazer polling ás estações e só depois é que a estação envia dados. Problemas: - Overhead de polling - Latência - Single point of failure (nodo mestre).

__Token passing__: Um token circula na rede e só a estação que tem o token consegue transmitir. Problemas: - Overhead de token - Latência - Single point of failure (token).

## LAN

### MAC Address e ARP

Endereços unicos na rede local. Isto e, so podemos ter acesso a eles se for adajacentes a nossa rede local.

__Endereço IP__ -> muda de acordo com a rede "hospedeira". \
__Endereço MAC__ -> não muda. \
__Protocolo ARP__ permite saber o endereço MAC atrav´es do seu IP.

Se A quer enviar uma trama para B, mas o endereço MAC do B nao esta na tabela ARP do A, A tem de fazer um ARP request, que contem o endereço IP de B. O endereço MAC destino utilizado e o endereço de broadcast. Quando uma trama possui esse endereço, TODOS os sistemas nessa LAN vao processar essa trama. Vao desencapsular, processar o pacote IP, e ver se o seu IP ´e igual ao IP pedido. A maquina com o IP correspondente, vai responder a A com uma primitiva "ARP reply" com o seu endereço MAC. E nessa altura o A pode atualizar com a informaçao recebida.

### Ethernet

A tecnologia LAN com fio "dominante". Foi a primeira tecnologia LAN amplamnete utilizada, pois era simples e barata. Funciona com um unico chip e usa varias sementes. Tambem acompanhou a corrida da velocidade (10Mbps - 40 Gbps).

__Bus__: todos os nos no mesmo dominio de colisao. Podem colidir uns com os outros. Popular ate os anos 90.

__Star__: todos os nos ligados a um switch. Nao ha colisoes. Usado atualmente.

#### Unreliable, Connectionless

__Connectionless__: Nao orientadas a conexao. Basta que sinta um meio em silencio para enviar as tramas, nao ha qualquer negociacao entre MAC de origem e um MAC de destino.

__Unreliable__: Nao ha confirmacoes entre N/C's dizendo se a trama chegaou bem ou nao. Se algo corre mal, as N/C's descartam a trama e depois tentam recuperar de colisao.

## Switches

Equipamento de nivel 2. O switch e capaz de paralelismo, STORE AND FORWARDING das frames. Em situaçoes de contençao, duas tramas a chegar ao switch por portas diferentes destinadas a mesma porta, primeiro comuta uma e depois comuta a outra. Examina o MAC Address da trama que esta a chegar e seletivamente encaminha essa trama por uma ou mais portas de saude. ´E transparente, isto ´e, os hosts nao sabem da presença de switches. Tem a capacidade de aprendizagem, nao precisa de muita configuraçao (apenas a basica necessaria). Permite isolar qualquer transmissoes simultaneas sem colisoes.

### Switches interconectados

Seus switches possíveis podem ser conectados juntos, você pode estar se perguntando como posso me conectar a um host após várias camadas de switches, mas exatamente como foi mencionado anteriormente devido à natureza de autoaprendizagem dos switches.

### Switches vs Routers

Em ambos os casos, eles são armazenados e encaminhados. Os roteadores funcionam com um dispositivo de camada de rede, enquanto os switches funcionam com dispositivos de camada de link. Outra coisa que eles têm em comum é que ambos possuem tabelas de encaminhamento. Enquanto os roteadores calculam as tabelas usando algoritmos de roteamento (endereços IP), os switches aprendem como preencher sua tabela de encaminhamento usando flooding, learning e endereços MAC.
