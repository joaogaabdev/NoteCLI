#Frontend 
# Conceito

**Single Page Application** é um **modelo de aplicação web que carrega uma única página HTML** e **atualiza seu conteúdo dinamicamente via JavaScript**, sem recarregar a página inteira a cada navegação.
	Em vez de o servidor enviar uma nova página a cada clique, ele envia **dados em JSON** e o **frontend (via JavaScript)** reconstrói a interface dinamicamente.

### Exemplo prático

**Antes (modelo tradicional – MPA / Multi-Page Application):**

`Usuário → /home → servidor envia home.html`
`Usuário → /produtos → servidor envia produtos.html 
`Usuário → /contato → servidor envia contato.html`

**Agora (SPA):**

`Usuário → / → servidor envia index.html (uma vez)
`→ JavaScript manipula rotas e conteúdo dinamicamente (sem reload)`
`→ Fetch/axios pega dados via API → atualiza DOM virtual`
