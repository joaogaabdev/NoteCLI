Referees: #Backend 

O versionamento de código nasceu para resolver três grandes problemas no desenvolvimento de software: 
* ***Perda de trabalho*** quando várias pessoas editavam o mesmo arquivo.
* ***Ausência de histórico auditável***, dificultando saber quem, quando e por que uma alteração foi feita; 
* ***Dificuldade em trabalhar com múltiplas versões*** ou ramificações (branches) sem comprometer a estabilidade da linha principal do código. 

Antes de explorar a evolução dos sistemas, precisamos entender dois conceitos essenciais: **árvores** e **deltas**.

#### Conceito de Árvore
No versionamento, uma _árvore_ representa a estrutura hierárquica de arquivos e diretórios de um projeto.  
Ela permite registrar:
- nomes dos arquivos
- pastas
- metadados
- o estado completo do projeto em um determinado momento

No Git, cada commit é um snapshot dessa árvore, formado por:
- **blobs** (conteúdo dos arquivos)
- **trees** (diretórios)
- **links** entre árvores e blobs

Isso é o que torna o Git capaz de “fotografar” o projeto inteiro de forma confiável e eficiente.

___ 
#### Conceito de Delta

Delta é a diferença entre duas versões de um arquivo.  
Em vez de armazenar o arquivo completo sempre que algo muda, o sistema registra apenas as alterações, economizando espaço e acelerando operações.

O RCS popularizou a técnica de **deltas reversos**, onde:

- a **versão mais recente** é armazenada por completo
- versões antigas são reconstruídas aplicando “deltas para trás”

Isso torna o acesso à versão atual rápido, crucial para desenvolvedores.

___
# Linha do Tempo: Dos Anos 1970 ao Git (2005)
## SCCS  (1972-1975) 

O _Source Code Control System_ foi o primeiro sistema amplamente utilizado.  
Era:

- **local** (um único computador)
- **por arquivo**
- possuía _check-in/check-out_ primitivo
- focado em controle de revisões, não em colaboração

Foi pioneiro, mas não atendia projetos maiores ou equipes distribuídas.

___ 

## RCS (Revision Control System, Walter Tichy, 1982)

O _Revision Control System_ trouxe o primeiro grande salto técnico.
### Inovações:

- armazenamento eficiente com **deltas reversos**
- histórico robusto por arquivo
- padronização de comandos (**ci**, **co**)
- recuperação rápida da versão atual

### Limitações:

- versionamento **apenas por arquivo**, não da árvore inteira
- sem commits atômicos envolvendo múltiplos arquivos
- colaboração extremamente limitada

Ainda assim, foi revolucionário para seu tempo.

___
## CVS (Concurrent Versions System, final dos anos 80 / 1990)

O _Concurrent Versions System_ surge para superar o maior problema do RCS: a falta de colaboração.
### Inovações:

- arquitetura **cliente-servidor**
- suporte a múltiplos desenvolvedores simultâneos
- integração de projetos com vários arquivos

### Limitações:

- **commits não são atômicos** — se um conjunto de arquivos falha no meio, o repositório pode ficar inconsistente
- diretórios não eram versionados
- branching e merging eram lentos e complexos
- dependência completa do servidor central

Foi importante para o software livre, mas carregava fraquezas estruturais.

___ 

## Subversion (SVN, lançado em 2000)

Criado como “CVS melhorado”, o Subversion corrigiu quase todas as falhas do CVS.
### Inovações:

- **commits atômicos** envolvendo toda a árvore
- versionamento de diretórios, renomeações e metadados
- arquitetura cliente-servidor mais estável
- merges mais previsíveis
### Limitações:

- ainda centralizado
- continua dependente do servidor
- branches custosos em comparação a DVCS

O SVN dominou a indústria por quase uma década.

___ 
## A transição para sistemas distribuídos (DVCS)

O mundo do software se tornou **global e massivo**, e isso exigia:

- trabalho offline
- operações locais instantâneas
- eliminação do “ponto único de falha”
- branching barato
- merges frequentes e seguros

O BitKeeper foi o primeiro DVCS amplamente usado (especialmente no Linux), mas era proprietários — algo incompatível com a filosofia do software livre.

Quando seu licenciamento mudou, Linus Torvalds decidiu criar uma solução totalmente nova.

___

## Git (2005): design, funcionamento e inovações

Linus Torvalds projetou o Git com quatro princípios imutáveis:

1. **Velocidade absurda**
2. **Modelo totalmente distribuído**
3. **Integridade garantida por hashes (SHA-1)**
4. **Branching e merging extremamente baratos**

### O Git abandonou o modelo baseado apenas em deltas.

Em vez disso:

> Cada commit é um snapshot completo da árvore de arquivos — mas _somente_ os arquivos alterados geram novos blobs, reaproveitando os demais.

### Os pilares do Git:

- repositório local completo (histórico inteiro disponível offline)
- commits atômicos e rápidos
- branches como **ponteiros leves**
- merges poderosos e estruturados
- segurança via hash criptográfico
- escalabilidade para milhares de colaboradores

Foi criado em semanas, e o primeiro commit do Git foi em **7 de abril de 2005**.
Hoje, é a base do GitHub, GitLab, Bitbucket e praticamente todo o desenvolvimento mundial.



### Funcionamento do Git

#### 1. Repositório e Commits

- snapshot da árvore completa
- objetos reutilizáveis (blobs e trees) para economizar espaço
#### 2. Branches (Ramificações)

- ponteiros móveis
- criação e troca rápidas
- modelo ideal para desenvolvimento paralelo
#### 3. Estados do Arquivo no Git 

