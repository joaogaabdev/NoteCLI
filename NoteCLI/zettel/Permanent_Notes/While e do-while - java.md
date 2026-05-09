 #Java 
## Conceito Central

As estruturas `while` e `do-while` são usadas para **repetir um bloco de código enquanto uma condição for verdadeira**. Diferente do `for`, elas são ideais quando **não sabemos previamente** quantas iterações serão necessárias.

> Se o `if` decide, o `while` insiste até dar certo 😄

---

## while

O `while` verifica a condição **antes** de executar o bloco.

### Sintaxe

```java
while (condicao) {

// código executado enquanto condicao == true

}
```

### Exemplo

```java
int contador = 1;

while (contador <= 5) {

System.out.println(contador);

contador++;

}
```

📌 Se a condição começar falsa, o bloco **não executa nenhuma vez**.

---

## Fluxo de Execução do while

1. Avalia a condição
    
2. Se `true`, executa o bloco
    
3. Atualiza variáveis de controle
    
4. Retorna à condição
    

⚠️ Esquecer o passo 3 é o caminho mais curto para um **loop infinito**.

---

## do-while

O `do-while` executa o bloco **ao menos uma vez**, pois a condição é verificada **após** a execução.

### Sintaxe

```java
do {

// código executado ao menos uma vez

} while (condicao);
```

### Exemplo

```java
int numero = 10;

do {

System.out.println(numero);

numero++;

} while (numero < 5);
```

Mesmo com a condição falsa, o código roda uma vez. Sem surpresas, só intenção clara.

---

## Quando usar while vs do-while

|Estrutura|Usar quando|
|---|---|
|`while`|A condição pode ser falsa desde o início|
|`do-while`|O bloco precisa rodar ao menos uma vez|

---

## Casos Comuns de Uso

### Leitura de dados até condição de parada

```java
Scanner sc = new Scanner(System.in);

int opcao = -1;

while (opcao != 0) {

System.out.print("Digite 0 para sair: ");

opcao = sc.nextInt();

}
```

### Validação de entrada

```java
int idade;

while (idade <= 0) {

System.out.println("Idade inválida");

}
```

---

## break e continue

### break

Interrompe o loop imediatamente.

```java
while (true) {

if (condicao) break;

}
```

### continue

Pula para a próxima iteração.

```java
while (contador < 10) {

contador++;

if (contador % 2 == 0) continue;

System.out.println(contador);

}
```

---

## ⚠️ Loop Infinito

```java
while (true) {

// executa para sempre

}
```

✔ Útil para servidores, listeners e sistemas reativos  
❌ Péssimo em exercícios se não houver saída

> Todo loop infinito precisa de uma estratégia de fuga.

---

## 🔹 Boas Práticas

✔ Condição clara e objetiva  
✔ Atualizar variáveis de controle corretamente  
✔ Evitar `while(true)` sem `break` explícito  
✔ Preferir `for` quando o número de iterações é conhecido

---

## 🧠 Comparação Rápida

|   |   |
|---|---|
|Estrutura|Característica|
|`for`|Iterações conhecidas|
|`while`|Iterações indefinidas|
|`do-while`|Executa ao menos uma vez|

---

## 🧩 Relação com Arquitetura

- Loops longos podem indicar:
    
    - Falta de eventos
        
    - Falta de streams
        
    - Lógica procedural excessiva
        

Em sistemas modernos, muitos `while` são substituídos por:

- Event loops
    
- Streams
    
- Observers
    

> Código maduro repete menos e reage mais.