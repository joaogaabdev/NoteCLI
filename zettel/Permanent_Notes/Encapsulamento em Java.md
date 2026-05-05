[[MOC - Orientação à Objetos]], #Java 
# Encapsulamento em Java – Controle de Estado via API de Classe

## Ideia central

Em Java, encapsulamento é a prática de **controlar rigorosamente o acesso ao estado de um objeto** por meio de **modificadores de acesso, métodos públicos e contratos claros**, garantindo integridade, coesão e evolução segura do código.

---

## Encapsulamento em Java não é opcional

Java foi projetada com encapsulamento como **default filosófico**:

- Atributos **não deveriam ser públicos**
- O acesso ao estado deve ocorrer por **métodos**
- O objeto é responsável por **validar e proteger suas próprias regras**
    

> Código Java idiomático assume encapsulamento como regra, não como exceção.

---

## Modificadores de acesso

Java oferece quatro níveis de encapsulamento:

- `private` → visível apenas dentro da própria classe
- _(default)_ → visível apenas no mesmo pacote
- `protected` → visível no pacote e em subclasses
- `public` → visível em qualquer lugar
    

> Quanto mais restrito o modificador, maior o encapsulamento.

---

## Atributos privados como regra

```java
public class Account {
    private double balance;
}
```

Atributos privados:

- Impedem alterações arbitrárias
- Forçam o uso de comportamento
- Protegem invariantes
    

---

## Métodos públicos como fronteira

```java
public void deposit(double amount) {
    if (amount <= 0) {
        throw new IllegalArgumentException("Valor inválido");
    }
    balance += amount;
}
```

O método:

- Valida
- Aplica regra de negócio
- Modifica o estado com segurança
    

> O método é o **porteiro do estado**.

---

## Getters e Setters: uso consciente

```java
public double getBalance() {
    return balance;
}
```

Getters:

- Expondo leitura quando necessário
- Devem ser **questionados**, não automáticos
    

```java
public void setBalance(double balance) {
    this.balance = balance;
}
```

Setters:

- Devem existir **apenas se fizerem sentido no domínio**
- Setters genéricos enfraquecem o encapsulamento
    

> Getter/Setter sem regra = encapsulamento cosmético.

---

## Encapsulamento e JavaBeans

JavaBeans reforça encapsulamento ao exigir:

- Atributos privados
- Acesso via getters/setters padronizados
    

Isso permite:

- Introspecção
- Integração com frameworks
    

Mas:

> JavaBeans não substitui modelagem de domínio.

---

## Imutabilidade como encapsulamento forte

```java
public final class Money {
    private final BigDecimal value;

    public Money(BigDecimal value) {
        this.value = value;
    }

    public Money add(Money other) {
        return new Money(this.value.add(other.value));
    }
}
```

- Sem setters
- Estado nunca muda
- Encapsulamento máximo
    

---

## Encapsulamento e coleções

```java
public List<Item> getItems() {
    return Collections.unmodifiableList(items);
}
```

Nunca expor:

- Coleções mutáveis diretamente
    

> Isso evita que consumidores burlem regras internas.

---

## Encapsulamento vs objetos anêmicos

Anti-padrão comum:

```java
public class User {
    private String name;
    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
}
```

Correção:

```java
public void rename(String newName) {
    validate(newName);
    this.name = newName;
}
```

> Em Java, comportamento deve viver onde o estado vive.

---

## Encapsulamento e SOLID

- **S**: protege a responsabilidade
- **O**: permite evolução sem quebra
- **L**: preserva contratos
- **I**: expõe apenas o necessário
- **D**: depende de abstrações, não de estado
    

Encapsulamento é transversal ao SOLID.

---

## Escala arquitetural

Em Java:

- Classe encapsula estado
- Pacote encapsula contexto
- Módulo encapsula domínio
    

> O `package-private` é uma ferramenta arquitetural poderosa.

---

## Frase de ancoragem

> Em Java, encapsular é transformar estado frágil em comportamento confiável.