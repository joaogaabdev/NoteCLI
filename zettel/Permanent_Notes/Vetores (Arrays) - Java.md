#Java, #DSA 
### Ideia central

Em Java, **vetores (arrays)** são estruturas de dados **lineares, homogêneas e de tamanho fixo**, usadas para armazenar múltiplos valores do **mesmo tipo** em posições contíguas de memória lógica, acessadas por **índice**.

> Pense no array como um **prédio numerado**: cada apartamento (índice) guarda exatamente um morador (valor), e o prédio não cresce depois de construído.

---

### Definição técnica

Um array em Java é um **objeto** que:

- Armazena elementos do mesmo tipo
- Possui tamanho imutável após a criação
- É indexado a partir do **zero**
- Vive na **Heap**
- Possui acesso direto (O(1)) aos elementos
    

```java
 int[] numeros = new int[5];
````

---

### Estrutura mental

```java
índice:   0   1   2   3   4 valor:   10  20  30  40  50
```


---

### Declaração e inicialização

```java
int[] a = new int[3];           // valores padrão: 0 
int[] b = {1, 2, 3};            // inicialização direta 
String[] nomes = new String[2]; // valores padrão: null
````
Valores padrão:

- `int`, `double`, etc → `0`
    
- `boolean` → `false`
    
- Objetos → `null`

   

---

### Acesso e modificação

`numeros[0] = 10; int x = numeros[0];`

- Índices inválidos geram `ArrayIndexOutOfBoundsException`
    
- O compilador confia em você. A JVM… nem tanto 😄
    

---

### Percorrendo vetores

**For tradicional**

```java
for (int i = 0; i < numeros.length; i++) {     System.out.println(numeros[i]); 
}
````

**For-each**

```java
for (int n : numeros) {     
System.out.println(n);
}
```

> `length` é **atributo**, não método. Arrays são simples, diretos e sem frescura.

---

### Arrays como objetos

Mesmo sendo estruturas básicas, arrays em Java:

- São **objetos**
    
- Possuem identidade (referência)
    
- São passados por **referência**
    

```java
int[] a = {1, 2, 3}; int[] b = a; b[0] = 99; // afeta 'a'`
````

---

### Arrays e memória

- Referência do array → **Stack**
- Conteúdo do array → **Heap**
- Tipos primitivos ficam dentro do array
- Objetos → referências dentro do array
---

### Limitações dos vetores

- ❌ Tamanho fixo
- ❌ Inserção e remoção custosas
- ❌ Pouco flexível para crescimento dinâmico
    

Por isso, na prática, arrays:

- São base para estruturas mais complexas
- Servem como **fundação** para `ArrayList`, `HashMap`, etc.
    

---

### Vetores vs ArrayList

|Característica|Array|ArrayList|
|---|---|---|
|Tamanho|Fixo|Dinâmico|
|Performance|Alta|Leve overhead|
|Flexibilidade|Baixa|Alta|
|API rica|Não|Sim|

> Array é o **motor**, ArrayList é o **carro completo**.

---

### Quando usar vetores

- Estruturas simples e de tamanho conhecido
- Código de baixo nível
- Performance crítica
- Base para implementação de algoritmos e estruturas
    

---

