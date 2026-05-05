#Java, #DSA 
# A Essência da Interface ```Map<K, V>```

Diferente das coleções que herdam de `Collection`, o `Map` é uma estrutura de dados independente que modela uma **função matemática** ou um **dicionário**.

 **Definição Técnica:** Um objeto que mapeia chaves para valores. Não pode conter chaves duplicadas; cada chave pode mapear para no máximo um valor. [1]

### Visão de Coleção (Collection Views)
A documentação oficial destaca que um Map fornece três formas de visualização:
1. **Set de Chaves (`keySet()`):** Como chaves são únicas, são representadas por um `Set`.
2. **Coleção de Valores (`values()`):** Como valores podem se repetir, são uma `Collection`.
3. **Set de Entradas (`entrySet()`):** Um `Set` de objetos `Map.Entry<K, V>`, ideal para iteração de alta performance.

---

## Nota 2: Implementações e Complexidade

Como sênior, você deve escolher a implementação baseada no **contrato de performance** e **comportamento de ordenação**. 

| Implementação     | Estrutura de Dados         | Ordenação            | Complexidade (Busca/Inserção) | Permite Null?            |
| :---------------- | :------------------------- | :------------------- | :---------------------------- | :----------------------- |
| **HashMap**       | Tabela Hash                | Nenhuma              | **O(1)** (médio)              | Sim (1 chave, n valores) |
| **LinkedHashMap** | Tabela Hash + Lista Ligada | Inserção / Acesso    | **O(1)**                      | Sim                      |
| **TreeMap**       | Árvore Rubro-Negra         | Natural / Comparator | **O(log n)**                  | Não (chave), Sim (valor) |

### Insight de Mentor:
* **HashMap:** Use por padrão. Se a performance degradar para O(n), verifique a implementação de `hashCode()` e `equals()` das suas chaves. (Nota: No Java 8+, o HashMap converte buckets longos em árvores, melhorando o pior caso para O(log n)). 
* **LinkedHashMap:** Excelente para implementar caches **LRU (Least Recently Used)** sobrescrevendo o método `removeEldestEntry`. 
* **TreeMap:** Use apenas quando a ordenação for um requisito funcional.

---

## Nota 3: Operações Essenciais (Java 7 e Anteriores)
Estes são os métodos fundamentais presentes desde as primeiras versões da interface Map. 

### ``V put(K key, V value)``
Associa o valor especificado à chave especificada neste mapa. Se o mapa continha anteriormente um mapeamento para a chave, o valor antigo é substituído.
```Java
Map<String, Integer> idades = new HashMap<>(); 
idades.put("Alice", 30); // Adiciona Alice 
idades.put("Bob", 25); // Adiciona Bob 
idades.put("Alice", 31); // Atualiza Alice para 31
System.out.println(idades); // {Alice=31, Bob=25}
```

### ``V get(Object key)``
Retorna o valor ao qual a chave especificada está mapeada, ou null se este mapa não contiver mapeamento para a chave.
```java
Integer idadeAlice = idades.get("Alice"); // 31 
Integer idadeCarlos = idades.get("Carlos"); // null
System.out.println("Idade de Alice: " + idadeAlice); //
Idade de Alice: 31 System.out.println("Idade de Carlos: " + idadeCarlos); // Idade de Carlos: null
```

### ``V remove(Object key)``
Remove o mapeamento para a chave especificada deste mapa, se presente. Retorna o valor anteriormente associado à chave, ou null se não houver mapeamento.
```java
Integer removido = idades.remove("Bob"); // 25 
System.out.println(idades); // {Alice=31}
System.out.println("Removido: " + removido); // Removido: 25
```

### ``boolean containsKey(Object key)``
Retorna true se este mapa contiver um mapeamento para a chave especificada.
```java
boolean temAlice = idades.containsKey("Alice"); // true 
boolean temBob = idades.containsKey("Bob"); // false 
System.out.println("Tem Alice? " + temAlice); // Tem Alice? true
```

### ``boolean containsValue(Object value)``
Retorna true se este mapa mapear uma ou mais chaves para o valor especificado.
```java
boolean temIdade31 = idades.containsValue(31); // 
true boolean temIdade25 = idades.containsValue(25); // false
System.out.println("Tem alguém com 31 anos? " + temIdade31); // Tem alguém com 31 anos? true
```

