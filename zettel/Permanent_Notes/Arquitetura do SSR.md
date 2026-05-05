#Frontend 

| Camada                 | Responsabilidade                                       | Exemplos                                   |
| ---------------------- | ------------------------------------------------------ | ------------------------------------------ |
| **Servidor (Backend)** | Executa o código do frontend e gera o HTML renderizado | Next.js, Nuxt.js, Remix, Angular Universal |
| **Cliente (Frontend)** | Hidrata o HTML e torna-o interativo                    | React, Vue, Angular                        |
| **API**                | Fornece dados ao servidor para renderização            | REST, GraphQL                              |
| **Build System**       | Gera bundles separados para _server_ e _client_        | Webpack, Vite, SWC                         |

### Fluxo geral do SSR

1. Usuário requisita `/produtos`.
    
2. O servidor executa o código React no Node.js.
    
3. O React monta o componente `Produtos` no servidor com os dados da API.
    
4. O HTML final é enviado pronto para o cliente.
    
5. O JavaScript do cliente hidrata o conteúdo, tornando-o interativo.