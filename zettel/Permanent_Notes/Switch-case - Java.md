#Java 
## 🧠 Ideia Central

O `switch-case` em Java é uma estrutura de **seleção múltipla baseada em igualdade**, adequada para cenários com **valores discretos e conhecidos**, mas que **não deve substituir polimorfismo ou boa modelagem**. Em Java moderno, o `switch` evoluiu para uma **expressão segura, exaustiva e legível**.

---

## 🧩 Conceito Fundamental

- Avalia **uma única expressão**
    
- Compara por **igualdade** (`==` para primitivos, `equals` para objetos como `String`)
    
- Direciona o fluxo para o `case` correspondente
    

👉 Não lida bem com **intervalos complexos** nem com **regras dinâmicas**.

---

## 🏛 Switch Clássico (Estrutura Histórica)

```java
switch (valor) {
	case A:
		acaoA();
		break;
	case B:
		acaoB();
		break;
	default:
		acaoPadrao();
}
```

### Invariantes importantes

- `break` controla o fluxo
    
- Ausência de `break` causa **fall-through**
    
- `default` é opcional, mas reduz estados implícitos
    

---

## ⚠ Fall-through

Fall-through é a continuação da execução para o próximo `case`.

- Pode ser **intencional** (ex: níveis de permissão)
    
- É uma **fonte clássica de bugs** quando não explícito
    

Regra prática:

> Se o fall-through não for óbvio ao ler o código, ele é um erro.

---

## 🧬 Tipos Compatíveis

- Primitivos: `byte`, `short`, `char`, `int`
    
- Wrapper equivalentes (autoboxing)
    
- `String` (Java 7+)
    
- `enum` (Java 5+)
    

❌ Não suporta `long`, `float`, `double`, `boolean`

---

## 🧱 Enum + Switch (Uso Recomendado)

```java
enum Status { ABERTO, FECHADO, PENDENTE }

switch (status) {
	case ABERTO -> abrir();
	case FECHADO -> fechar();
	case PENDENTE -> aguardar();

}
```

Por que é superior:

- Domínio fechado
    
- Sem valores inválidos
    
- Melhor leitura semântica
    
- Base para **exaustividade em tempo de compilação**
    

---

## 🚀 Switch como Expressão (Java 14+)

O `switch` moderno **retorna valores**.

```java
String tipo = switch (dia) {
	case 1, 7 -> "Fim de semana";
	case 2, 3, 4, 5, 6 -> "Dia útil";
	default -> "Inválido";
};
```

### Propriedades

- Não usa `break`
    
- Não permite fall-through acidental
    
- Força retorno consistente
    

---

## 🧠 `yield`

Usado quando o `case` exige múltiplas instruções.

```java
String resultado = switch (nota) {
	case 10, 9 -> {
	log();
	yield "Excelente";
	}
	default -> "Regular";
};
```

`yield` expressa explicitamente **retorno de valor**, não fluxo.

---

## 🔐 Exhaustividade

Com `enum` + switch expression:

- O compilador exige cobertura total
    
- Elimina estados não tratados
    

👉 Segurança estrutural, não apenas lógica.

---

## ⚙ Performance (Nota Secundária)

- JVM pode usar `tableswitch` ou `lookupswitch`
    
- Diferença de performance vs `if-else` raramente é relevante
    

Regra:

> Priorize **clareza e domínio**, não micro-otimização.

---

## ❌ Anti-Padrões

- `switch` com lógica extensa dentro dos `case`
    
- `switch` sobre `String` quando um `enum` representa melhor o domínio
    
- Uso de `switch` como substituto de **polimorfismo**
    

---

## 🏗 Alternativas Arquiteturais

### Polimorfismo / Strategy

```java
interface Acao { void executar(); }
```

### Map + Função

```java
Map<String, Runnable> comandos = Map.of(
	"START", this::start,
	"STOP", this::stop
);
```

Use quando:

- Comportamento varia mais que o dado
    
- Regras crescem com o tempo
    

---

## 🧠 Heurística de Uso (Regra Mental)

Use `switch` se:

- Os valores são discretos e estáveis
    
- O domínio é pequeno
    
- O código fica mais legível
    

Evite se:

- Há crescimento comportamental
    
- OO resolve melhor
    

---

## 📌 Princípio Final

> `switch` resolve **decisão por valor**, não **variação de comportamento**.

Quando comportamento muda, **modelagem vence controle de fluxo**.

---

