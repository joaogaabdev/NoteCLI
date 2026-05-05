Referees: #Golang 
Permitem que a depender dos dados inseridos, teremos saídas diferentes.

## `if` e `else`
Exemplo:

``` go
	func main() {
		var idade int8
		fmt.Print("Digite sua idade: ")
		fmt.Scanf("%d", &idade)
		if idade >= 18 {
			fmt.Prinln("Você é maior de idade.")
		} else {
			fmt.Println("Você é menor de idade.")
		}
	}
```

## `Switch` 
Exemplo:
``` go
	func main() {
		var abreviacao string
		
		fmt.Println("Digite a abreviação de um dia da semana (ex: seg, ter, qua):")
		fmt.Scan(&abreviacao)
		
		switch abreviacao {
		case "dom":
			fmt.Println("Domingo)
		case "seg":
			fmt.Println("Segunda-feira"
		case "ter":
			fmt.Println("Terça-feira")
			
		default:
			fmt.Println("Abreviação inválida! Tente novamente.")	
			}
	}
```
## Operadores de comparação


|     |  **Comparadores**  |
| :-: | :------------: |
| ==  |    igual a     |
|  >  |   maior que    |
|  <  |   menor que    |
| >=  | maior ou igual |
| <=  | menor ou igual |
| !=  |   diferente    |

Estudar mais o FOR
Slice
Maps
Arrays

