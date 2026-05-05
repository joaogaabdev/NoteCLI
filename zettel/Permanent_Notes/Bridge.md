---
Nome do Projeto: Ecossistema Bridge
Status: Futuro
Backend: Java
Frontend: React
Framework: Spring boot
Objetivo: Criar um ecossistema financeiro
Documentação de API: Swagger
Docker: PostgreSQL
Teste de Request: Postman
---
## Resumo

Ecossistema financeiro para acompanhar todo o ciclo de pagamento, de banco a lojista.

* # Banco - [[BridgeBank]]
	Funcionalidades:
	* Criação de contas
	* Autenticação - oAuth
	* Transações
	* Depósitos
	* Transferências
	* Integração com [[BridgeCoin]] - moeda
	
* # Gateway de pagamentos - [[BridgePay]]
	Funcionalidades: 
	* Integração com [[BridgeCoin]] - moeda, verifica e valida a transação de cada pagamento entre o ecommerce e o banco
	
* # Moeda - [[BridgeCoin]]
	Funcionalidades:
	Criação e manutenção de uma moeda.
	Observação: A moeda será uma API com um uma quantia fixa de 1000 unidades de moeda, sempre que for depositado uma quantidade de [[BridgeCoin]] em uma conta no [[BridgePay]], deverá ser debitado do "estoque" da API.
	
* # Sistema de logs de transação da moeda - [[PayView]]  
	Funcionalidades: 
	* Sistema de monitoramento dos logs de cada transação
	
* # Ecommerce - [[BridgeStore]]
	Funcionalidades:
	* Criação de produtos
	* Autenticação
	* Métodos de pagamento
	* Integração com [[BridgeCoin]] - moeda

