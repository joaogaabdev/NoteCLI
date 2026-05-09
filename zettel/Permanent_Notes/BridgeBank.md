Esse serviço do projeto é responsável pela aplicação bancária, contendo as seguintes funcionalidades:

* Criação de conta
* Depósito
* Saque
* Criação de pagamento Pix
* Poupança
* Integração com a [[BridgeCoin]] por meio de API REST.

Utiliza do framework Spring Boot, em Java e implementa [[Layered Architecture]] em conjunto com [[Vertical Architecture]].
Docker para conteinerização do banco de dados PostgreSQL.
Postman para testes de API REST's e requisições.

Possui 3 classes principais para a regra de negócio da aplicação
* User -> cuida das responsabilidades do usuário
* Account -> cuida das responsabilidades da conta
* Transaction -> cuida das responsabilidades da transferência

### Para a Segurança:
JWT -> Autenticação


