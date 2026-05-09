Referees: #Golang 
Funções são trechos de códigos reutilizáveis, que podem receber argumentos e podem retornar valores ou executar outras funções.

Função que não recebe argumento e não retorna:
``` go
	func Hello() {
		fmt.Println("Hello, World!")
	}
```

Função que recebe argumento e não retorna:
``` go
	func Hello(string) {
		fmt.Printf("Hello, %s"), nome
	}
```

Para chamar uma função, devemos chamar em um trecho de código que será executado, nesse caso a função main:
``` go
	func main() {
	Hello("João")
	}

```

Função que retorna valor:
``` go
	func Hello() string {
	return "Hello, World!"
	}
```

Função que retorna dois valores:
``` go
func Hello() string {
	return "Hello, World!", 0
	}
```

## Recebendo valores de uma função

Quando funções retornam valores, podem ser alocados em variáveis:
``` go
	func main() {
	mensagem := Hello()
	fmt.Println(mensagem)}
```

Caso de dois retornos:
``` go
	func main() {
	mensagem, retorno2 := Hello()
	fmt.Println(mensagem, retorno2)
	}
```
	Caso queira ignorar um dos dois retornos, basta substituir por _ no lugar da variável, exemplo:
	(_, retorno2) --> só irá retornar o valor de retorno2.