### ``int size()``
Retorna o número de mapeamentos chave-valor neste mapa.
```java
int tamanho = idades.size(); // 1 
System.out.println("Tamanho do mapa: " + tamanho); // Tamanho do mapa: 1
```

### ``boolean isEmpty()``
Retorna true se este mapa não contiver mapeamentos chave-valor.
```java
boolean estaVazio = idades.isEmpty(); // false
System.out.println("Está vazio? " + estaVazio); // Está vazio? false
```

### ``void putAll(Map<? extends K, ? extends V> m)``
Copia todos os mapeamentos do mapa especificado para este mapa.
```java
Map<String, Integer> novasIdades = new HashMap<>(); novasIdades.put("Carlos", 40); novasIdades.put("Diana", 35); idades.putAll(novasIdades); System.out.println(idades); // {Alice=31, Carlos=40, Diana=35}
```

### ``void clear()``
Remove todos os mapeamentos deste mapa.
```java
idades.clear(); 
System.out.println(idades); // {}
```

### ``Set<K> keySet()``
Retorna um Set de todas as chaves contidas neste mapa.
```java
Map<String, String> frutas = new HashMap<>();
frutas.put("Maçã", "Vermelha"); 
frutas.put("Banana", "Amarela"); 
Set<String> chaves = frutas.keySet(); 
System.out.println("Chaves: " + chaves); // Chaves: [Maçã, Banana]
```

### ``Collection<V> values()``
Retorna uma Collection de todos os valores contidos neste mapa.
```java
Collection<String> valores = frutas.values(); System.out.println("Valores: " + valores); // Valores: [Vermelha, Amarela]
```

### ``Set<Map.Entry<K, V>> entrySet()
Retorna um Set de objetos Map.Entry<K, V>, representando os mapeamentos chave-valor. Ideal para iteração eficiente.
```java
Set<Map.Entry<String, String>> entradas = frutas.entrySet(); 
for (Map.Entry<String, String> entrada : entradas) { System.out.println(entrada.getKey() + " -> " + entrada.getValue()); 
} // Maçã -> Vermelha // Banana -> Amarela
```

### ``boolean equals(Object o)``
Compara o objeto especificado com este mapa para igualdade. Retorna true se o objeto dado também for um mapa e os dois mapas representarem os mesmos mapeamentos.
```java
Map<String, String> frutas2 = new HashMap<>(); 
frutas2.put("Maçã", "Vermelha"); 
frutas2.put("Banana", "Amarela"); 
System.out.println("Mapas são iguais? " + frutas.equals(frutas2)); // Mapas são iguais? true
```

### ``int hashCode()``
Retorna o valor do código hash para este mapa. 
```java
System.out.println("Hash code do mapa: " + frutas.hashCode());
```

## Operações Modernas e Funcionais (Java 8+)

O Java 8 introduziu métodos default na interface Map, que fornecem funcionalidades mais concisas e expressivas, especialmente úteis com expressões lambda. 

### ``V getOrDefault(Object key, V defaultValue)``
Retorna o valor ao qual a chave especificada está mapeada, ou defaultValue se este mapa não contiver mapeamento para a chave. [1]
```java
Map<String, String> configuracoes = new HashMap<>(); configuracoes.put("tema", "dark"); String tema = configuracoes.getOrDefault("tema", "light"); // 
dark String idioma = configuracoes.getOrDefault("idioma", "pt-BR"); // pt-BR 
System.out.println("Tema: " + tema + ", Idioma: " + idioma);
```

### ``void forEach(BiConsumer<? super K, ? super V> action)``
Executa a ação fornecida para cada entrada neste mapa até que todas as entradas tenham sido processadas ou a ação lance uma exceção. 
```java
Map<String, Double> produtos = new HashMap<>(); produtos.put("Notebook", 1200.0);
produtos.put("Mouse", 25.0);
System.out.println("Lista de Produtos:"); 
produtos.forEach((nome, preco) -> System.out.println(nome + ": R$" + preco));
```

### ``V putIfAbsent(K key, V value)``
Se a chave especificada ainda não estiver associada a um valor (ou estiver mapeada para null), associa-a ao valor fornecido e retorna null. Caso contrário, retorna o valor atual. 
```java
Map<String, String> cache = new HashMap<>(); cache.put("user1", "data1"); String oldVal1 = cache.putIfAbsent("user1", "newData1"); // data1 (não altera) 
String oldVal2 = cache.putIfAbsent("user2", "data2"); // null (adiciona) 
System.out.println(cache); // {user1=data1, user2=data2}
System.out.println("oldVal1: " + oldVal1 + ", oldVal2: " + oldVal2);
```

