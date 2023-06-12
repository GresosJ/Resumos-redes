# Capitulo 1 - Introdução

 1. __O que é a internet?__
 2. __Network Edge__
 3. __Network Core__
 4. __Delay, Loss, Throughput in Networks__
 5. __Protocol Layers, service models__
 6. __Network under attack: Security__
 7. __History__

## O que é a internet?

A Internet é constituida por:
    
- Host ou end system pode ser um telemovel, computador, qualquer equipamento ligado á rede;
- Links de comunicação (ligações): fibra otica, cobre, etc.
- Routers e switchers (__Packet Switches__) conduzem e encaminham o tráfego que os utilizadores geram nas apilicações.
- Taxa de transmissão: Largura de banda -> número de bits (informação) que conseguimos transmitir numa dada unidade de tempo (normalmente em segundos).

__Internet__ -> Rede de redes (Network of Nerworks) -> Conjunto de protocolos de comunicação/aplicação. TCP e IP são osprincipais protocolos. TCP assegura a entrega fíavel fim a fim (do utilizador A, origem, ao utilizador B ,final). Redes IP são responsaveis por fazer o encaminhamento dos dados que geramos por o conjunto de redes interligadas.

__Protocolos__ -> Basicamente é um conjunto de regras que regulamentam a comunicação. Essencialmente definem formatos, ordem de mensagens que são recebidas e enviadas entre as entidades e quais são as ações que devem ser tomadas quando as mensagens são enviadas ou recebidas.
    
    EXEMPLO DE UM PROTOCOLO:
        Computador -> TCP connection request  -> Router
        Computador <- TCP connection response <- Router
        Computador -> Get http//www.cesium... -> Router
        Computador <- <FILE>                  <- Router

## Network edge

. Periferia da rede : Host (clientes e servidores);
. Redes de acesso : Rede por cabo, wireless;
. Core de redes : Equipamento de interligação que assegura que o tráfego;

__Multiplexagem no dominio da frequencia__ : diferentes canais a transmitirem frequências diferentes (num canal video, noutro audio, etc.). Os host essencialmente enviam dados. Se tiver uma mensagem de x kBytes, geralmente não é enviado de uma vez para rede. é dividido em pacotes mais pequenos (packets de L bits) que vão ser enviados num link de transmissão R (se houver um erro num desse packet, não é preciso reenviar os x kBytes).

$$
\begin{align}
    \frac{L (bits)}{R (bits/sec)} = PTD 
\end{align}
$$

__Meios fisicos__ : 

- Guiados -> cabos de cobre, coaxial, fibra otica. Fibras são imunes a ruido eletromagnetico (taxa de erro muito inferior), nem causa tanta atenuação como o coaxial por exemplo.
-Não guiados -> atmosfera, sinais radio, etc. O facto do sinal se propagar num meio aberto causa vários problemas.

## Network Core