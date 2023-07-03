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