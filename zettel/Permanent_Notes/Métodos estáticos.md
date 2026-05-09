#Java 
## Métodos Estáticos em Java

### Conceito central

Um **método estático** em Java pertence à **classe**, não às instâncias dela.  
Ele existe independentemente de objetos e pode ser chamado sem `new`.

> **Ideia-chave:**  
> **Objeto é comportamento + estado**.  
> **Método estático é só comportamento.**

---

### Definição técnica

Um método estático é declarado com a palavra-chave `static` e é carregado na **Method Area** da JVM no momento em que a classe é carregada.

```java
public class MathUtils {    
	public static int somar(int a, int b) {
           return a + b;    
	} 
}
```
Uso:

```java
int resultado = MathUtils.somar(2, 3);
```

Nenhuma instância foi criada. Zero objetos. Economia de memória e semântica clara.

---

### Características fundamentais

1. **Não depende de estado de instância**
    
    - Não acessa atributos não estáticos
    - Não pode usar `this` ou `super`
        
2. **Pode acessar apenas membros estáticos**
    
```java
    static int contador;  static void incrementar() {     
	    contador++;
    }
```
    
3. **É resolvido em tempo de compilação**
    
    - Não participa de polimorfismo
    - Não sofre override (apenas _method hiding_)
        

---

### Métodos estáticos ≠ Métodos de instância

|Aspecto|Estático|Instância|
|---|---|---|
|Pertence a|Classe|Objeto|
|Usa `this`|❌|✅|
|Polimorfismo|❌|✅|
|Estado interno|❌|✅|
|Uso típico|Utilitário|Comportamento de domínio|

> **Regra mental:**  
> Se o método precisa de identidade → **não é estático**.

---

### Casos de uso corretos

#### 1. Métodos utilitários

Clássico e legítimo.

```java
Math.max(10, 20); Integer.parseInt("42"); Collections.sort(lista);
```

✔ Não dependem de estado  
✔ Funções puras  
✔ Reutilizáveis

---

#### 2. Fábricas (Factory Methods)

Muito usado em APIs modernas.

```java
public class Usuario {

    private Usuario(String nome) {
               this.nome = nome;
    }      
    public static Usuario criarAdmin(String nome) {
             return new Usuario(nome);
    } 
}
```

✔ Encapsula regras de criação  
✔ Evita construtores confusos  
✔ Nome expressivo

---

#### 3. Entry point da aplicação

```java
public static void main(String[] args)
```

A JVM não cria objetos por conta própria. Ela chama um método **estático** por design.

---

### Limitações e armadilhas ⚠️

#### ❌ Não usar para lógica de domínio

```java
public static boolean aprovarEmprestimo(Cliente c) { ... }
```

_Cheiro de código procedural._  
Se existe um `Cliente`, ele deveria saber algo sobre isso.

---

#### ❌ Dificulta testes e extensibilidade

- Não pode ser mockado facilmente
- Não participa de injeção de dependência
- Aumenta acoplamento
    

> **Design insight:**  
> Quanto mais `static`, menos orientado a objetos você está sendo.

---

### Relação com princípios de software

- **SRP (SOLID)**  
    Métodos estáticos costumam virar “Deus utilitário” se não houver cuidado.
- **OCP**  
    Não podem ser sobrescritos → fechados para extensão.
- **DDD**  
    Usáveis apenas para _Domain Services_ sem estado (com parcimônia).
    

---

### Modelo mental (analogia)

- **Método de instância:**  
    “O carro acelera”
- **Método estático:**  
    “Converter km/h para m/s”
    

Um **faz**, o outro **transforma**.