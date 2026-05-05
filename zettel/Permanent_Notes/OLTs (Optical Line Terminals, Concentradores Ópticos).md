## 1. O que é uma OLT (visão de redes de computadores)

A **OLT (Optical Line Terminal)** é o **equipamento central da rede FTTH** responsável por:

- Agregar tráfego IP da rede do provedor
- Converter sinais elétricos (Ethernet/IP) em **sinais ópticos**
- Distribuir esse sinal para centenas ou milhares de clientes
- Controlar autenticação, banda, QoS, VLANs, multicast, etc.
    

> Em redes de computadores, a OLT exerce um papel análogo a:

- **Switch L3 + Access Concentrator**
- Controlando múltiplos “clientes” (ONUs/ONTs) em um meio compartilhado
    

Ela fica instalada no **POP**.

---

## 2. O que é um POP (Point of Presence)

Um **POP** é o ponto físico onde o provedor concentra sua infraestrutura:

- OLTs
- Roteadores de borda (BGP)
- Switches
- Servidores
- Sistemas de energia (UPS, retificadores)
- Backhaul (fibra, rádio, IX)
    

Em termos de arquitetura de redes:

- O POP é o **núcleo de acesso**
- A OLT é o **gateway FTTH**
- As ONTs são os **hosts finais**
    

---

## 3. Arquitetura básica de uma rede FTTH (PON)

```Markdown
Internet   
 ↓ 
Roteador de Borda    
 ↓ 
OLT (POP)    
 ↓ 
Fibra feeder    
 ↓ 
Splitter(s)    
 ↓ 
Fibra de distribuição    
 ↓ 
CTO    
 ↓ 
Drop    
 ↓
ONT (Cliente)
```


Tudo isso funciona em **PON — Passive Optical Network**, ou seja:
- Não há equipamentos ativos entre OLT e cliente
- Apenas fibra + splitters passivos
    

---

## 4. Tecnologias de OLT / PON

### 4.1 GPON (Gigabit Passive Optical Network)

**A mais comum no Brasil**

**Características:**

- Downstream: **2,5 Gbps**
- Upstream: **1,25 Gbps**
    
- Comprimento de onda:
    - Down: **1490 nm**
    - Up: **1310 nm**
        
- Alcance típico: até **20 km**
- Split comum: **1:16, 1:32, 1:64**
    

**Funcionamento:**

- Downstream: **broadcast**
- Upstream: **TDMA (Time Division Multiple Access)**
    
 A OLT decide quando cada ONU pode falar (controle de tempo).

---

### 4.2 EPON (Ethernet PON)

**Baseada diretamente em Ethernet (IEEE 802.3ah)**

**Características:**

- Downstream: **1 Gbps**
- Upstream: **1 Gbps**
	- Comprimento de onda:
	    - Down: **1490 nm**
	    - Up: **1310 nm**
- Mais simples que GPON
- Menos usada em ISPs grandes
    
 Boa para redes menores ou legadas.

---

### 4.3 GEPON (Gigabit Ethernet PON)

Muitas vezes tratado como sinônimo de EPON

**Características:**

- 1 Gbps simétrico
- Ethernet nativa
- Menos overhead de protocolo
- Menos recursos avançados que GPON
    

---

### 4.4 XPON (conceito geral)

**XPON não é uma tecnologia específica**, mas um **guarda-chuva**:

Inclui:

- GPON
- XG-PON
- XGS-PON
- 10G-PON
- 25G-PON
    

Indica redes PON de **nova geração**.

---

### 4.5 XG-PON / XGS-PON

|Tecnologia|Downstream|Upstream|
|---|---|---|
|XG-PON|10 Gbps|2,5 Gbps|
|XGS-PON|10 Gbps|10 Gbps|

**Comprimentos de onda:**

- Down: **1577 nm**
- Up: **1270 nm**
    

**Compatível com GPON na mesma fibra** (overlay)

Ideal para planos de:

