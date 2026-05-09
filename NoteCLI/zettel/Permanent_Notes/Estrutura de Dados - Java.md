#Java, #DSA 
## Ideia Central

Estruturas de dados em Java são **abstrações para organizar, acessar e manipular dados** com diferentes compromissos entre **performance, memória, ordenação e semântica**. O domínio dessas estruturas não é sobre decorar classes, mas **escolher conscientemente o custo certo para cada problema**.

> Engenharia não é saber _usar_ uma estrutura — é saber **por que não usar outra**.

---

## 🧩 Princípio Fundamental

Em Java, estruturas de dados são expostas majoritariamente via **interfaces**, não implementações.

Hierarquia-chave:

- `Iterable`
- `Collection`
    - `List`
    - `Set`
    - `Queue`  
- `Map` (fora de `Collection`)
    

👉 **Sempre programe para a interface**, nunca para a implementação.

---

## 📦 Arrays (Base do Sistema)

### Conceito

- Estrutura **contígua**, tamanho fixo
    
- Acesso por índice O(1)
    
- Base de quase todas as outras estruturas
    

Sintaxe:
```java
int[] nums = new int[10];
```

### Características

- Muito rápidos
    
- Não crescem dinamicamente
    
- Sem operações semânticas (inserir, remover)
    

Use quando:

- Tamanho é conhecido
    
- Performance extrema é necessária
    

---

## 📜 List (Sequência Ordenada)

### Ideia

Coleção **ordenada**, permite duplicatas, acesso por índice.

---

### ArrayList

- Internamente: array dinâmico
    
- Acesso por índice: O(1)
    
- Inserção/remoção no meio: O(n)
    

Use quando:

- Leitura é mais frequente que escrita
    
- Acesso aleatório é importante
    

---

### LinkedList

- Lista duplamente encadeada
    
- Inserção/remoção nas extremidades: O(1)
    
- Acesso por índice: O(n)
    

⚠ Geralmente pior que `ArrayList` na prática (cache miss).

Use quando:

- Há muitas inserções/remoções no início/fim
    

---

## 🧮 Set (Conjunto)

### Ideia

Coleção **sem elementos duplicados**.

---

### HashSet

- Baseado em hash
    
- Ordem não garantida
    
- Operações básicas: O(1) médio
    

Use quando:

- Unicidade importa
    
- Ordem não importa
    

---

### LinkedHashSet

- Mantém ordem de inserção
    
- Leve custo adicional
    

Use quando:

- Precisa de unicidade + previsibilidade
    

---

### TreeSet

- Baseado em árvore balanceada (Red-Black)
    
- Ordenado
    
- Operações: O(log n)
    

Use quando:

- Ordem natural ou customizada é requisito
    

---

## 🗂 Map (Chave → Valor)

### Ideia

Estrutura de **associação**, não faz parte de `Collection`.

---

### HashMap

- Sem ordem garantida
    
- Busca/inserção: O(1) médio
    
- Aceita `null` (1 chave)
    

Use quando:

- Performance é prioridade
    

---

### LinkedHashMap

- Mantém ordem de inserção ou acesso
    

Use quando:

- Precisa de cache (LRU)
    

---

### TreeMap

- Ordenado por chave
    
- O(log n)
    

Use quando:

- Queries ordenadas importam
    

---

### Hashtable (Legado)

- Sincronizado
    
- Evite em código moderno
    

---

## 🚦 Queue / Deque

### Queue

FIFO — primeiro a entrar, primeiro a sair.

---

### PriorityQueue

- Heap
    
- Remove sempre o menor/maior
    
- O(log n)
    

Use quando:

- Prioridade importa mais que ordem
    

---

### Deque (Double-ended queue)

Implementação comum: `ArrayDeque`

- Inserção/remoção nas duas pontas
    
- Mais rápida que `Stack`
    

---

## 🧱 Stack (Pilha)

- LIFO
    
- Classe `Stack` é legada
    

Use:

```java
Deque<Integer> stack = new ArrayDeque<>();
```

---

## 🔐 Estruturas Imutáveis

```java
List<Integer> l = List.of(1, 2, 3);
```

- Seguras
    
- Thread-safe
    
- Evitam efeitos colaterais
    

Use quando:

- Dados não devem mudar
    

---

## 🧵 Estruturas Concorrentes (`java.util.concurrent`)

- `ConcurrentHashMap`
- `CopyOnWriteArrayList`
- `BlockingQueue`
    

Use quando:

- Múltiplas threads acessam os dados
    
- Lock explícito seria custoso
    

---

## ⚙ Performance (Visão Sistêmica)

|Estrutura|Acesso|Inserção|Ordenação|
|---|---|---|---|
|ArrayList|O(1)|O(n)|✔|
|LinkedList|O(n)|O(1)|✔|
|HashSet|—|O(1)|❌|
|TreeSet|—|O(log n)|✔|
|HashMap|O(1)|O(1)|❌|
|TreeMap|O(log n)|O(log n)|✔|

---

## ❌ Anti-Padrões

- Usar `List` quando `Set` representa melhor o domínio
    
- Usar `TreeMap` sem necessidade de ordenação
    
- Usar `Stack`
    
- Ignorar custo de ordenação
    

---

## 🧠 Heurística de Escolha

Perguntas-chave:

1. Preciso de ordem?
    
2. Preciso de unicidade?
    
3. Preciso de acesso por índice?
    
4. Preciso de concorrência?
    

A estrutura certa **emerge das respostas**, não da preferência pessoal.

---

## 📌 Princípio Final

> Estruturas de dados são **decisões arquiteturais disfarçadas de código**.

Escolher bem reduz bugs, melhora performance e simplifica o sistema.