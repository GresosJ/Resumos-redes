# Capitulo 4 - Camada de Rede

Modelos de serviço:

__Connectionless__ - Tipicamente uma rede de datagramas que são encaminhadas de forma independentes na rede e sem necessidade de estabelecer um circuito;

__Connection__ - Circuito Virtual. Nível de rede organizado a circuitos virtuais implica que a máquina de origem não possa enviar dados sem estabelecer o circuito. Utiliza o endereço de destino para estabelecer o circuito e depois são criados identificadores de circuito.

## Tabelas de encaminhamento

IP pega na rota que fizer match mais longo. Exemplo:

Destination Address Range  | Link interface
-------------------------- | --------------
110010000001011100010....... | 0
110010000001011100011000.... | 2
110010000001011100011....... | 3
otherwise | 3

**DA** : 110010000001011100011000**111010100001** *WHICH INTERFACE?*

**DA** : 110010000001011100011000**100010101010** *WHICH INTERFACE?*

O primeiro exemplo corresponde á interface 2 e o segundo exemplo corresponde á interface 1, apesar de também dar match na interface 2.