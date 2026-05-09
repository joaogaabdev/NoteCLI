Referees: #Golang 
Usaremos o comando ScanF para receber variáveis, similar ao printf, precisaremos lembrar das notações para cada tipos de dados, usando a %.

%d: int / uint
%s: string
%.2f: float (.2 significa = duas casas depois do .)
%t: booleano

Scaneando um nome
``` go
	func main() {
	var nome string 
	fmt.Print("Digite seu nome: ")
	fmt.Scanf("%s", &nome)
	fmt.Prinf("Olá, %s", nome)
	}
```
Aqui percebe o uso do Scanf e uso do & antes da variável.
		Esse *&* acessa o endereço de memória da variável e altera o seu valor.