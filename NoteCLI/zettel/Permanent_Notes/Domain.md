## Camada de Domínio: quando e por que ela existe
[[MOC - Arquitetura de Software]]
A **Camada de Domínio** é onde ficam os **conceitos centrais do negócio** da aplicação. Nem todo projeto precisa de uma camada de domínio explícita, mas quando o sistema começa a crescer, ela se torna extremamente valiosa.

Diferente do Service, que orquestra regras e fluxos, o Domínio representa **o que o sistema é**, não **o que ele faz**. Aqui moram entidades, regras fundamentais e comportamentos que fazem parte do coração do negócio.

Em projetos simples, o domínio pode ser apenas um conjunto de interfaces ou classes básicas. Em sistemas mais complexos, ele se aproxima bastante de conceitos do **[Domain-Driven Design (DDD)](https://culturadev.com.br/o-que-e-ddd-domain-driven-design/)**.

### O que normalmente fica na Camada de Domínio?

Alguns exemplos comuns:

- Entidades (User, Order, Product)
- Value Objects (Email, CPF, Money)
- Interfaces de contratos (ex: UserRepository)
- Regras que não dependem de infraestrutura