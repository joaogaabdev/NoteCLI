## 1. Fibra (óptica)

**Fibra** é o **meio físico em si** — o filamento de vidro (ou plástico) que conduz a luz.

- Núcleo (core) + revestimento (cladding)
    
- Responsável **exclusivamente** pela propagação óptica
    
- Não inclui proteção mecânica, capa ou estrutura
    

Em termos conceituais:

> Fibra ≠ cabo  
> Fibra é o “fio de luz”; o cabo é a armadura que o protege.

 Em livros como Tanenbaum, “fibra óptica” é tratada como **meio de transmissão**, não como produto de instalação.

---

## 2. Cabo Drop

**Cabo drop** é um **tipo específico de cabo de fibra**, projetado para o **último trecho da rede** (FTTH).

Características:

- Contém **uma ou duas fibras**
    
- Estrutura reforçada (mensageiro metálico ou dielétrico)
    
- Alta resistência mecânica
    
- Flexível e leve
    
- Projetado para:
    
    - Fachada
        
    - Poste → residência
        
    - Entrada no imóvel
        

Função clara:

> Conectar a rede do ISP até a ONT do cliente.

Se rompe o drop, **um cliente cai**.  
Se rompe um feeder, **um bairro cai**.

---

## 3. Emenda (fusão ou mecânica)

**Emenda** é o **processo de unir duas fibras ópticas**, mantendo a continuidade do sinal luminoso.

Tipos:

### Emenda por fusão

- Fusão térmica das fibras
    
- Menor perda óptica
    
- Mais confiável
    
- Padrão em ISPs profissionais

### Emenda mecânica

- União física sem fusão
    
- Maior perda
    
- Uso emergencial ou temporário
    

Conceito-chave:

> Emenda não é o ponto, é o processo.  
> O ponto físico é a **caixa de emenda**.

📉 Cada emenda adiciona **atenuação** ao enlace.

---

## 4. A.S (Acesso de Serviço)

**A.S** é o **ponto físico onde o drop do cliente é conectado à rede do ISP**.

Na prática, a A.S:

- Fica em:
    
    - CTO
        
    - Caixa de atendimento
        
    - Caixa de emenda próxima ao cliente
        
- Marca a **transição**:
    
    - Rede de distribuição → cliente
        
- É onde ocorre:
    
    - Emenda do drop
        
    - Ativação do cliente
        
    - Manutenção de acesso
        

Em termos operacionais:

> A A.S é o “portal” do cliente para a rede.

Problema na A.S costuma gerar:

- Sinal fraco
    
- Intermitência
    
- Cliente “online” mas sem tráfego
    

---

## 5. Comparação direta (para não confundir mais)

|Termo|O que é|Função|
|---|---|---|
|Fibra|Filamento óptico|Transportar luz|
|Cabo drop|Cabo com fibra|Levar a rede até o cliente|
|Emenda|Processo de união|Garantir continuidade óptica|
|A.S|Ponto de acesso|Conectar cliente à rede|

---

## 6. Regra de ouro de campo (vale anotar)

> 🔦 **Fibra conduz, cabo protege, emenda conecta e a A.S entrega.**

Se você domina essa frase, domina 80% da conversa técnica com cliente, técnico e NOC.