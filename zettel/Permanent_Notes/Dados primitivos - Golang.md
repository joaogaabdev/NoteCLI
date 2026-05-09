Referees: #Golang 
## Numéricos

Inteiros (com sinal):
* int (tamanho depende da arquitetura: 32 ou 64bits)
* int8, int16, int32, int64
Inteiro sem sinal:
* uint, uint8, (alias de byte(ocupa 8 bits)), uint16, uint32, uint64
Ponto flutuante:
* float32, float64
Números complexos:
* complex64 (float32 + float32i)
* complex64 (float32 + float32i)

## Texto e caracteres

- string: sequência imutável de bytes (UTF-8)
    
- rune: alias para `int32`, representa um caractere Unicode

## Booleano

* bool: true ou false

# Declaração de Variáveis

Segue a sintaxe:

var nomeDaVariavel tipo
	var idade int => exemplo

Inferindo tipos de dados

Podemos inferir o tipo de dados em golang usando o operador gopher " := " 
Com ele podemos inferir o tipo de dados:
	nome := "João" // Automaticamente entende que é uma string
**Atenção!** Utilizar o := sempre vai alocar o máximo de memória que o tipo permitir.
	Por exemplo, int será sempre int64, uint será sempre uint64 e float será sempre float64 e assim vai...

## Notações para tipos de dados

%d: int / uint
%s: string
%.2f: float (.2 significa = duas casas depois do .)
%t: booleano
