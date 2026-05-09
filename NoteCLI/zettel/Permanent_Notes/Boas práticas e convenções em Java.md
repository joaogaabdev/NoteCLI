#Java
## Conceito Central

Boas práticas e convenções em Java existem para **padronizar, tornar o código legível, sustentável e escalável**. Código Java raramente é escrito para o computador — ele é escrito para **outros humanos (e para você no futuro)**.

> Código funciona hoje. Boas práticas funcionam por anos 😄

---

## Convenções de Nomenclatura

### Classes

- Usar **PascalCase**
    
- Substantivos
    

```java
public class UsuarioService {}
public class PedidoController {}
```

---

### Métodos

- **camelCase**
    
- Verbos no infinitivo
    

```java
public void calcularTotal() {}
public boolean validarSenha() {}
```

---

### Variáveis

- **camelCase**
    
- Nomes claros e descritivos
    

```java
int idadeUsuario;
double saldoConta;
```

❌ Evitar

```java
int x;
String a;
```

---

### Constantes

- `static final`
    
- **UPPER_SNAKE_CASE**
    

```java
public static final int IDADE_MINIMA = 18;
```

---

## Organização de Pacotes

- Usar nomes em **minúsculo**
    
- Estrutura baseada em domínio ou responsabilidade
    

```text
com.empresa.projeto
 ├── controller
 ├── service
 ├── repository
 └── model
```

> Pacote bagunçado é o começo da entropia.

---

## Princípios Fundamentais

### Single Responsibility Principle (SRP)

Uma classe deve ter **um único motivo para mudar**.

❌ Classe faz tudo  
✔ Classe faz uma coisa bem

---

### DRY — Don’t Repeat Yourself

Evite duplicação de código.

```java
// ruim
calcularImposto();
calcularImposto();
```

---

### KISS — Keep It Simple, Stupid

Prefira soluções simples e legíveis.

> Se precisa explicar demais, está complexo demais.

---

## Estruturas de Controle

✔ Evitar `if/else` muito profundos  
✔ Preferir retorno antecipado

```java
if (!ativo) return;
```

✔ Usar `switch` quando houver múltiplos casos claros

---

## Tratamento de Exceções

### Use exceções para fluxo excepcional

```java
try {
    processarPagamento();
} catch (PagamentoException e) {
    log.error(e.getMessage());
}
```

❌ Não usar exceções como controle de fluxo normal

---

### Nunca engolir exceções

```java
catch (Exception e) {
    // errado
}
```

✔ Sempre trate ou propague

---

## Imutabilidade Sempre que Possível

```java
public final class Usuario {
    private final String nome;

    public Usuario(String nome) {
        this.nome = nome;
    }
}
```

Benefícios:

- Thread-safe
    
- Mais previsível
    
- Menos bugs
    

---

## Coleções e Loops

✔ Preferir interfaces (`List`, `Set`, `Map`)  
✔ Usar `for-each` para leitura  
✔ Evitar modificar coleção durante iteração

---

## Comentários

✔ Explicar **por quê**, não **o quê**

```java
// Regra fiscal definida pelo BACEN
```

❌ Comentários óbvios

```java
// incrementa i
```

---

## Código Limpo

✔ Métodos curtos (ideal < 20 linhas)  
✔ Evitar números mágicos  
✔ Nomes claros > comentários

```java
if (idade >= IDADE_MINIMA) {}
```

---

## Testes

✔ Escrever código testável  
✔ Métodos pequenos facilitam testes  
✔ Testes explicam o comportamento

> Código sem teste funciona. Até não funcionar.

---

## Performance (Sem Obsessão)

- Primeiro: legibilidade
    
- Depois: correção
    
- Por último: otimização
    

> Otimização prematura é dívida técnica.

---

## 🧩 Relação com Arquitetura

Boas práticas são a base de:

- SOLID
    
- Clean Architecture
    
- Domain-Driven Design
    

Sem convenção, não há arquitetura — apenas arquivos.

