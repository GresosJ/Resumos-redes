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

"O caminho origem-destino se comporta muito semlhantemente com um circuito telefônico"

- Desempenha sabiamente
- Ações de rede ao longo do caminho da origem ao destino

#### VC implementation

Consiste em:

 1. Caminho origem para o destino;
 2. Números VC, um número para cada link no caminho;
 3. Entradas em tabelas de encaminhamento em roteadores ao longo do caminho;

O pacote pertence ao VC que carrega o número do VC (não o endereço de destino). O número do VC pode ser alterado em cada link.

