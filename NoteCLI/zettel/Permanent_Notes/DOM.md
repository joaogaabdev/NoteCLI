#Frontend 

O **DOM (Document Object Model)** é uma **representação em árvore de todos os elementos HTML de uma página web**.  
Ele traduz o código HTML em uma estrutura manipulável por **JavaScript**, **CSS** e **navegadores**.

## Como o DOM funciona

1. O **parser do navegador** lê o HTML.
    
2. Cria uma **árvore de nós** (`document`, `element`, `text`, etc.).
    
3. Cada nó pode ser acessado ou alterado com **JavaScript** (via `document.getElementById`, `querySelector`, etc.).
    
4. Quando o DOM é alterado, o navegador **re-renderiza** parte da tela (_reflow_ + _repaint_).
    