- 1 Gbps
- 2 Gbps
- Empresas
- Backhaul celular
    

---

## 5. Divisão de uma porta da OLT (Split Ratio)

Cada **porta PON da OLT** alimenta **vários clientes** por splitters.

### Exemplo clássico: GPON

- 1 porta GPON → **2,5 Gbps down**
- Split 1:32 → até **32 ONTs**
    

```markdown
OLT (1 porta)    
 ↓ 
Splitter 1:4    
 ↓ 
Splitter 1:8    
 ↓ 
CTOs
```

Split total:

`1 × 4 × 8 = 32 clientes`

---

## 6. Cálculo de quantos clientes uma porta atende

### 6.1 Cálculo por largura de banda (engenharia de tráfego)

Exemplo:

- Porta GPON: **2,5 Gbps**
- Clientes: planos de **300 Mbps**
    

Oversubscription (razão típica): **1:8 a 1:16**

```Markdown
300 Mbps × 32 = 9,6 Gbps (teórico) 
Mas: - Nem todos usam ao mesmo tempo - A OLT controla QoS
```

Na prática:

- 1:32 é seguro
- 1:64 exige bom dimensionamento
    

---

### 6.2 Cálculo por potência óptica (mais crítico)

Aqui entra a física

---

## 7. Potência óptica e orçamento (Optical Budget)

### Classes GPON comuns:

|Classe|Potência Máx|Alcance|
|---|---|---|
|B+|~28 dB|Curto|
|C+|~32 dB|Médio|
|C++|~35 dB|Longo|

---

### Atenuação típica

- Fibra: **~0,35 dB/km**
- Conector: **0,2 a 0,5 dB**
- Emenda: **0,1 dB**
- Splitter:
    - 1:2 → ~3,5 dB
    - 1:4 → ~7,2 dB
    - 1:8 → ~10,5 dB
    - 1:16 → ~13,5 dB
    - 1:32 → ~17 dB
        

---

### Exemplo de cálculo de potência

- Distância: 10 km → **3,5 dB**
- Split total: 1:32 → **17 dB**
- Conectores/emendas: **3 dB**
    

**Total:**

`3,5 + 17 + 3 = 23,5 dB`

Funciona tranquilo em:

- GPON B+    
- GPON C+
    

---

## 8. Downstream vs Upstream (fibra única)

📌 **Uma única fibra transporta ambos**

### Como isso funciona?

- **WDM (Wavelength Division Multiplexing)**
    

|Sentido|Comprimento|
|---|---|
|Downstream|1490 nm|
|Upstream|1310 nm|
|Vídeo RF (legado)|1550 nm|

👉 A fibra é a mesma, a luz é diferente.

---

## 9. Do POP até o cliente — fluxo do sinal

1. **OLT gera o sinal óptico**
2. Fibra feeder leva até o splitter primário
3. Splitters dividem a potência
4. Fibra de distribuição chega às CTOs
5. CTO divide para drops
6. Drop chega à ONT
7. ONT converte óptico → Ethernet/IP
    

A OLT:
- Identifica ONTs por **SN ou LOID**
- Controla banda, VLAN, prioridade
- Decide quando cada ONT transmite (upstream)
    

---

## 10. Relação direta com redes de computadores

FTTH não é “só fibra”. É rede pura:

- IP
    
- VLAN
    
- QoS
    
- Multicast
    
- Controle de acesso
    
- Oversubscription
    
- Engenharia de tráfego
    

👉 A fibra é o **meio físico**  
👉 A OLT é o **equipamento de acesso**  
👉 O POP é o **nó da rede**

---

## 11. Resumo mental (mapa rápido)

```Markdown
POP  
 ├─ Roteadores  
 ├─ Switches  
 └─ OLT      
	 ├─ Portas PON      
	 │   ├─ Splitters      
	 │   │   └─ CTOs      
	 │   │         └─ ONTs      
	 │   └─ Controle de banda      
	 └─ Gerência IP
```

