#Java 
## Conceito Central

Estruturas condicionais permitem **tomar decisões** no fluxo do programa com base em expressões booleanas. Em Java, as principais são `if`, `else if`, `else` e o **operador ternário** (`? :`).

> Se código fosse vida real: `if` é escolher, `else` é assumir as consequências 😄

---

## if

Executa um bloco **somente se** a condição for verdadeira.

```java
if (condicao) {

// código executado se condicao == true

}
```

### Exemplo

```java
int idade = 18;

if (idade >= 18) {

System.out.println("Maior de idade");

}
```

---

## 🔹 if + else

Executa **um bloco ou outro**, nunca ambos.

```java
if (condicao) {

// true

} else {

// false

}
```

### Exemplo

```java
int nota = 6;

if (nota >= 7) {

System.out.println("Aprovado");

} else {

System.out.println("Reprovado");

}
```

---

##  if + else if + else

Usado quando há **múltiplas condições** mutuamente exclusivas.

```java
if (condicao1) {  

} else if (condicao2) {

} else {

}

```
### Exemplo

```java
int hora = 14;

if (hora < 12) {

System.out.println("Bom dia");

} else if (hora < 18) {

System.out.println("Boa tarde");

} else {

System.out.println("Boa noite");

}
```

📌 **Atenção:** a primeira condição verdadeira encerra a verificação.

---

## 🔹 Boas Práticas com if/else

✔ Condições claras e simples  
✔ Evitar `if` aninhado excessivo ("escada do sofrimento")  
✔ Usar chaves `{}` sempre, mesmo em blocos de uma linha

 **Evitar:

```java
if (x > 0)

if (y > 0)

System.out.println("Perigo");
```

---

## 🔸 Operador Ternário (`? :`)

Forma **compacta** de um `if/else` simples.

### Sintaxe

```java
condicao ? valorSeTrue : valorSeFalse;
```

### Exemplo

```java
int idade = 20;

String status = idade >= 18 ? "Maior" : "Menor";

Equivalente a:

String status;

if (idade >= 18) {

status = "Maior";

} else {

status = "Menor";

}
```

---

## 🔸 Quando usar Ternário

✔ Atribuições simples  
✔ Retornos diretos  
✔ Código mais legível

return saldo >= 0 ? "Saldo OK" : "Saldo negativo";

❌ Evitar ternário quando:

- Há lógica complexa
    
- Mais de uma ação por condição
    
- Fica difícil de ler (código não é charada)
    

---

## ⚠️ Ternário Aninhado (Cuidado)

String resultado = nota >= 7 ? "Aprovado" : nota >= 5 ? "Recuperação" : "Reprovado";

Funciona, mas **cobra juros de manutenção**. Prefira `if/else` nesses casos.

---

## 🧠 Comparação Rápida

|Estrutura|Usar quando|
|---|---|
|`if`|Uma condição simples|
|`if/else`|Dois caminhos|
|`if/else if/else`|Múltiplas decisões|
|Ternário|Atribuição simples|

---

## 🧩 Relação com Arquitetura

- Condicional em excesso pode indicar **falta de polimorfismo**
    
- Em sistemas maiores, regras complexas migram para:
    
    - Strategy Pattern
        
    - State Pattern
        
    - Regras de negócio isoladas
        

> Bom código decide bem. Código excelente quase não precisa decidir.