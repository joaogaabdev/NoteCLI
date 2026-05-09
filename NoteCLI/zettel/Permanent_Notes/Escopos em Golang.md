Referees: #Golang 
1. Escopo de bloco
Variáveis declaradas dentro de um bloco { } só podem ser usadas ali
isso vale pra funções, if, for, switch, etc.

``` go
package main

import "fmt"

func main() {
	if true {
	x:=10
	fmt.Prinln(x)}
}
```

2. Escopo de função
Variáveis declaradas dentro de uma função só existem naquela função, são chamadas de variáveis locais.
``` Go
fun soma (a int, b int) int{
	resultado := a + b
	return resultado
	}
```

3. Escopo de pacote
Quando você declara algo fora de uma função, ele pertence ao pacote inteiro(de forma global), é visível por todas as funções dentro do mesmo pacote.
``` Go
package main

import "fmt"

var global = "visível a todo o pacote"

func Main() {
	fmt.Println(global)
}
```

4. Escopo de exportação(público x privado)
Em Go, a visibilidade entre pacotes diferentes depende da primeira letra do identificador:
* Se começar com letra maiúscula -> é exportado(público)
* Se começar com letra minúscula -> é não exportado(privado)
``` Go
package util

var Interno = "visível em outros pacotes"
var interno = "visível dentro do pacote util"
```

5. Shadowing
Se você declara uma variável com o mesmo nome em um escopo interno, ela "sombra"(substitui) a do escopo externo.
``` Go
package main

import "fmt"

var x = 100

func main() {
x := 50
fmt.Println(x) // 50
}
```

