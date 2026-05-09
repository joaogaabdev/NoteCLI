## Camada Service: onde vive a regra de negócio
[[MOC - Arquitetura de Software]]
Se o Controller é apenas o ponto de entrada, a **camada Service** é o cérebro da aplicação. É aqui que ficam as **regras de negócio**, decisões importantes e fluxos que dão sentido ao sistema. Em uma Layered Architecture bem feita, quase toda a inteligência do software está concentrada nessa camada.

De forma simples, o Service responde perguntas como:

- Posso criar esse usuário?
- Esse pedido é válido?
- O usuário tem permissão para executar essa ação?
- O que acontece depois que um registro é salvo?

O Service **não se preocupa com HTTP**, nem com detalhes de banco de dados. Ele apenas executa regras e coordena chamadas para outras partes do sistema.