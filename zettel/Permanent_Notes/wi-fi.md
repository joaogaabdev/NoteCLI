## Padrão Wi-fi 802.11

|padrao  | ano de lancamento| frequencia  | largura canal| velocidade max teorica|
|802.11  |       1997       |  2,4 GHz    |   20MHz      |         2 Mbps        |
|802.11a |       1999       |    5 Ghz    |   20Mhz      |         54Mbps        | 
|802.11b |       1999       |  2,4 Ghz    |   20MHz      |         11Mbps        |
|802.11g |       2003       |  2,4 Ghz    |   20MHz      |         54Mbps        |
|802.11n |       2009       |2,4 & 5 Ghz  |   20 & 40Mhz |        600Mbps        |
|802.11ac|       2013       |    5 Ghz    |   20 & 40Mhz |        3,5Gbps        |
|802.11ax|       2019       |2,4, 5 & 6Ghz|   20 & 160Mhz|        9,6Gbps        |
|802.11be|       2024       |2,4, 5 & 6Ghz|   20 & 320Mhz|         30Gbps        |
|_________________________________________________________________________________

## 802.11a (Wi-fi)
* Lancado em 1999
* Primeiro padrao a usar 5Ghz
* Largura de 20Mhz de canal
* Usava OFDM
* Taxas nominais de 54Mbps
* Era mais utilizado por empresas
	* Maior custo
	* Menor interferencia

## 802.11b (Wi-fi 2)
* Lancado em 1999
* Primeiro padrao a usar 5Ghz
* Largura de 20Mhz de canal
* Usava DSSS
* Taxas nominais de 11Mbps
* Amplamente adotado em uso domestico
	* Custo reduzido

## 802.11g (Wi-fi 3)
* Lancado em 2003
* Opera em 2.4Ghz
* Largura de 20Mhz de canal
* Usava OFDM
* Taxas nominais de 54Mbps
* Um dos padroes mais adotados
	* Dimimuia interferencia por uso do OFDM
	* Era compativel com equipamentos 802.11b

## 802.11n (Wi-fi 4)
* Lancado em 2009
* Opera em 2.4Ghz a 40Mhz de canal 
* Utilizacao de OFDM com suporte a MIMO
* Taxas nominais de ate 600Mbps
* Suporte a multiplas antenas (MIMO)
	* Aumento de capacidade
	* Aumento de alcance

## OFDM, DSSS e MIMO + OFDM

###  DSSS (Direct Sequence Spread Spectrum)
* Utilizado no 802.11b
* Espalha o sinal
* Mais lento 
* Maior alcance (2.4Ghz)

### OFDM (Orthogonal Frequency Division Multiplexing)
* Utilizado no 802.11a
* Divide o sinal em partes menores
* Mais rapido 
* Menor alcance (5.8Ghz)

** Inclusao do MIMO ao OFDM **
* Multiple Input, Multiple Output
* Varias antenas trabalhando juntas 
* OFDM = sinal dividido
* MIMO = multipla comunicacao simultanea 

## 802.11ax (Wi-fi 6)
* Solucao para aumento de dispositivos e banda
* 2.4 e 5Ghz
* OFDMA
* MU-MIMO ate 8x8
* 1024-QAM
* TWT - target wake time
* Ate 160Mhz de largura de canal 
* Ate 9.6Gbps (Nominal)

## Wi-Fi 6E (Extended)
* Mesmas tecnologias e padroes do Wifi6
* Inclusao de frequencia de 6Ghz
* Equipamentos chamados de Tri-band
* 14 canais de 80Mhz ou 7 canais de 160Mhz
* Nova frequencia = menos interferencia 
* Mais velocidade e menor distancia 

## 802.11be (Wi-fi 7)
* Nova geracao de Wifi EHT (Extremely High Throughput)
* Suporte a ultra-densidade
* Ate 320Mhz de largura de canal
* MLO - Multi-link Operation (multiplas frequencias)
* Coordinated Multi-user MIMO (Multiplos APs)
* 4096-QAM

## Faixa de 6Ghz e a ANATEL
* De 5.925Mhz a 7.125Mhz - 1200Mhz
* Maio de 2024 - consulta publica
* Limitacao para de 5.925Mhz a 6.425Mhz (500Mhz)
* Reserva de 6.425Mhz a 7.125Mhz para futuro

## TDMA (Time Division Multiple Access)
* Acesso pela divisao do tempo
* Reserva um tempo para cada dispositivo
* Reduz interferencia e colisoes
* Cada vez menos usado para o Wifi

## Beamforming 
* Tecnica de direcionamento de sinal
* Melhor alcance
* Melhor qualidade
* Focar o sinal = menor interferencia

## MIMO & MU-MIMO
* MIMO = Multiple Input, Multiple Output
* MU-MIMO = Multi-user MIMO
* MIMO - Wi-Fi 4
* MU-MIMO - Wi-Fi 5
* Aprimorado no Wi-fi 6 e Wi-fi 7
* 1x1, 2x2 .... 16x16

## MLO - Multi-link Operation
* Multi frequencias - 2.4Ghz, 5Ghz, 6Ghz

## Coordinated Multi-user MIMO
* Uso de varios APs simultaneamente 

## Mesh Real x Mesh Comercial
* Mesh real 
	* Rede inteligente, Dinamica, Auto-ajustavel
	* Malha de comunicacao

* Mesh Comercial
	* Pontos de acessos sincronizados
	* Mesmo ESSID

## SSID x ESSID
* SSID (Service Set Identifier)
	* Nome da rede, ex: Casa WIFI

* ESSID (Extended Service Set Identifier)
	* Conjunto de SSIDs compartilhados
	* Redes Mesh ou sincronizadas

## Componentes de rede Mesh
* Controladores
	* centraliza os ESSIDs
	* Administracao dos canais
	* Gestao dos dispositivos conectados
	* Controlador integrado ou a parte

## Satelites
* conectam-se ao controlador ou outro satelite
* aumentam a cobertura do sinal 
* pode ser conectado via ethernet ou wifi
	* backhaul por WiFi - menor estabilidade e velocidade
	* backhaul por ethernet - melhor estabilidade e velocidade



