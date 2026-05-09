O modelo se chama Modelo de Referência ISO OSI (Open Systems Interconnection), pois ele trata da interconexão de sistemas abertos — ou seja, sistemas abertos à comunicação com outros sistemas. Para abreviar, vamos chamá-lo simplesmente de modelo OSI modelo OSI.

O modelo OSI tem sete camadas. Veja, a seguir, um resumo dos princípios aplicados para chegar às sete camadas. 

1. Uma camada deve ser criada onde houver necessidade de outro grau de abstração. 
2. Cada camada deve executar uma função bem definida
3. A função de cada camada deve ser escolhida tendo em vista a definição de protocolos padronizados internacionalmente. 
4. Os limites de camadas devem ser escolhidos para minimizar o fluxo de informações pelas interfaces.
5. O número de camadas deve ser grande o bastante para que funções distintas não precisem ser desnecessariamente colocadas na mesma camada e pequeno o suficiente para que a arquitetura não se torne difícil de controlar.

## 1. Camada Física

A **camada física** trata da transmissão de bits normais por um canal de comunicação. O projeto de rede deve garantir que, quando um lado enviar bit 1, o outro lado o receberá como bit 1, não como bit 0, a quantidade de nanossegundos que um bit deve durar, se a transmissão pode ou não ser realizada simultaneamente nos dois sentidos, a forma como a conexão inicial será estabelecida e de que maneira ela será encerrada quando ambos os lados tiverem terminado, e ainda quantos pinos o conector de rede terá e qual será a finalidade de cada pino. Nessa situação, as questões de projeto lidam em grande parte com interfaces mecânicas, elétricas e de sincronização, e com o meio físico de transmissão que se situa abaixo da **camada física**.

## 2. Camada Enlace de Dados

A principal tarefa da **camada** **enlace de dados** é transformar um canal de transmissão normal em uma linha que pareça livre de erros de transmissão. Para fazer isso, a camada de enlace mascara os erros reais, de modo que a camada de rede não os veja. Isso é executado fazendo com que o transmissor divida os dados de entrada em quadros de dados (que, em geral, têm algumas centenas ou alguns milhares de bytes) e transmita os quadros sequencialmente. Se o serviço for confiável, o receptor confirmará a recepção correta de cada quadro, enviando de volta um **quadro de confirmação**.
Outra questão na camada de enlace de dados é como impedir que um transmissor rápido envie uma quantidade excessiva de dados a um transmissor lento. Normalmente é preciso que haja um algum mecanismo que regule o tráfego para informar ao transmissor quando o receptor pode aceitar mais dados.
As redes de broadcast têm uma questão adicional a ser resolvida na camada de enlace de dados: como controlar o acesso ao canal compartilhado. Uma subcamada especial da camada de enlace de dados, a subcamada de **controle de acesso ao meio**, trata desse problema.

## 3. Camada de Rede

A **camada de rede** controla a operação da sub-rede. Uma questão fundamental de projeto é determinar a maneira como os pacotes são roteados da origem até o destino. As rotas podem se basear em tabelas estáticas, 'amarradas' à rede e raramente alteradas, ou frequentemente podem ser atualizadas de forma automática, para evitar componentes defeituosos. Elas também podem ser determinadas do início de cada conversação, por exemplo, uma sessão de terminal, como um login em uma máquina remota. Por fim, elas podem ser altamente dinâmicas, sendo determinadas para cada pacote, refletindo a carga atual da rede.
Se houver muitos pacotes na sub-rede ao mesmo tempo, eles dividirão o mesmo caminho, formando gargalos. A responsabilidade pelo controle desse congestionamento também pertence à camada de rede, em conjunto com as camadas mais altas, que adaptam a carga imposta sobre a rede. De modo mais geral, a qualidade do serviço fornecido (atraso, tempo em trânsito, instabilidade etc.) também é uma questão da **camada de rede**. Quando um pacote precisa trafegar de uma rede para outra até chegar a seu destino, podem surgir muitos problemas. O endereçamento utilizado pela segunda rede pode ser diferente do que é usado pela primeira. Talvez a segunda rede não aceite o pacote por ele ser muito grande. Os protocolos podem ser diferentes e assim por diante. Cabe à **camada de rede** superar todos esses problemas, a fim de permitir que redes heterogêneas sejam interconectadas. Nas redes de broadcast, o problema de roteamento é simples e, assim, a camada de rede geralmente é estreita, ou mesmo inexistente.

