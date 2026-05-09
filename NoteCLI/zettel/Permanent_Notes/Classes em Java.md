#Java [[MOC - Orientação à Objetos]]
## Essência

Uma **classe** em Java é a abstração central da linguagem: um molde que define **estado** (atributos), **comportamento** (métodos) e **contratos** (modificadores, interfaces, herança). Pensar em classes é pensar em **modelagem do domínio**, não apenas em código.

> Classe é para o Java o que o projeto arquitetural é para o prédio: antes de levantar paredes, você define a estrutura.

---

## Estrutura básica

```java
public class Usuario {
    private String nome;
    private int idade;

    public Usuario(String nome, int idade) {
        this.nome = nome;
        this.idade = idade;
    }

    public String getNome() {
        return nome;
    }
}
```

### Elementos principais

- **Nome da classe**: substantivo, semântico, em _PascalCase_
    
- **Atributos**: representam o estado
    
- **Métodos**: representam comportamento
    
- **Construtores**: garantem criação válida do objeto
    

---

## Modificadores de classe

- `public` → acessível de qualquer lugar
    
- _(default)_ → acessível apenas no mesmo pacote
    
- `final` → não pode ser herdada
    
- `abstract` → não pode ser instanciada
    

```java
public abstract class Conta {
    protected double saldo;
}
```

---

## Responsabilidade única

Uma classe deve ter **um motivo para mudar**.

❌ Classe Deus:

```text
UsuarioService
- valida CPF
- acessa banco
- envia email
- calcula imposto
```

✅ Classes coesas:

- `Usuario`
    
- `UsuarioRepository`
    
- `EmailService`
    

Classes boas são pequenas, focadas e fáceis de explicar em uma frase.

---

## Relacionamentos entre classes

### Associação

```java
class Pedido {
    private Cliente cliente;
}
```

### Composição (vida dependente)

```java
class Carro {
    private Motor motor = new Motor();
}
```

### Herança (use com cautela)

```java
class ContaPoupanca extends Conta {}
```

> Prefira **composição** a herança. Herança é poderosa — e cobra juros altos.

---

## Classes como contratos

### Implementando interfaces

```java
class PagamentoPix implements MetodoPagamento {
    @Override
    public void pagar() {}
}
```

A classe cumpre um **papel**, não apenas executa código.

---

## Classes imutáveis

Ideais para segurança, concorrência e previsibilidade.

```java
public final class Dinheiro {
    private final BigDecimal valor;

    public Dinheiro(BigDecimal valor) {
        this.valor = valor;
    }
}
```

Características:

- `final`
    
- sem setters
    
- estado definido no construtor
    

---

## Classes e arquitetura

- **Entidades** → regras de negócio
    
- **DTOs** → transporte de dados
    
- **Services** → orquestração
    
- **Repositories** → persistência
    

Misturar papéis gera acoplamento e sofrimento futuro (normalmente às 2h da manhã).

---

## Heurísticas práticas

- Se não consegue nomear a classe, o modelo está errado
    
- Métodos grandes indicam classe inchada
    
- Muitas dependências → sinal de alerta
    
- Classe boa é fácil de testar
    

---

## Síntese

Classes são **decisões de design cristalizadas em código**. Quanto melhor a decisão, menos esforço cognitivo o sistema exige no futuro.

Código passa. Boas classes permanecem.