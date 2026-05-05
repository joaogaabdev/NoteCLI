Referees #Golang, #DSA 
É um tipo composto que agrupa zero ou mais campos, cada um com nome e tipo.
Em Go não há "classes", structs + métodos + interfaces formam o paradigma orientado a objetos.

Definição e sintaxe básica:
``` Go
type pessoa struct {
	Nome string 
	Idade int
	Ativo bool
}
```

Sintaxe: type NomeDaStruct struct {}
	Campos exportados pra fora da struct, iniciam com letra maiúscula, não exportados, minúscula.

## Instanciação e valor zero

```
```