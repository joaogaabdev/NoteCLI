#Frontend 

Um documento HTML simples:
``` html
<html>
  <body>
    <h1>Olá, João!</h1>
    <button id="btn">Clique aqui</button>
  </body>
</html>
```

É transformado internamente em uma árvore de objetos:

``` html
Document
└── html
    └── body
        ├── h1
        │    └── "Olá, João!"
        └── button#btn
             └── "Clique aqui"
```


