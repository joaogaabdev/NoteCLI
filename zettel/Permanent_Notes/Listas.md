Referees: #Java, #DSA 
### É uma estrutura de dados com as seguintes características:
* Homogênea (dados do mesmo tipo)
* Ordenada (elementos acessados por meio de posições)
* Inicia vazia, e seus elementos são alocados sob demanda
* Cada elemento ocupa um "nó" (ou nodo) da lista

**Vantagens**:
* tamanho variável
* Facilidade para se realizar inserções e deleções
**Desvantagens**:
* Acesso sequencial aos elementos 

Ela modela conceitualmente algo como:
```java
[elemento0, elemento1, elemento2, elemento3]
```

Ou seja:

Estrutura ordenada + acesso por posição

## Hierarquia

```java
Iterable
|
Collection
|
List (interface)
|
Implementações:
|-Arraylist
|-LinkedList
|-Vector
```

Exemplo:
```java
List<String> nomes = new ArrayList<>();  
  
nomes.add("Ana");  
nomes.add("Carlos");  
nomes.add("Ana");

Resultado:
[ Ana, Carlos, Ana ]
```

# Criando uma lista

### Forma recomendada

```java
List<String> nomes = new ArrayList<>();
```

Princípio importante:
Programar para interface, não para implementação

Ou seja:
```java
List<String> lista = new ArrayList<>();
```

e não:
```java
ArrayList<String> lista = new ArrayList<>();
```

## Comandos de uma lista
* Tamanho da lista: `size()`
* Inserir elemento na lista: `add(obj), add(int, obj)`
* Remover elementos da lista: `remove(obj), remove(int), removeIf(Predicate)`
* Encontrar posição do elemento: `indexOf(obj), lastIndexOf(obj)`
* Filtrar lista com base em predicado: `List<Integer> result = list.stream().filter(x -> x > 4).collect(Collectors.toList());`
* Encontrar primeira ocorrência com base em predicado: `Integer result = list.stream().filter(x -> x > 4).findFirst().orElse(null);`