### ``boolean remove(Object key, Object value)``
Remove a entrada para a chave apenas se ela estiver atualmente mapeada para o valor especificado. 
```java
Map<String, Integer> pontuacoes = new HashMap<>(); pontuacoes.put("JogadorA", 100); pontuacoes.put("JogadorB", 150); boolean removido1 = pontuacoes.remove("JogadorA", 100); // true
boolean removido2 = pontuacoes.remove("JogadorB", 200); // false (valor não corresponde)
System.out.println(pontuacoes); // {JogadorB=150}
System.out.println("Removido JogadorA: " + removido1 + ", Removido JogadorB: " + removido2);
```

### ``boolean replace(K key, V oldValue, V newValue)``
Substitui a entrada para a chave especificada apenas se ela estiver atualmente mapeada para o oldValue especificado.
```java
Map<String, String> statusPedidos = new HashMap<>(); statusPedidos.put("ORD-001", "PENDENTE"); boolean substituido1 = statusPedidos.replace("ORD-001", "PENDENTE", "PROCESSANDO"); // true
boolean substituido2 = statusPedidos.replace("ORD-001", "FINALIZADO", "CANCELADO"); // false 
System.out.println(statusPedidos); // {ORD-001=PROCESSANDO}
System.out.println("Substituído ORD-001 (PENDENTE->PROCESSANDO): " + substituido1);
```

### ``V replace(K key, V value)``
Substitui a entrada para a chave especificada apenas se ela estiver atualmente mapeada para algum valor. 
```java
Map<String, String> usuariosLogados = new HashMap<>(); usariosLogados.put("admin", "sessao123"); String oldSession = usuariosLogados.replace("admin", "sessao456"); // sessao123 
String nonExistent = usuariosLogados.replace("guest", "sessao789"); // null 
System.out.println(usuariosLogados); // {admin=sessao456}
System.out.println("Sessão antiga do admin: " + oldSession);
```

### ``V computeIfAbsent(K key, Function<? super K, ? extends V> mappingFunction)``
Se a chave especificada ainda não estiver associada a um valor (ou estiver mapeada para null), tenta calcular seu valor usando a função de mapeamento fornecida e o insere neste mapa, a menos que seja null. 

// Agrupamento de dados (exemplo anterior, agora com explicação) Map<String, List<String>> grupos = new HashMap<>(); grupos.computeIfAbsent("Devs", k -> new ArrayList<>()).add("João"); grupos.computeIfAbsent("Devs", k -> new ArrayList<>()).add("Maria"); grupos.computeIfAbsent("QAs", k -> new ArrayList<>()).add("Pedro"); System.out.println(grupos); // {QAs=[Pedro], Devs=[João, Maria]} // Explicação: Se 'Devs' não existe, cria uma nova ArrayList e a associa. Em seguida, adiciona 'João'. // Na segunda chamada para 'Devs', a chave já existe, então a função não é executada, e 'Maria' é adicionada à lista existente.

### V computeIfPresent(K key, BiFunction<? super K, ? super V, ? extends V> remappingFunction)

Se o valor para a chave especificada estiver presente e não for null, tenta calcular um novo mapeamento dado a chave e seu valor mapeado atual. [1]

Java

// Atualização atômica (exemplo anterior, agora com explicação) Map<String, Double> precos = new HashMap<>(); precos.put("Livro", 50.0); precos.put("Caneta", 5.0); Double novoPrecoLivro = precos.computeIfPresent("Livro", (k, v) -> v * 0.9); // Aplica 10% de desconto Double novoPrecoLapis = precos.computeIfPresent("Lápis", (k, v) -> v * 0.9); // null (chave não existe) System.out.println(precos); // {Livro=45.0, Caneta=5.0} System.out.println("Novo preço do Livro: " + novoPrecoLivro); // Explicação: Se 'Livro' existe, aplica a função de remapeamento (desconto). Se 'Lápis' não existe, nada acontece.

### V compute(K key, BiFunction<? super K, ? super V, ? extends V> remappingFunction)

Tenta calcular um mapeamento para a chave especificada e seu valor mapeado atual (ou null se não houver mapeamento atual). [1]

