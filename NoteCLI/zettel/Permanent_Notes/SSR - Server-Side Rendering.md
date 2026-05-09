#Frontend 
# Conceito

**Server-Side Rendering (SSR)** é o processo de **renderizar o HTML completo da aplicação no servidor**, antes de enviá-lo ao navegador.  
Ou seja, o servidor gera a página **já pronta** com conteúdo, e o cliente apenas exibe — sem depender de JavaScript para montar a interface inicial.

Em outras palavras:

> O **SSR** gera o HTML no **servidor**.  
> O **CSR (Client-Side Rendering)** gera o HTML no **navegador**.

## Exemplo prático

### Client-Side Rendering (SPA)

- O navegador recebe um `index.html` vazio.
    
- Carrega `bundle.js` e monta tudo via JavaScript.
    
- Bots de SEO (como o Googlebot) podem ter dificuldade em indexar.
    

## Server-Side Rendering (SSR)

- O servidor executa o código React/Vue/Angular no servidor.
    
- Gera um HTML completo e já renderizado.
    
- O navegador exibe instantaneamente o conteúdo.
    
- O JavaScript no cliente “hidrata” esse HTML (liga os eventos e torna interativo).