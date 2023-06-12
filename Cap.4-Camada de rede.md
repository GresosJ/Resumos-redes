# Capitulo 4 - Camada de Rede

 1. Introduction
 2. Virtual Circuit and Datagram Networks
 3. IP: Internet Protocol
 4. Routing Algorithms

## Network Layer

- Transponha o segmento da origem para o host de destino;
- O lado que envia encapsula os segmentos nos datagramas;
- O destino entrega segmentos para a camada de transporte;
- Protocolos da camada de rede em cada host, router;
- Router examina cabeçalhos fiéis em todos os datagramas IP que passam por ele;

#### Duas funções chaves do network-layer

- __Forwarding__ - Move pacotes do input do router para o output do router;
- __Routing__ - Determina a rota que os pacotes iram fazer deste da origem ate o destino;

## Virtual Circuit

A rede fornece serviço de conexão de camada de rede

*"O caminho origem-destino se comporta muito semlhantemente com um circuito telefônico"*

- Desempenha sabiamente
- Ações de rede ao longo do caminho da origem ao destino

__VC implementation__

Consiste em:

 1. Caminho origem para o destino;
 2. Números VC, um número para cada link no caminho;
 3. Entradas em tabelas de encaminhamento em roteadores ao longo do caminho;

O pacote pertence ao VC que carrega o número do VC (não o endereço de destino). O número do VC pode ser alterado em cada link.

__Signalling protocols__

São usados para configurar, manter e desmontar VC. Eles são usados em redes ATM ou frame-relay. Isso não é usado na Internet de hoje.

__Datagram networks__

Estes não precisam de nenhuma chamada de configuração na camada de rede. Os roteadores não têm nenhum estado para duvidar das conexões de ponta a ponta (sem conceito de nível de rede de "conexão"). Os pacotes são usaando o endereço do host de destino.

__Tabelas de encaminhamento__

IP pega na rota que fizer match mais longo. Exemplo:

Destination Address Range  | Link interface
-------------------------- | --------------
110010000001011100010....... | 0
110010000001011100011000.... | 2
110010000001011100011....... | 3
otherwise | 3

**DA** : 110010000001011100011000*111010100001* 
**DA** : 110010000001011100011000*100010101010* *WHICH INTERFACE?*

O primeiro exemplo corresponde á interface 2 e o segundo exemplo corresponde á interface 1, apesar de também dar match na interface 2.

### Datagram or VC network: Porque?

|  Internet Datagram| ATM (VC) |
|:---:|:---:|
|  Troca de dados entre computadores | Evoluiu da telefonia  |
|  Muitos tipos de link | Conversação humana, tempo restrito, requisitos de confiabilidade |
|  End systems "inteligentes" (computadores) | End systems "burros" |
