
Commits semânticos são uma convenção de escrita de mensagens de commit que descrevem **claramente a intenção da mudança**, permitindo leitura rápida, automação e melhor rastreabilidade.

Eles seguem um padrão estruturado:

```
<tipo>(escopo opcional): <descrição curta> 
```

---

### Por que isso é útil?

1. **Legibilidade imediata**
    - Dá pra entender o histórico sem abrir o código
2. **Automação**
    - Geração automática de changelog
    - Versionamento semântico (SemVer)
    - CI/CD mais inteligente
3. **Colaboração**
    - Times grandes conseguem navegar no histórico com eficiência
4. **Debug mais rápido**
    - Encontrar regressões vira quase uma busca por palavra-chave

---

### Tipos principais de commit

#### feat → nova funcionalidade

Usado quando você adiciona algo novo ao sistema

```
git commit -m "feat: adiciona cadastro de usuário"
```

Com escopo:

```
git commit -m "feat(auth): adiciona login com JWT"
```

---

#### fix → correção de bug

Quando algo que estava quebrado foi corrigido

```
git commit -m "fix: corrige erro ao calcular total do carrinho"
```

---

#### chore → tarefas internas / manutenção

Não afeta diretamente o comportamento da aplicação

```
git commit -m "chore: atualiza dependências do projeto"
```

---

#### docs → documentação

Alterações apenas em documentação

```
git commit -m "docs: adiciona instruções de instalação no README"
```

---

#### style → formatação / estética

Não altera lógica (espaço, indentação, ponto e vírgula, etc.)

```
git commit -m "style: ajusta indentação do controller"
```

---

#### refactor → refatoração

Melhoria de código sem mudar comportamento

```
git commit -m "refactor: simplifica lógica de validação de CPF"
```

---

#### perf → melhoria de performance

```
git commit -m "perf: otimiza consulta ao banco com índice"
```

---

#### test → testes

```
git commit -m "test: adiciona testes para serviço de pagamento"
```

---

#### remove → remoção de código

```
git commit -m "remove: exclui método legado de autenticação"
```

---

### Commits com BREAKING CHANGE

Quando você quebra compatibilidade:

```
git commit -m "feat: altera estrutura da API

BREAKING CHANGE: endpoints antigos foram removidos"
```

---

### 📏 Boas práticas

- Use verbo no presente ("adiciona", "corrige", não "adicionou")
- Seja específico, mas curto
- Evite commits genéricos tipo:
    
    ```
    git commit -m "ajustes"
    ```
    
    (isso é praticamente um crime de guerra em times grandes)
    

---

### Exemplo real de sequência de commits

```
feat(user): adiciona endpoint de cadastro
fix(user): corrige validação de email duplicado
refactor(user): separa lógica de serviço e controller
test(user): adiciona testes de integração
```

Isso conta uma história completa do desenvolvimento.

---

### Implementação prática no dia a dia

1. **Padronize no time**
2. Use ferramentas como:
    - commitlint
    - husky (para validar commits automaticamente)
3. Crie templates de commit:
    
    ```
    git config commit.template .gitmessage
    ```
    

---