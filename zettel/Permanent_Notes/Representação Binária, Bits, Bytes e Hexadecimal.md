
## Ideia Central

Computadores não entendem conceitos — entendem **estados elétricos**. Tudo em software é, no fim, **representação**: números, texto, imagens e protocolos são mapeamentos consistentes entre **bits** e **significado**.

> Engenharia de software começa quando você entende **como a informação é representada**, não apenas como ela é usada.

---

## Bit

### Conceito

- **Bit** (_binary digit_) é a menor unidade de informação
    
- Possui dois estados: `0` ou `1`
    

Fisicamente representa:

- tensão elétrica (baixo / alto)
    
- carga magnética
    
- estado lógico
    

---

## Byte

### Conceito

- **1 byte = 8 bits**
    
- Unidade mínima endereçável na maioria das arquiteturas
    

Exemplo:

```text
10101010  -> 1 byte
```

Por que 8 bits?

- Compromisso histórico entre custo e capacidade
    
- Permite 256 combinações (0–255)
    

---

## Sistemas de Numeração

Computadores trabalham em **base 2**, humanos em **base 10**.

|Sistema|Base|Dígitos|
|---|---|---|
|Binário|2|0, 1|
|Decimal|10|0–9|
|Hexadecimal|16|0–9, A–F|

---

## Binário (Base 2)

Cada posição representa uma potência de 2.

```text
1011₂ = 1·2³ + 0·2² + 1·2¹ + 1·2⁰ = 11₁₀
```

Use quando:

- Manipula bits diretamente
    
- Analisa flags e máscaras
    

---

## Hexadecimal (Base 16)

### Conceito

Hexadecimal é uma **representação compacta do binário**.

|Hex|Binário|
|---|---|
|0|0000|
|F|1111|

Exemplo:

```text
0xAF = 1010 1111
```

Por que é usado:

- Menos dígitos
    
- Mapeamento direto (4 bits = 1 hex)
    
- Excelente para leitura humana
    

---

## Complemento de Dois (Números Negativos)

Java usa **complemento de dois** para inteiros com sinal.

Processo:

1. Inverte os bits
    
2. Soma 1
    

Exemplo (`-5` em 8 bits):

```text
5      = 00000101
invert = 11111010
+1     = 11111011
```

Propriedades importantes:

- Soma e subtração funcionam naturalmente
    
- Um único zero
    

---

## Tipos Primitivos e Tamanho (Java)

|Tipo|Bits|Intervalo|
|---|---|---|
|`byte`|8|-128 a 127|
|`short`|16|-32.768 a 32.767|
|`int`|32|±2 bilhões|
|`long`|64|±9 quintilhões|
|`char`|16|Unicode|

👉 `boolean` é conceitual (tamanho dependente da JVM).

---

## Bits, Bytes e Operações

Operações comuns:

- AND, OR, XOR
    
- Shift (`<<`, `>>`, `>>>`)
    

Essas operações **não entendem valores**, apenas bits.

---

## Representação de Texto

Texto não é letra — é **código**.

- ASCII: 7 bits
    
- Unicode: milhares de símbolos
    
- UTF-8: variável (1 a 4 bytes)
    

Exemplo:

```text
'A' = 65 = 01000001
```

---

## 🧠 Endianness (Ordem dos Bytes)

Define como bytes são armazenados na memória.

- **Big-endian**: byte mais significativo primeiro
    
- **Little-endian**: byte menos significativo primeiro
    

Java abstrai isso, mas protocolos e arquivos não.

---

## ⚙ Por que isso importa

- Serialização
    
- Protocolos de rede
    
- Criptografia
    
- Compressão
    
- Performance
    
- Interoperabilidade
    

Ignorar representação leva a bugs silenciosos.

---

## ❌ Erros Comuns

- Confundir tamanho lógico com tamanho físico
    
- Assumir encoding errado
    
- Ignorar sinal
    
- Tratar binário como detalhe irrelevante
    

---

## Regra Mental

> Toda vez que dados cruzam um limite (arquivo, rede, API),  
> **representação importa**.

---

## 📌 Princípio Final

Bits são simples.  
O poder está em **como você decide usá-los**.

---

