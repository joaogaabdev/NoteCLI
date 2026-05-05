#Java 
## Conceito central

Em Java, **funções são chamadas de métodos**.  
Um método representa uma **unidade de comportamento**, responsável por executar **uma única ideia bem definida**.

> Pense em métodos como _engrenagens_: pequenas, especializadas e reutilizáveis. Quando uma quebra, o resto da máquina continua funcionando.

---

## Estrutura básica de um método

```java
modificador retorno nomeDoMetodo(parâmetros) {     
	// corpo do método     
	return valor; // se houver retorno }
```

### Exemplo simples

```java
public int somar(int a, int b) {     return a + b; }
```

---

## Componentes do método

### 1. Modificador de acesso

Controla **quem pode chamar o método**.

- `public` → acessível de qualquer lugar
    
- `private` → acessível apenas dentro da classe
    
- `protected` → mesmo pacote ou subclasses
    
- _(default)_ → apenas no mesmo pacote
    

```java
private void validarSenha() { }
```

---

### 2. Tipo de retorno

Define **o que o método devolve**.

- Tipos primitivos (`int`, `double`, `boolean`)
    
- Objetos (`String`, `List`, `User`)
    
- `void` → não retorna nada
    

```java
public void imprimirMensagem() { }
```

---

### 3. Nome do método

Deve ser:

- Verbo
    
- camelCase
    
- Expressivo
    

```java
calcularTotal()
buscarUsuarioPorId()
validarCpf()
```

> Se o nome parece uma frase, você está no caminho certo.

---

### 4. Parâmetros

São as **entradas** do método.

```java
public double calcularArea(double largura, double altura) {
     return largura * altura; 
}
```

- Ordem importa
    
- Tipos importam
    
- Quantidade importa (e muito)
    

---

## Tipos de métodos

### Método sem retorno

```java
public void exibirSaldo(double saldo) {
     System.out.println(saldo); 
}
```

---

### Método com retorno

```java
public boolean estaAtivo() {     
	return true;
}
```

---

### Método sem parâmetros

```java
public String getVersaoSistema() {     return "1.0.0"; }
```

---

### Método com parâmetros

```java
public void depositar(double valor) {    
 saldo += valor;
}
```

---

## Métodos estáticos (`static`)

Pertencem à **classe**, não ao objeto.

```java
public static int somar(int a, int b) {
     return a + b;
}
```

Uso comum:

- Métodos utilitários
    
- Função `main`
    
- Cálculos puros (sem estado)
    

```java
Math.max(10, 20);
```

---

## Boas práticas (ouro puro)

### 1. Uma responsabilidade por método

❌ Ruim:

```java
processarPedido()
```

✅ Melhor:

```java
validarPedido() 
calcularTotal() 
salvarPedido()
```

---

### 2. Métodos curtos

- Ideal: até **20 linhas**
    
- Se passou disso, provavelmente faz coisa demais
    

---

### 3. Evite muitos parâmetros

❌

```java
criarUsuario(String nome, String cpf, String email, String telefone, String endereco)
```

✅

```java
criarUsuario(Usuario usuario)
```

---

### 4. Não misture lógica com I/O

❌

```java
public double calcularDesconto() {     
	Scanner sc = new Scanner(System.in);   
	return sc.nextDouble() * 0.1;
}
```

✅

```java
public double calcularDesconto(double valor) {
     return valor * 0.1;
}
```