1. **Working directory**
2. **Staging area**
3. **Repository**

Esse fluxo impede gravações acidentais e permite granularidade nas mudanças.
## Principais comandos Git

``` git
git clone: cria uma cópia local de um repositório remoto.
    
git branch: listar, criar ou deletar branches.
    
git checkout: trocar entre branches.
    
git add: preparar arquivos para commit (staging).
    
git commit: salvar alterações locais com mensagem descritiva.
    
git push: enviar commits locais para o repositório remoto.
    
git pull: atualizar repositório local com mudanças remotas.
    
git merge: incorporar mudanças de uma branch em outra.
    
```

## Tipos de Sistemas de Versionamento

| Categoria                                                    | Descrição                                                                                                                                                                                                                                                                                                                                            | Exemplo                                            |
| ------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------- |
| Local (LVCS - Local Version Control System)                  | Sistema que mantém um banco de dados de versões apenas localmente, no computador do desenvolvedor. Não suporta colaboração eficiente, pois o histórico não é compartilhado nem sincronizado. Útil para projetos individuais e controle básico de versões.<br>                                                                                        | RCS (Revision Control System), SCCS                |
| Centralizado (CVCS - Centralized Version Control System)<br> | Sistema que utiliza um servidor central para armazenar todo o histórico de versões do projeto. Desenvolvedores obtêm cópias de trabalho locais e sincronizam através de operações de "checkout" (retirada) e "commit" (envio). Suporta trabalho colaborativo, mas depende do servidor, que é ponto único de falha e gargalo potencial.<br>           | CVS (Concurrent Versions System), Subversion (SVN) |
| Distribuído (DVCS - Distributed Version Control System)<br>  | Cada desenvolvedor possui uma cópia completa do repositório, incluindo todo o histórico de alterações. Operações como commits são feitas localmente, permitindo trabalhar offline e com alta velocidade. A sincronização entre repositórios é feita por push/pull. Oferece maior segurança, flexibilidade e suportabilidade em equipes distribuídas. | Git, Mercurial, Bazaar                             |

## Comparação entre sistemas

| Sistema | Modelo       | Unidade de Versionamento   | Commit                     | Branching/Merging | Escalabilidade/Colaboração                      |
| ------- | ------------ | -------------------------- | -------------------------- | ----------------- | ----------------------------------------------- |
| RCS     | Local        | Por arquivo                | Atômico por arquivo        | Limitado          | Trabalho local, pouca colaboração               |
| CVS     | Centralizado | Por arquivo                | Não atômico entre arquivos | Frágil e caro     | Suporte básico para múltiplos colaboradores     |
| SVN     | Centralizado | Árvore inteira + metadados | Atômico por commit         | Melhor que CVS    | Centralizado, dependente do servidor            |
| Git     | Distribuído  | Snapshot da árvore         | Atômico local              | Rápido e barato   | Trabalho offline, múltiplas branches frequentes |

# Fontes

- "A History of Source Control Systems: SCCS and RCS (Part 1)", 2024. Explora os primeiros sistemas como SCCS e o desenvolvimento do RCS por Walter Tichy, destacando o uso de deltas reversos. [experimentalworks.net][](https://experimentalworks.net/posts/2024-03-18-a-history-of-vcs-part1/)​
    
- "Revision Control Systems" (Trabalho técnico). Descreve os conceitos fundamentais do SCCS e RCS, delta storage, versionamento por arquivo, e registro de revisões. [aserebre.win.tue.nl][](https://aserebre.win.tue.nl/2IS55/2009-2010/stijn.pdf)​
    
- "Concurrent Versioning System (CVS)" – Documentação sobre funcionamento cliente-servidor do CVS, suas operações e limitações. [slac.stanford.edu][](https://www.slac.stanford.edu/exp/glast/wb/prod/pages/softwareOverview/cvsBasics.htm)​
    
- "Version Control with Subversion (SVN Book)", CollabNet / O’Reilly, 2002. Livro clássico sobre SVN, explicando sua arquitetura, commits atômicos, versionamento de diretórios e metadados. [svnbook.red-bean.com][](https://svnbook.red-bean.com/en/1.7/svn-book.pdf)​
    
- "Git" – História do Git desde sua criação em 2005 por Linus Torvalds e design focado em desempenho, integridade e operações locais rápidas. [Wikipedia][](https://en.wikipedia.org/wiki/Git)​
    
- "Centralized Vs Distributed Version Control" (GeeksforGeeks, 2019). Análise comparativa das arquiteturas CVCS e DVCS, destacando vantagens técnicas e limitações. [geeksforgeeks.org][](https://www.geeksforgeeks.org/git/centralized-vs-distributed-version-control-which-one-should-we-choose/)​
    
- "What is Commit? What does it do?" (TechCareer.net, 2024). Explica a operação commit, sua importância para rastreamento e colaboração em software. [techcareer.net][](https://www.techcareer.net/en/dictionary/commit)​
    
- "Git Basic Commands" (W3Schools). Tutorial prático dos comandos essenciais do Git, desde a inicialização, criação de branches, commits e envio para repositórios remotos. [w3schools.in][](https://www.w3schools.in/git/basic-commands)​
    
- "Version control" (Wikipedia, 2002). Panorama histórico dos sistemas de controle de versão e evolução conceitual. [Wikipedia][](https://en.wikipedia.org/wiki/Version_control)​
    
- "RCS—A System for Version Control" (Artigo original de Walter F. Tichy). Paper fundacional que detalha o design do RCS e conceitos fundamentais de versionamento. [gnu.org]