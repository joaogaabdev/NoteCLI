#Frontend 

O **Virtual DOM (VDOM)** é uma **cópia leve do DOM real** mantida na memória, usada por bibliotecas como **React** e **Vue** para otimizar atualizações na interface.

Em vez de mexer diretamente no DOM real, o React:

1. Mantém uma versão virtual (um _snapshot_ do estado atual da UI).
    
2. Gera uma nova versão quando o estado muda.
    
3. Compara as duas (processo de _diffing_).
    
4. Atualiza **apenas as partes que mudaram** no DOM real.

## Ciclo simplificado do Virtual DOM
```
[1] Estado muda
     ↓
[2] React cria uma nova árvore Virtual DOM
     ↓
[3] Compara com a árvore anterior (diff)
     ↓
[4] Envia mudanças mínimas para o DOM real (patch)
```
