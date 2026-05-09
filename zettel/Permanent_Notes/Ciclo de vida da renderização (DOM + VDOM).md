#Frontend 

1. **Inicialização**
    
    - O framework monta o Virtual DOM e o transforma no DOM real.
        
2. **Mudança de estado**
    
    - Uma ação do usuário (ex: clique) altera o estado interno.
        
3. **Re-renderização virtual**
    
    - O Virtual DOM é recriado na memória.
        
4. **Diffing**
    
    - O React compara a nova e antiga árvore virtual.
        
5. **Patching**
    
    - Só as diferenças são aplicadas no DOM real.
        
6. **Commit**
    
    - O navegador re-renderiza as partes afetadas.