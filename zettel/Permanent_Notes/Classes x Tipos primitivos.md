#Java 
### Ideia central

Em Java, **tipos primitivos** e **classes** representam dois paradigmas distintos:  
**dados puros** vs **dados + comportamento**.

---

### Tipos Primitivos

São os blocos fundamentais da linguagem.

|Tipo|Tamanho|
|---|---|
|`byte`|8 bits|
|`short`|16 bits|
|`int`|32 bits|
|`long`|64 bits|
|`float`|32 bits|
|`double`|64 bits|
|`char`|16 bits|
|`boolean`|JVM-dependent|

**Características:**

- Não são objetos
- Armazenam valores diretamente
- Geralmente vivem na stack
- Melhor performance
- Não possuem métodos
    

**Não aceitam `null`**

---

### Classes (Tipos por Referência)

Classes definem **objetos**, que encapsulam **estado + comportamento**.

**Características:**

- Criadas com `new`
- Armazenadas no heap
- Acessadas por referência
- Podem ter métodos, construtores, herança, interfaces
- Podem ser `null`
    

`class User {     String name; }`

📌 Variável → referência  
📌 Objeto → heap

---

### Wrapper Classes

Java cria uma ponte entre os dois mundos:

|Primitivo|Wrapper|
|---|---|
|`int`|`Integer`|
|`double`|`Double`|
|`boolean`|`Boolean`|

Usadas quando:

- Trabalhando com Collections (`List<Integer>`)
- Precisando de `null`
- Usando Generics
    

📌 **Autoboxing / Unboxing** resolve, mas cobra juros em performance.