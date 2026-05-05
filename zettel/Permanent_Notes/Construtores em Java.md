#Java [[MOC - Orientação à Objetos]]
## Ideia central

**Construtores são o mecanismo pelo qual um objeto nasce em um estado válido.**  
Eles não “criam” objetos — isso é papel da JVM — mas **definem como o objeto deve começar a existir**.

> Em Java, um objeto mal inicializado é um bug em potencial com CPF e RG.

---

## O que é um construtor

Um **construtor** é um método especial que:

- Tem **o mesmo nome da classe**
- **Não possui tipo de retorno**
- É executado **automaticamente** no momento da instanciação (`new`)
- Serve para **inicializar o estado interno do objeto**
    

```java
public class User {

	private String name;
	
	public User(String name) {
	    this.name = name;     
	} 
}
```

Aqui, o construtor garante que **não exista um `User` sem nome**.

---

## Papel conceitual do construtor

No modelo mental orientado a objetos:

- Classe → **molde**
- Objeto → **instância viva**
- Construtor → **rito de nascimento**
    

O construtor impõe **invariantes**: regras que **devem ser verdadeiras** para todo objeto daquela classe.

Exemplo de invariante:

- Um `Account` **nunca** nasce com saldo negativo
- Um `Student` **sempre** nasce com matrícula
    

---

## Construtor padrão (default)

Se **nenhum construtor for declarado**, o compilador cria automaticamente:

```java
public ClassName() {}
```

⚠️ Porém:

- Se você declarar **qualquer construtor**, o default **não é mais gerado**
- Isso força quem usa a classe a respeitar seu contrato de criação
    

---

## Construtores parametrizados

Permitem controlar o estado inicial:

```java
public class Account {

    private double balance;
    
    public Account(double initialBalance) {
        if (initialBalance < 0) {
        throw new IllegalArgumentException("Saldo inicial inválido");
        } this.balance = initialBalance;     
    } 
}
```

Aqui o construtor atua como:

- **Guardião do domínio**
- **Firewall contra estados inválidos**
    

---

## Sobrecarga de construtores

Uma classe pode ter **múltiplos construtores**, desde que tenham assinaturas diferentes.
```java

public class User {
    private String name;
    private boolean active;   
    
	public User(String name) {
		this(name, true);     
	}      
	public User(String name, boolean active) {
	    this.name = name;
	    this.active = active;  
	} 
}
```

---

## Uso de `this()`

`this()` chama **outro construtor da mesma classe**.

Regras importantes:

- Deve ser a **primeira instrução**
- Evita duplicação de lógica
- Centraliza invariantes
    

> Um bom construtor é DRY. Um mau construtor vira um cemitério de bugs.

---

## Ordem de execução

Ao criar um objeto:

1. Alocação de memória (heap)
2. Inicialização com valores padrão
3. Execução do construtor
4. Objeto pronto para uso
    

Se houver herança:

```java
Construtor da superclasse 
		   ↓ 
Construtor da subclasse
```

---

## Construtores e herança

- Construtores **não são herdados**
- A subclasse **sempre chama** um construtor da superclasse (`super()`)
    

```java
public class PremiumAccount extends Account {     
	public PremiumAccount(double balance) {
	    super(balance);     
	} 
}
```

Se `super()` não for explícito, o compilador tenta chamar o construtor padrão da superclasse.

---

## Construtores privados

Usados para:

- **Singleton**
- **Factory Method**
- Classes utilitárias
    

```java
public class MathUtils {
	private MathUtils() {}
}
```

Aqui o construtor **impede instanciação**.

---

## Relação com SOLID

- **SRP**: o construtor deve cuidar apenas da **inicialização**
- **OCP**: invariantes bem definidas reduzem modificações futuras
- **DIP**: construtores são o ponto ideal para **injeção de dependências**
    

---

## Erros comuns

- Construtores longos demais
- Lógica de negócio dentro do construtor 
- Muitos parâmetros (code smell → _telescoping constructor_)
- Inicialização condicional confusa
    

Sinal clássico:

```java
public Service(A a, B b, C c, D d, E e, F f) { ... }
```

Cheiro forte de necessidade de **Builder Pattern**