
## Ideia central

Encapsulamento é o **princípio da Orientação a Objetos** que determina que o **estado interno de um objeto não deve ser acessado ou modificado diretamente**, mas apenas por meio de **interfaces controladas**, preservando invariantes e reduzindo acoplamento.

---

## Problema que o encapsulamento resolve

Sem encapsulamento, objetos se tornam:

- Frágeis (qualquer parte do sistema pode corromper seu estado)
- Fortemente acoplados
- Difíceis de manter e evoluir
    

> Um objeto sem encapsulamento é um conjunto de variáveis soltas usando disfarce de classe.

---

## Encapsulamento como fronteira

Encapsular é **definir uma fronteira clara** entre:

- **O que o objeto é** (estado interno)
- **O que o objeto faz** (comportamento exposto)
    

Essa fronteira permite que a implementação interna mude **sem quebrar quem consome o objeto**.

---

## Estado vs comportamento

Encapsulamento desloca o foco de:

> “Quem pode mexer nesse dado?”  
> para  
> “Quais comportamentos fazem sentido sobre esse dado?”

O estado deixa de ser protagonista; o comportamento assume o controle.

---

## Invariantes

Um objeto encapsulado protege suas **regras internas** (invariantes).

Exemplos de invariantes:

- Um saldo bancário não pode ser negativo
- Uma conexão não pode estar ativa e fechada ao mesmo tempo
- Um pedido não pode ser entregue antes de ser pago
    

> Encapsulamento é o guardião das invariantes.

---

## Encapsulamento e acoplamento

Quanto menor o acesso direto ao estado:

- Menor o acoplamento
- Maior a coesão
- Maior a previsibilidade do sistema
    

Encapsulamento transforma dependências de **dados** em dependências de **comportamento**.

---

## Encapsulamento não é esconder tudo

Encapsular não significa:

- Tornar tudo privado indiscriminadamente
- Criar getters e setters automáticos sem regra
    

> Expor dados sem comportamento é **encapsulamento cosmético**.

O que se expõe deve ter **significado semântico**, não apenas acesso técnico.

---

## Relação com outros princípios de OOP

- **Abstração**: define _o que_ é exposto
    
- **Encapsulamento**: controla _como_ isso é acessado
- **Herança**: reutiliza comportamento encapsulado
- **Polimorfismo**: opera sobre contratos, não sobre estados
    

Encapsulamento é a base que sustenta os demais.

---

## Encapsulamento como princípio arquitetural

Em escala maior:

- Classes encapsulam dados
- Módulos encapsulam regras
- Serviços encapsulam capacidades
    

> Arquitetura é encapsulamento aplicado em múltiplos níveis.

---

## Anti‑padrões comuns

- Objetos anêmicos (apenas getters/setters)
- Exposição direta de atributos públicos
- Lógica de negócio fora do objeto que possui o estado
    

Esses anti‑padrões enfraquecem o modelo de domínio.


---

## Frase de ancoragem

> Encapsulamento é a arte de proteger o estado para que o comportamento possa evoluir com segurança.