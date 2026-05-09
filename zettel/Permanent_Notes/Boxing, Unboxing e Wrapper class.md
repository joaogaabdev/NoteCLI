Referees: #Java 
Em Java existem **tipos primitivos** (`int`, `double`, `boolean`, etc.) e **tipos objeto**.

As **Wrapper Classes** são classes que **encapsulam tipos primitivos em objetos**.

Isso permite que valores primitivos possam ser usados em **contextos que exigem objetos**, como coleções, generics e APIs orientadas a objetos.


| Tipo primitivo | Wrapper Class |
| -------------- | ------------- |
| ``byte``       | ``Byte``      |
| ``short``      | ``Short``     |
| ``int``        | ``Integer``   |
| ``long``       | ``Long``      |
| ``float``      | ``Float``     |
| ``double``     | ``Double``    |
| ``char``       | ``Char``      |
| ``boolean``    | ``Boolean``   |

## Conceito de Boxing
**Boxing** é o processo de transformar um tipo primitivo em um objeto wrapper.
Exemplo:
```java
int -> Integer
```

# Conceito de Unboxing

**Unboxing** é o processo inverso:  
converter um **wrapper em tipo primitivo**.
Exemplo:
```java
Integer -> int
```

# Por que Wrapper Classes existem?

Java tem uma regra estrutural importante:

**Coleções trabalham apenas com objetos, não com tipos primitivos.**
Por isso wrappers são necessários.
