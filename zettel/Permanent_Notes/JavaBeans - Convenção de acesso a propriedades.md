#Java 
## Ideia central

JavaBeans é uma **convenção de design** em Java que define como uma classe expõe suas propriedades por meio de **métodos padronizados**, permitindo que frameworks, IDEs e ferramentas descubram e manipulem dados automaticamente via **introspecção**.

---

## Contexto

JavaBeans não é um framework nem uma API específica, mas um **contrato implícito** seguido por classes Java para garantir interoperabilidade com bibliotecas como Spring, Hibernate, Jackson, JSP/JSF e ferramentas baseadas em reflexão.

Seguir essa convenção reduz configuração manual, elimina acoplamento desnecessário e viabiliza automações em larga escala.

---

## Convenções fundamentais

### 1. Construtor padrão (no-args)

A classe deve possuir um construtor público sem parâmetros.

> Permite que frameworks instanciem objetos dinamicamente via reflexão.

---

### 2. Encapsulamento dos atributos

Os atributos devem ser **privados**, evitando acesso direto ao estado interno do objeto.

> O acesso às propriedades ocorre exclusivamente por métodos.

---

### 3. Getters e Setters padronizados

#### Getter

```java
public Tipo getPropriedade()
```

#### Setter

```java
public void setPropriedade(Tipo valor)
```

#### Booleanos

```java
public boolean isPropriedade()
```

> O **nome da propriedade** é inferido a partir do nome do método, não do atributo.

---

### 4. Serialização (opcional, mas comum)

Implementar `Serializable` é frequente quando o objeto:

- Trafega pela rede
- Vai para sessão
- É persistido ou cacheado
    

---

## Exemplo canônico

```java
public class Product {

    private Long id;
    private String name;
    private double price;
    private boolean available;

    public Product() {}

    public Long getId() {
        return id;
    }

    public void setId(Long id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public double getPrice() {
        return price;
    }

    public void setPrice(double price) {
        this.price = price;
    }

    public boolean isAvailable() {
        return available;
    }

    public void setAvailable(boolean available) {
        this.available = available;
    }
}
```

---

## Por que JavaBeans é relevante

### Introspecção

Frameworks identificam propriedades analisando métodos que começam com:

- `get`
- `set`
- `is`
    

Isso permite:

- Injeção de dependências
- Serialização automática (JSON/XML)
- Mapeamento objeto-relacional
    

---

### Integração com frameworks

- **Spring**: binding e injeção via setters
- **Hibernate/JPA**: acesso a propriedades
- **Jackson**: conversão objeto ↔ JSON
- **JSP/JSF**: acesso por EL (`obj.propriedade` → `getPropriedade()`)
    

---

## O que JavaBeans não é

- Não é um DTO (apesar de frequentemente usado como)
- Não é uma Entity JPA (apesar de Entities seguirem JavaBeans)
- Não é Record
- Não é qualquer POJO
    

> JavaBean = POJO **com convenções explícitas**

---

## JavaBeans vs abordagens modernas

|Aspecto|JavaBeans|Records|
|---|---|---|
|Mutabilidade|Mutável|Imutável|
|Verbosidade|Alta|Baixa|
|Compatibilidade com frameworks|Muito alta|Parcial|
|Modelo mental|Orientado a estado|Orientado a valor|

> O ecossistema Java ainda depende fortemente de JavaBeans, apesar da evolução da linguagem.
 
---

## Frase de ancoragem

> JavaBeans é a convenção que transforma classes Java em componentes compreensíveis por máquinas — e escaláveis por arquiteturas.