#Java 
# 📋 Tabela de especificadores de formato (`printf`) – Java

```java
System.out.printf("Formato aqui", variavel);
```

## **Inteiros**

|Especificador|Tipo|Significado|
|---|---|---|
|`%d`|byte, short, int, long|Inteiro decimal|
|`%o`|int|Inteiro octal|
|`%x`|int|Inteiro hexadecimal (minúsculo)|
|`%X`|int|Inteiro hexadecimal (maiúsculo)|
## **Ponto flutuante**

|Especificador|Tipo|Significado|
|---|---|---|
|`%f`|float, double|Decimal padrão|
|`%.2f`|float, double|Decimal com 2 casas|
|`%e`|float, double|Notação científica|
|`%E`|float, double|Científica (maiúscula)|
|`%g`|float, double|Usa `%f` ou `%e` automaticamente|
|`%a`|float, double|Hexadecimal em ponto flutuante|
## **Strings e caracteres**

|Especificador|Tipo|Significado|
|---|---|---|
|`%s`|String|Texto|
|`%S`|String|Texto em MAIÚSCULO|
|`%c`|char|Caractere|
|`%C`|char|Caractere MAIÚSCULO|
## **Booleanos**

|Especificador|Tipo|Significado|
|---|---|---|
|`%b`|boolean|true / false|
|`%B`|boolean|TRUE / FALSE|
## **Genéricos / utilitários**

|Especificador|Tipo|Significado|
|---|---|---|
|`%s`|Object|Chama `toString()`|
|`%h`|Object|HashCode em hexadecimal|
|`%n`|—|Quebra de linha (portável)|
|`%%`|—|Imprime `%`|
## **Largura, alinhamento e precisão**

|Exemplo|Significado|
|---|---|
|`%6d`|Inteiro com largura mínima 6|
|`%-6d`|Inteiro alinhado à esquerda|
|`%06d`|Preenche com zeros|
|`%.2f`|2 casas decimais|
|`%8.2f`|Largura 8, 2 decimais|
## **Exemplo completo**

```java
int idade = 25; 
double salario = 3450.756;
String nome = "João";  
System.out.printf(     
"Nome: %s%nIdade: %d%nSalário: R$ %.2f%n",       nome, idade, salario );

```
