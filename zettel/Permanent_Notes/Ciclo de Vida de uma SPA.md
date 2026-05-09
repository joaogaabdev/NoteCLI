#Frontend 

- **Primeiro carregamento (Initial Load)**  
    O navegador baixa `index.html`, `bundle.js` e `bundle.css`.  
    Isso monta a estrutura inicial e carrega o JavaScript da aplicação.
    
- **Renderização inicial**  
    O JS gera a interface usando o Virtual DOM.
    
- **Navegação interna (Client-side Routing)**  
    Ao clicar em links, a aplicação **não faz requisições de página**, apenas altera a rota e atualiza o componente correspondente.
    
- **Comunicação com o servidor (API calls)**  
    Fetch ou Axios buscam dados em endpoints REST/GraphQL, atualizando o estado e re-renderizando a UI.
    
- **Atualização dinâmica (Re-render)**  
    O Virtual DOM compara o estado antigo e o novo, aplicando apenas as mudanças necessárias no DOM real (alta performance).
