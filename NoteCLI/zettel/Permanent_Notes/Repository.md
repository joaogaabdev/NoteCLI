## Camada Repository: isolando o acesso a dados
[[MOC - Arquitetura de Software]]
A **camada Repository** é a responsável por tudo que envolve **acesso a dados**. Banco de dados, ORM, queries SQL, chamadas para APIs externas ou qualquer outra forma de persistência devem ficar aqui. A grande ideia é simples: **o restante da aplicação não precisa saber de onde os dados vêm**.