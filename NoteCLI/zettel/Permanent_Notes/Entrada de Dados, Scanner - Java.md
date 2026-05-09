#Java 

Para fazer uma entrada de dados(input) em Java, é necessário criar um objeto do tipo **"Scanner"** da seguinte forma:

``` java
Scanner sc = new Scanner(System.in);
```

Para essa entrada funcionar, será necessário colocar no início do programa p seguinte código:

``` java
import java.util.Scanner;
```

Para encerrar a entrada de dados, use:
``` java
sc.close()
```

Exemplo de código de importação e uso do Scanner:

```java
import java.util.Scanner;

public class Main {

	public static void main(String[] args) {
	
	Scanner sc - new Scanner(System.in);
	
	String x;
	x = sc.next(); 
	sc.close()
	}
}
```

## Tabela de entrada de dados (Scanner – Java)

### Strings

| Tipo   | Método        | Observação                             |
| ------ | ------------- | -------------------------------------- |
| `String` | `sc.next()`     | Lê até o próximo espaço.               |
| `String` | `sc.nextLine()` | Lê a linha inteira(incluindo espaços). |
### Inteiros


| Tipo  | Método         |
| ----- | -------------- |
| `byte`  | `sc.nextByte()`  |
| `short` | `sc.nextShort()` |
| `int`   | `sc.nextInt()`   |
| `long`  | `sc.nextLong()`  |

### Números de ponto flutuante(float)


| Tipo     | Método            | Observação                                |
| -------- | ----------------- | ----------------------------------------- |
| `float`  | `sc.nextFloat()`  | Usa vírgula ou ponto dependendo do locale |
| `double` | `sc.nextDouble()` | Mesmo esquema do float                    |

> Se o usuário digitar “3,14” em um sistema com *locale* americano, vai dar erro.  
> Pode resolver com:

``` java
public class Main {

	public static void main(String[] args) {
	Locale.setDefault(Locale.US);
	}
}
```

## Booleanos 


| Tipo      | Método             | Aceita            |
| --------- | ------------------ | ----------------- |
| `boolean` | `sc.nextBoolean()` | `true` ou `false` |