Java

Map<String, String> status = new HashMap<>(); status.put("TarefaA", "Iniciada"); // Atualiza TarefaA para "Concluída" se estiver "Iniciada" status.compute("TarefaA", (k, v) -> v.equals("Iniciada") ? "Concluída" : v); // Concluída // Adiciona TarefaB como "Pendente" se não existir status.compute("TarefaB", (k, v) -> v == null ? "Pendente" : v); // Pendente System.out.println(status); // {TarefaA=Concluída, TarefaB=Pendente}

### V merge(K key, V value, BiFunction<? super V, ? super V, ? extends V> remappingFunction)

Se a chave especificada ainda não estiver associada a um valor ou estiver mapeada para null, associa-a ao valor fornecido. Caso contrário, substitui a entrada pelo resultado da função de remapeamento fornecida. [1]

Java

// Contador de palavras simplificado (exemplo anterior, agora com explicação) Map<String, Integer> contador = new HashMap<>(); String[] palavras = {"java", "map", "java", "collection", "map"}; for (String palavra : palavras) { contador.merge(palavra, 1, Integer::sum); } System.out.println(contador); // {java=2, collection=1, map=2} // Explicação: Para 'java' (primeira vez), adiciona 1. Para 'java' (segunda vez), soma 1 ao valor existente (1+1=2).

### void replaceAll(BiFunction<? super K, ? super V, ? extends V> function)

Substitui cada entrada do mapa pelo resultado da aplicação da função fornecida em seus valores atuais. [1]

Java

Map<String, Double> notas = new HashMap<>(); notas.put("Matemática", 7.5); notas.put("Português", 8.0); notas.replaceAll((disciplina, nota) -> nota + 0.5); // Adiciona 0.5 a todas as notas System.out.println(notas); // {Matemática=8.0, Português=8.5}
---

## Nota 4: Imutabilidade e Fábricas Estáticas (Java 9+)

Desde o Java 9, temos formas concisas de criar Maps imutáveis. [2]

```java
// Criando um Map imutável (Java 9+)
Map<String, String> config = Map.of(
    "env", "prod",
    "timeout", "3000"
);

// Criando uma cópia defensiva imutável (Java 10+)
Map<String, String> copy = Map.copyOf(originalMap);
```
**Atenção:** `Map.of` e `Map.copyOf` **não aceitam chaves ou valores null** e lançam `UnsupportedOperationException` se você tentar modificá-los. [2]

---

## Nota 5: Implementação Prática e Explicação

Vamos analisar um cenário real: **Processamento de Pedidos**.

```java
import java.util.*;

public class OrderProcessor {
    public static void main(String[] args) {
        // Usamos LinkedHashMap para manter a ordem cronológica dos pedidos
        Map<String, Double> orders = new LinkedHashMap<>();
        
        orders.put("ORD-001", 150.0);
        orders.put("ORD-002", 250.0);
        orders.put("ORD-003", 100.0);

        // Iteração moderna usando forEach (Java 8+)
        // Explicação: O método forEach aceita um BiConsumer (key, value)
        orders.forEach((id, total) -> System.out.println("Pedido: " + id + " | Total: R$" + total));

        // Atualização atômica: Se o pedido existir, aplica 10% de desconto
        orders.computeIfPresent("ORD-002", (id, total) -> total * 0.9);
        
        System.out.println("Após desconto no ORD-002: " + orders.get("ORD-002"));
    }
}
```

---

## Nota 6: Exercícios para Prática

Para fixar o conhecimento, tente resolver estes desafios:

1.  **Frequência de Caracteres:** Escreva um método que receba uma String e retorne um `Map<Character, Integer>` com a contagem de cada caractere, usando `Map.merge`.
2.  **Cache LRU Simples:** Utilize `LinkedHashMap` para criar um cache de tamanho fixo (ex: 3 elementos). Quando o 4º elemento for inserido, o mais antigo deve ser removido automaticamente.
3.  **Agrupamento por Categoria:** Dado uma lista de objetos `Produto(nome, categoria, preco)`, use um `Map<String, List<Produto>>` para agrupar os produtos por categoria usando `computeIfAbsent`.
4.  **Ordenação Customizada:** Crie um `TreeMap` que armazene nomes de pessoas como chaves, mas que a ordenação seja feita pelo **comprimento do nome** (do menor para o maior) e não pela ordem alfabética.

---
