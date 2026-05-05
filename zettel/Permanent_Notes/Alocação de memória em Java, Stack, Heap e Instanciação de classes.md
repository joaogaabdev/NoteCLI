#Java 
### Ideia central

Na JVM, **Stack** e **Heap** representam dois modelos distintos de gerenciamento de memória, refletindo **tempo de vida**, **escopo** e **custo de acesso** dos dados.

---

### Stack Memory

A **Stack** é uma estrutura **LIFO (Last In, First Out)** usada para gerenciar a execução dos métodos.

**Características-chave:**

- Cada _thread_ possui sua própria stack
- Alocação e desalocação automáticas
- Extremamente rápida
- Escopo bem definido (método)
    

**Armazena:**

- Variáveis locais
- Tipos primitivos (`int`, `double`, `boolean`, etc.)
- Referências para objetos no heap
- Frames de métodos (call stack)
    

📌 **Tempo de vida**: enquanto o método está em execução  
📌 **Erro típico**: `StackOverflowError` (recursão sem fim — clássico 😅)

---

### Heap Memory

O **Heap** é a área onde vivem os **objetos** e instâncias criadas com `new`.

**Características-chave:**

- Compartilhada entre threads
- Gerenciada pelo Garbage Collector
- Mais flexível, porém mais lenta que a stack
- Pode crescer/diminuir dinamicamente
    

**Armazena:**

- Objetos
- Arrays
- Strings (incluindo o String Pool)
    

📌 **Tempo de vida**: enquanto houver referências válidas  
📌 **Erro típico**: `OutOfMemoryError`

---

### Relação Stack ↔ Heap

`Account acc = new Account();`

- `acc` → referência na **stack**
- `new Account()` → objeto no **heap**
    

A stack aponta, o heap sustenta. Um manda, o outro obedece.