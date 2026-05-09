
## Ideia Central

Arquitetura em camadas é um estilo arquitetural que organiza o sistema em **níveis de responsabilidade bem definidos**, onde cada camada possui um papel específico e se comunica apenas com camadas adjacentes.

De forma simples, a Layered Architecture costuma separar o sistema em camadas como **[[Controller]]**, **[[Service]]**, **[[Domain]]** e **[[Repository]]**. Cada camada conversa apenas com a camada “vizinha”, o que deixa o código mais fácil de entender, testar, manter e evoluir.

> Princípio estrutural: **separação de responsabilidades + direção clara de dependência**

De forma clássica, uma aplicação em camadas costuma ser organizada assim:

- **Controller (Camada de Apresentação)**
- **Service (Camada de Aplicação ou Negócio)**
- **Domain (Camada de Domínio)**
- **Repository (Camada de Acesso a Dados)**
### Como as camadas se comunicam?

Um ponto muito importante da Layered Architecture é que **as camadas não se comunicam de qualquer jeito**. Existe um fluxo bem definido:

- O **Controller** recebe a requisição (HTTP, por exemplo)
- O **Controller** chama o **Service**
- O **Service** aplica as regras de negócio
- O **Service** usa o **Repository** para acessar dados
- O resultado sobe o caminho inverso até chegar ao usuário

Ou seja, o Controller **não acessa o banco diretamente**, e o Repository **não sabe nada sobre HTTP ou requisições**. Cada camada conhece apenas o necessário para cumprir sua função.

## Direção das Dependências

Regra de ouro:

> Camadas superiores dependem das inferiores.  
> Camadas inferiores não conhecem as superiores.

Controller → Service → Domain

Nunca:

Domain → Controller ❌

---

## Princípios Relacionados

- 🔹 SRP (Single Responsibility Principle)
    
- 🔹 DIP (Dependency Inversion Principle)
    
- 🔹 Encapsulamento
    
- 🔹 Baixo acoplamento
    
- 🔹 Alta coesão
    

---

## Benefícios

- Clareza estrutural
    
- Testabilidade
    
- Manutenção facilitada
    
- Substituição de infraestrutura (ex: trocar PostgreSQL por Mongo)
    
- Organização mental do sistema
    

---

## Limitações

- Pode gerar código “anêmico” se o domínio não concentrar regras
    
- Pode virar burocrático se exagerado
    
- Não resolve problemas de escalabilidade por si só
    

---

## Quando Usar

Ideal para:

- Sistemas corporativos
    
- CRUDs complexos
    
- Sistemas com regras de negócio bem definidas
    

Não ideal para:

- Microsserviços muito simples
    
- Sistemas orientados a eventos altamente distribuídos