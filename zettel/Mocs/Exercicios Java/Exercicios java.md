Referees: #Java 
# Problema "numero negativo"
Faça um programa que leia um número inteiro positivo N (máximo = 10) e depois N números inteiros e armazene-os em um vetor. Em seguida, mostrar na tela todos os números negativos lidos. 

Exemplo 
```java
Quantos numeros voce vai digitar? 6
Digite um numero: 8
Digite um numero: -2
Digite um numero: 9
Digite um numero: 10
Digite um numero: -3
Digite um numero: -7
NUMEROS NEGATIVOS: 
-2
-3
-7
```

# Problema "alturas"
Fazer um programa para ler nome, idade e altura de N pessoas, conforme o exemplo. Depois, mostrar na tela a altura média das pessoas, e mostrar também a porcentagem de pessoas com menos de 16 anos, bem como os nomes dessas pessoas se houver.

Exemplo
```java
Quantas pessoas serao digitadas? 5 
dados da 1a pessoa:
Nome: Joao 
Idade: 15
Altura: 1.82
dados da 2a pessoa:
Nome: Maria
Idade: 16
Altura: 1.60
dados da 3a pessoa:
Nome: Teresa
Idade: 14
Altura: 1.58
dados da 4a pessoa:
Nome: Carlos
Idade: 21
Altura: 1.65
dados da 5a pessoa:
Nome: Paulo
Idade: 17
Altura: 1.78

Altura media: 1.69
Pessoas com menos de 16 anos: 40.0%
Joao 
Teresa
```

# Problema "pensionato"
A dona de um pensionato possui dez quartos para alugar para estudantes, sendo esses quartos identificados pelos números 0 a 9.

Fazer um programa que inicie com todos os 10 quartos vazios, e depois leia uma quantidade N representando o número de estudantes que vão alugar os quartos (N pode ser de 1 a 10). Em seguida, registre o aluguel dos N estudantes. Para cada registro de aluguel, informar o nome e email do estudante, bem como qual dos quartos ele escolheu (de 0 a 9). Suponha que seja escolhido um quarto vago. Ao final, seu programa deve imprimir um relatório com todas as ocupações do pensionato, por ordem de quarto, conforme exemplo:

```java
how many rooms will be rented? 3

Rent #1:
Name: Maria Green
Email: maria@gmail.com
Room: 5

Rent #2:
Name: Marco Antonio
Email: marco@gmail.com
Room: 1

Rent #3:
Name: Alex Brown 
Email: alex@gmail.com
Room: 8

Busy rooms: 
1: Marco Antonio, marco@gmail.com
5: Maria Green, maria@gmail.com
8: Alex Brown, alex@gmail.com
```

# Problema Listas

```java
How many employees will be registered? 3

Employee #1:
Id: 333
Name: Maria Brown
Salary: 4000.00

Employee #2:
Id: 536
Name: Alex Grey
Salary: 3000.00

Employee #3:
Id: 772
Name: Bob Green
Salary: 5000.00

Enter the employee id that will have salary increase: 536
Enter the percentage: 10.0

List of employees:
333, Maria Brown, 4000.00
536, Alex Grey, 3300.00
772, Bob Green, 5000.00
```
se o id não existir:
```java
How many employees will be registered? 2

Employee #1:
Id: 333
Name: Maria Brown
Salary: 4000.00

Employee #2:
Id: 536
Name: Alex Grey
Salary: 3000.00

Enter the employee id that will have salary increase: 776
This id does not exist!

List of employees:
333, Maria Brown, 4000.00
536, Alex Grey, 3000.00
```

## Problema Matrizes
Fazer um programa para ler um número inteiro N e uma matriz de ordem N contendo números inteiros. Em seguida, mostrar a diagonal principal e a quantidade de valores negativos da matriz.  

```java
input:
3
5 -3 10
15 8 2
7 9 -4

Output:
Main diagonal:
5 8 -3
Negative numbers = 2
```

## Problema Matrizes 2
Fazer um programa para ler dois números inteiros M e N, e depois ler uma matriz de M linhas e N colunas contendo números inteiros, podendo haver repetições. Em seguida, ler um número inteiro X que pertence à matriz. Para cada ocorrência de X, mostrar os valores à esquerda, à direita e abaixo de X, quando houver, conforme exemplo:

```java
3 4
10 8 15 12
21 11 23 8
14 5 13 19
8

Position 0,1:
Left: 10
Right: 15
Down: 11
Position 1,3:
Left 23
Up: 12
Down: 19
```