## 4. Camada de Transporte

A função básica da **camada de transporte** é aceitar dados da camada acima dela, dividi-los em unidades menores, se for preciso, repassar essas unidades à camada de rede e garantir que todos os fragmentos chegarão correta mente à outra extremidade. Além do mais, tudo isso deve ser feito com eficiência e de forma que as camadas superiores fiquem isoladas das inevitáveis mudanças na tecnologia de hardware com o passar do tempo.
A **camada de transporte** também determina que tipo de serviço deve ser fornecido à **camada de sessão** e por fim, aos usuários da rede. O tipo mais popular de conexão de transporte é um canal ponto a ponto livre de erros que entrega mensagens ou bytes na ordem em que eles foram enviados. No entanto, outros possíveis tipos de serviço de transporte são as mensagens isoladas sem nenhuma garantia relativa à ordem de entrega e à propagação de mensagens para múltiplos destinos. O tipo de serviço é determinado quando a conexão é estabelecida. (Observe que é impossível conseguir um canal livre de erros; o que as pessoas realmente entendem por essa expressão é que a taxa de erros é baixa o suficiente para ser ignorada na prática.)
A camada de transporte é uma verdadeira camada de ponta a ponta, que liga a origem ao destino. Em outras palavras, um programa na máquina de origem mantém uma conversação com um programa semelhante instalado na máquina de destino, utilizando os cabeçalhos de mensagens e as mensagens de controle.
Nas camadas inferiores, os protocolos são trocados entre cada uma das máquinas e seus vizinhos imediatos, e não entre as máquinas de ori gem e de destino, que podem estar separadas por muitos roteadores. A diferença entre as camadas 1 a 3, que são encadeadas, e as camadas 4 a 7, que são camadas de ponta a ponta, é ilustrada na Figura 1.17.

![[Pasted image 20251206001710.png]]

## 5. Camada de Sessão

A **camada de sessão** permite que os usuários em diferentes máquinas estabeleçam de comunicação entre eles. Uma sessão oferece diversos serviços, inclusive o controle de diálogo (mantendo o controle de quem deve transmitir em cada momento), o gerenciamento de tokens (impedindo que duas partes tentem executar a mesma operação crítica ao mesmo tempo) e a sincronização (realizando a verificação periódica de longas transmissões para permitir que elas continuem a partir do ponto em que estavam ao ocorrer uma falha e a subsequente reparação

## 6. Camada de Apresentação

Diferente das camadas mais baixas, que se preocupam principalmente com a movimentação de bits, a **camada de apresentação** camada de apresentação está relacionada à sintaxe e à semântica das informações transmitidas. Para tornar possível a comunicação entre computadores com diferentes representações
internas dos dados, as estruturas de dados a serem trocadas podem ser definidas de maneira abstrata, com uma codificação padrão que será usada durante a conexão. A **camada de apresentação** gerencia essas estruturas de dados abstratas e permite a definição e o intercâmbio de estruturas de dados de nível mais alto (por exemplo, registros bancários).

## 7. Camada de Aplicação

A **camada de aplicação** contém uma série de protocolos comumente necessários para os usuários. Um protocolo de aplicação amplamente utilizado é o HTTP (HyperText Transfer Protocol), que constitui a base da World Wide Web. Quando um navegador deseja uma página Web, ele envia o nome da página desejada ao servidor que hospeda a página, utilizando o HTTP. O servidor, então, transmite a página ao navegador. Outros protocolos de aplicação são usados para transferências de arquivos, correio eletrônico e transmissão de notícias pela rede.