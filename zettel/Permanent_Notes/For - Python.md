Referees: #Python

Serve para iterar em uma sequência de elementos, irá repetir o mesmo comando na sequência de elementos

``` python
lista = [1, 2, 3, 4, 5]
for elemento in lista:
	print(elemento) #Vai printar todos os elementos da lista, um por vez
	
tupla = (1, 2, 3, 4, 5)
for elemento in tupla:
	print(elemento) #Vai printar todos os elementos da tupla, um por vez
	
pessoa = {"nome": "Joao", "idade": 21, "cidade": "maceio"}
for chave in pessoa.keys():
	print(chave) #Vai printar todas as chave do dicionárip, um por vez
	
pessoa = {"nome": "Joao", "idade": 21, "cidade": "maceio"}
for valor in pessoa.values():
	print(valor) #Vai printar todss os valores do dicionárip, um por vez	

pessoa = {"nome": "Joao", "idade": 21, "cidade": "maceio"}
for chave, valor in pessoa.items()
	print(f"{chave} : {valor}") #Vai printar todas as chave e valores do dicionário em forma de listas de tuplas, a primeira informação vai pra chave e a segunda pra valor
	
range() #intervalo numérico de uma lista

numero = [1, 2, 3, 4, 5]
for numero in range(5):
	print("Número:", numero) #Vai printar o valor do endereço 0 até a posição 5
	
```
