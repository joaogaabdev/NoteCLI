# Notes-Terminal

# 🧠 Zettel Terminal — Knowledge System with Zettelkasten + MOCs

Um sistema de gerenciamento de conhecimento baseado em **Zettelkasten** e **Maps of Content (MOCs)**, operando diretamente no terminal, com armazenamento em arquivos Markdown e versionamento via GitHub.

A proposta é simples: criar uma alternativa leve, escalável e independente de ferramentas proprietárias, mantendo total controle sobre suas notas.

---

## 🚀 Motivação

Ferramentas como Obsidian são excelentes, mas possuem limitações no plano gratuito, especialmente em sincronização entre dispositivos.

Este projeto resolve isso através de:

* Armazenamento local em arquivos `.md`
* Sincronização via GitHub
* Uso direto no terminal (Nano, Vim, etc.)
* Estrutura escalável e extensível

---

## 🧱 Estrutura do Projeto

```bash
zettel/
├── notes/        # Notas atômicas (Zettelkasten)
├── mocs/         # Mapas de conteúdo (índices)
├── tags/         # Agrupamentos por tema
└── index.md      # Entrada principal
```

---

## 📝 Formato das Notas

Cada nota segue um padrão simples:

```md
# Título da Nota

ID: 202604231030  
Tags: #backend #java

## Conteúdo
Explicação ou ideia principal da nota.

## Links
- [[202604231045]]
- [[engenharia_software]]
```

### 🔑 Princípios

* Cada nota representa **uma única ideia**
* Links são feitos via `[[ID ou nome]]`
* Notas devem ser **pequenas, claras e conectáveis**

---

## 🧭 MOCs (Maps of Content)

MOCs funcionam como hubs de navegação:

```md
# Engenharia de Software

## Tópicos
- [[arquitetura]]
- [[design_patterns]]
- [[clean_code]]

## Notas relacionadas
- [[202604231030]]
```

---

## 🔗 Backlinks no Terminal

Para encontrar quais notas apontam para uma específica:

```bash
grep -R "202604231030" .
```

Ou usando ferramentas mais avançadas:

```bash
rg "202604231030" | fzf
```

---

## ⚙️ Fluxo de Uso

### Criar nova nota

```bash
nano notes/$(date +%Y%m%d%H%M).md
```

### Buscar nota

```bash
rg "termo"
```

### Navegar entre notas

* Abrir manualmente pelo ID
* Ou usar `fzf` para seleção interativa

---

## 🔄 Sincronização com GitHub

```bash
git add .
git commit -m "nova nota"
git push
```

Benefícios:

* Backup automático
* Histórico de aprendizado
* Acesso multi-dispositivo

---

## 🧠 Arquitetura Conceitual

O sistema funciona como um **grafo de conhecimento**, onde:

* Cada nota = um nó
* Cada link = uma conexão

---

## ⚠️ Nota sobre implementação em Java

Embora uma LinkedList possa parecer útil inicialmente, este sistema é melhor representado como um **grafo direcionado**.

Exemplo de estrutura ideal:

```java
class Note {
    String id;
    String content;
    List<String> links;
}
```

Estrutura principal:

```java
Map<String, Note> graph;
```

---

## 🚀 Roadmap do Projeto

### Fase 1 — Terminal puro

* Markdown + Nano/Vim
* grep / ripgrep
* GitHub sync

### Fase 2 — CLI customizado

* Comandos como:

  * `zettel create`
  * `zettel link`
  * `zettel backlinks`

### Fase 3 — Automações

* Parser de links `[[...]]`
* Geração automática de backlinks
* Visualização de grafo

### Fase 4 — Inteligência

* Sugestão de conexões
* Ranking de notas
* Análise semântica

---

## 💡 Filosofia

> Conhecimento não é uma lista. É uma rede.

Este projeto transforma suas anotações em um sistema vivo, navegável e evolutivo.

---

## 🧩 Possíveis Extensões

* Integração com Graphviz para visualização
* Interface web leve
* Indexação com ElasticSearch
* API REST em Java (Spring)

---

## 📌 Conclusão

Você não precisa de uma ferramenta complexa para ter um sistema poderoso de conhecimento.

Com:

* arquivos simples
* links explícitos
* e disciplina

…você constrói algo tão poderoso quanto (ou mais) que ferramentas pagas.

---

## 🛠️ Licença

MIT — use, modifique e evolua livremente.

---

## ✨ Autor

Projeto idealizado como alternativa open-source para gerenciamento de conhecimento pessoal via terminal.
