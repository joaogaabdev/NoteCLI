#Java 
## Ideia central

Em Java, **String é imutável**. Toda manipulação gera um **novo objeto na memória**. Esse detalhe pequeno explica metade dos bugs, problemas de performance e decisões de design envolvendo texto.

> Regra de ouro: _muitas alterações de texto → evite String pura_.

---

## String (java.lang.String)

### Características

- Imutável
    
- Thread-safe por natureza
    
- Armazenada no **String Pool** quando criada como literal
    

### Criação

```java
String a = "Java";          // Pool de Strings
String b = new String("Java"); // Novo objeto no heap
```

### Operações comuns

```java
String s = "Java";

s.length();
s.charAt(0);
s.substring(1, 3);
s.toUpperCase();
s.toLowerCase();
s.trim();
s.replace("a", "o");
s.contains("av");
s.startsWith("Ja");
s.endsWith("va");
```

### Comparação (armadilha clássica)

```java
s.equals("Java");   // correto
s == "Java";        // compara referência
```

---

## StringBuilder

### Quando usar

- Construção dinâmica de strings
    
- Laços (loops)
    
- Performance crítica
    

### Características

- Mutável
    
- Não é thread-safe
    
- Muito mais eficiente que concatenação
    

```java
StringBuilder sb = new StringBuilder();
sb.append("Java");
sb.append(" ");
sb.append("Rocks");

String resultado = sb.toString();
```

---

## StringBuffer

### Quando usar

- Ambientes multithread legados
    

### Características

- Mutável
    
- Thread-safe (sincronizado)
    
- Mais lento que StringBuilder
    

```java
StringBuffer sb = new StringBuffer("Java");
sb.append(" Safe");
```

---

## Concatenação

### Evite em loops

```java
String s = "";
for (int i = 0; i < 1000; i++) {
    s += i; // cria muitos objetos
}
```

### Forma correta

```java
StringBuilder sb = new StringBuilder();
for (int i = 0; i < 1000; i++) {
    sb.append(i);
}
```

---

## Split e Join

### split()

```java
String texto = "Java,Python,Go";
String[] linguagens = texto.split(",");
```

### String.join()

```java
String resultado = String.join(" | ", linguagens);
```

---

## Regex com String

```java
String cpf = "123.456.789-00";
cpf = cpf.replaceAll("[^0-9]", "");
```

---

## Conversões úteis

```java
int x = Integer.parseInt("10");
String s = String.valueOf(10);
```

---

## Boas práticas

- Use `equals()` para comparar strings
    
- Prefira `StringBuilder` em concatenações frequentes
    
- Evite `new String()` sem necessidade
    
- Cuidado com `substring()` em versões antigas (retenção de memória)
    
- Normalize strings para comparação (`trim`, `toLowerCase`)
    

---

## Modelo mental (Zettelkasten)

- **String = valor** (imutável)
    
- **StringBuilder = processo** (construção)
    
- **StringBuffer = processo seguro** (concorrência)    

---

## Nota final

Se strings fossem LEGO:

- `String` → peças coladas
    
- `StringBuilder` → peças encaixáveis
    

Escolha sabiamente. O garbage collector agradece.