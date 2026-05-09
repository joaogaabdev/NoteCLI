Referees: #Java 
Sintaxe opcional para percorrer coleções 
Sintaxe:
```java
fpr (tipo apelido : coleção) {
	<comando1>
	<comando2>
} 
```

For:
```java
String[] vect = new String[] {"Maria", "Bob", "Alex"};

for (int i = 0; i < vect.length; i++) {
	System.out.println(vect[i]);
}
```

For each:
```java
String[] vect = new String[] {"Maria", "Bob", "Alex"};

for (String obj : vect) {
	System.out.println(obj);
}
```

