Referees: #Python, #DSA 
Estruturas de chave e valor

``` python
pessoa = {"nome": "Joao", "idade": 21}

print(pessoa)

print(pessoa["nome"]) #Acessa o valor da chave nome 

pessoa["sobrenome"] = ["Santos"] #Adicionando uma nova Chave e valor dentro do dicionário
pessoa["idade"] = [22] #Atualizando a idade para 22

del pessoa["sobrenome"] #Deleta a chave e o valor atrelado a sobrenome

keys() #Retorna todas as chaves do dicionário em formato de lista
#ex
	chaves = pessoa.keys()
	print(chaves)
	
values() #Retorna todos os valores de chaves do dicionário em formato de lista
#ex
	valores = pessoa.values()
	print(valores)
	
items() #Retorna uma lista de tuplas contendo todas as chaves e valores do dicionário
#ex
	itens = pessoa.items()
	print(itens)
```

