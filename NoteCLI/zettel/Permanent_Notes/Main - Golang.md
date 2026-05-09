Referees: #Golang 
Obrigatoriamente, todo projeto Go precisa de um pacote main.

Para criar o arquivo main, não basta colocar o nome main.go mas sim importar o pacote main:

`package main`

Para transformar o arquivo em executável(binário) é preciso fazer o build do mesmo com o comando:

`go build main.go`

Para executar o binário gerado:
`.\main.exe`

Para rodar o código sem gerar um executável diretamente com o código:
`go run main.go`
