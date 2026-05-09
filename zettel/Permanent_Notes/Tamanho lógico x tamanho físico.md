
## Ideia Central

Em software, **o que você vê não é o que ocupa espaço**.

O **tamanho lógico** representa o _significado conceitual_ de um dado.  
O **tamanho físico** representa _quantos bits/bytes_ são realmente usados para armazená-lo.

> Grande parte dos bugs invisíveis em sistemas nasce da confusão entre esses dois conceitos.

---

## Tamanho Lógico

### Definição

É o **significado abstrato** do dado para o programador e para o domínio.

Exemplos:

- `boolean`: verdadeiro ou falso
    
- `char`: um caractere
    
- `int`: um número inteiro
    
- `enum`: um conjunto finito de estados
    

O tamanho lógico responde à pergunta:

> _O que esse dado representa?_

---

## Tamanho Físico

### Definição

É a **quantidade real de memória** utilizada para armazenar o dado.

Exemplos em Java:

- `boolean`: pode ocupar 1 byte ou mais
    
- `char`: sempre 16 bits (UTF-16)
    
- `int`: 32 bits
    
- `Object`: cabeçalho + alinhamento + campos
    

O tamanho físico responde à pergunta:

> _Quanto isso custa na memória?_

---

## 🧩 Por que eles raramente coincidem

Razões principais:

- alinhamento de memória
    
- otimizações da JVM
    
- arquitetura da CPU
    
- endereçamento mínimo (byte)
    
- necessidade de performance
    

Exemplo clássico:

```java
boolean ativo;
```

Lógico: 1 bit  
Físico: ≥ 1 byte (ou mais)

---

## Exemplos Práticos

### Boolean

- Lógico: verdadeiro/falso
    
- Físico: depende da JVM
    
- Arrays de boolean são otimizados, variáveis isoladas não
    

### Enum

- Lógico: estado semântico
    
- Físico: geralmente um `int`
    

### String

- Lógico: texto
    
- Físico:
    
    - referência
        
    - objeto
        
    - array de `char` ou `byte`
        

---

## Impacto em Performance

Confundir tamanho lógico com físico pode causar:

- consumo excessivo de memória
    
- cache misses
    
- serializações infladas
    
- gargalos silenciosos
    

Por isso:

- otimização começa na **representação**
    
- não na micro-otimização de código
    

---

## Relação com Bitwise e Flags

Bitmasks:

- comprimem vários estados lógicos
    
- em um único valor físico
    

Trade-off:

- ganha memória e performance
    
- perde semântica explícita
    

---

## Regra Mental

> Se o dado cruza um limite (memória, rede, disco),  
> o tamanho físico passa a importar.

---

## ❌ Erros Comuns

- assumir que boolean ocupa 1 bit
    
- ignorar overhead de objetos
    
- confundir tamanho em memória com tamanho serializado
    
- otimizar sem medir
    

---

## 📌 Princípio Final

Modelagem escolhe o **tamanho lógico**.  
Arquitetura responde pelo **tamanho físico**.

Engenharia de software madura entende ambos.

---
