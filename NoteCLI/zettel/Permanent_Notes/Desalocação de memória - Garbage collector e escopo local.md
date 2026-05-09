#Java 
### Ideia central

Em Java, a desalocação de memória **não é explícita**. Ela emerge da combinação entre **escopo**, **referências** e a atuação do **Garbage Collector (GC)**.  
O desenvolvedor não libera memória — ele **para de apontar para ela**.

---

## Garbage Collector (GC)

### O que é

O **Garbage Collector** é o mecanismo da JVM responsável por **identificar objetos inalcançáveis** e **recuperar a memória do heap** automaticamente.

GC **não remove variáveis**, remove **objetos sem referência válida**.

---

### Como o GC decide o que limpar

O critério é simples e brutalmente eficiente:

> **Um objeto é coletável se não for mais alcançável a partir das GC Roots.**

#### GC Roots incluem:

- Variáveis locais na stack
- Variáveis estáticas
- Threads ativas
- Referências JNI
    
Se não há caminho até o objeto → _bye bye_ 👋

---

### Ciclo de vida de um objeto

1. Objeto criado no heap (`new`)
2. Uma ou mais referências apontam para ele
3. Todas as referências são perdidas ou saem de escopo
4. Objeto se torna **inacessível**
5. GC pode coletá-lo (não imediatamente!)
    
 **GC não é determinístico**

---

## 🎯 Escopo Local e Desalocação

### Escopo local

O **escopo** define **até onde uma variável é visível** no código.

```java
void process() {     
Account acc = new Account();
}
```

- `acc` existe apenas dentro do método
    
- Ao sair do método:
    
    - A variável é removida da **stack**
    - A referência deixa de existir
    - O objeto no heap **torna-se candidato ao GC**
        
 O escopo **não desaloca o heap diretamente**, ele **remove referências**.

---

### Blocos e escopo menor

```java
{  User user = new User(); } // referência removida aqui
```

Escopos menores:

- Facilitam coleta mais rápida
- Reduzem pressão no heap
- Melhoram legibilidade e previsibilidade
    
Menos tempo vivo, menos bagunça. Minimalismo aplicado à memória.

---

## 🧠 Stack vs Heap na desalocação

|Área|Como desaloca|
|---|---|
|Stack|Automática e imediata (fim do escopo)|
|Heap|Indireta, via GC|

A stack é pontual.  
O heap é filosófico: “será que ainda sou necessário?”

---

## Armadilhas clássicas

### Memory Leak em Java (sim, eles existem)

Mesmo com GC, é possível **reter memória sem perceber**.

Exemplos:

- Coleções estáticas que nunca são limpas
- Listeners não removidos
- Caches sem política de expiração
- Referências circulares com GC Roots
    

GC não coleta **o que ainda é referenciado**, mesmo que seja inútil.

---

### `finalize()` (legado e perigoso)

- Não garante execução
- Impacta performance
- **Depreciado**
- Substituído por `try-with-resources` e `AutoCloseable`
    

O GC cuida da memória.  
Você cuida de recursos externos (arquivos, sockets, conexões).

---

## Escopo, GC e Design de Código

Boas práticas:

- Prefira escopos curtos
- Evite variáveis estáticas desnecessárias
- Limpe coleções long-lived
- Use `try-with-resources`
    
- Pense em **tempo de vida**, não apenas em estrutura