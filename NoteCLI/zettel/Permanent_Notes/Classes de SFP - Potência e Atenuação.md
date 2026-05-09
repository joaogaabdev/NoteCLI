## 1. O que é um SFP (no contexto correto)

**SFP (Small Form-factor Pluggable)** é um **transceptor óptico** responsável por:

- Converter sinal elétrico ↔ óptico
- Determinar **potência de transmissão**
- Definir **sensibilidade de recepção**
- Limitar o **alcance máximo do enlace**
    

👉 Em outras palavras:

> **Quem manda no alcance do link não é a fibra — é o SFP.**

---

## 2. Por que existem classes de SFP

Classes como **B+, C, C+, C++** indicam **faixas de potência e sensibilidade**, padronizando:

- Distância suportada
- Orçamento óptico máximo
- Cenários de uso (acesso, distribuição, backbone)
    

Essas classes são comuns em:

- GPON
- EPON
- Enlaces ópticos Ethernet
    

---

## 3. Conceito-chave: orçamento óptico

> **Orçamento óptico = Potência transmitida − Sensibilidade do receptor**

Ele representa a **perda máxima (em dB)** que o enlace pode ter sem cair.

Quanto maior a classe, **maior o orçamento**, não necessariamente a distância física.

---

## 4. Classes de SFP — visão comparativa

### Classe B+

- **Tx:** ~ +1 a +5 dBm 
- **Rx (mín):** ~ −27 dBm
- **Orçamento:** ~ 28 dB
- **Alcance típico:** até 20 km
    

**Uso comum:**

- FTTH urbano
- GPON padrão
- Redes de acesso curtas
    

 É o “default” dos ISPs.

---

### Classe C

- **Tx:** ~ +3 a +7 dBm
- **Rx (mín):** ~ −30 dBm
- **Orçamento:** ~ 32 dB
- **Alcance típico:** até 30 km
    

**Uso comum:**

- Redes com mais splitters
- Áreas suburbanas
- Topologias mais densas
    

---

### 🔹 Classe C+

- **Tx:** ~ +5 a +9 dBm
- **Rx (mín):** ~ −32 dBm
- **Orçamento:** ~ 35 dB
- **Alcance típico:** até 40 km
    

**Uso comum:**

- FTTH rural
- Longos trechos de feeder
- Enlaces com alta atenuação acumulada
    

---

### Classe C++

- **Tx:** ~ +7 a +11 dBm
- **Rx (mín):** ~ −35 dBm
- **Orçamento:** ~ 38 dB
- **Alcance típico:** até 60 km
    

**Uso comum:**

- Backbones ópticos
- Regiões remotas
- Topologias críticas
    

⚠️ Exige cuidado com **saturação** em enlaces curtos.

---

## 5. Tabela comparativa rápida

|Classe|Tx (dBm)|Rx mín (dBm)|Orçamento (dB)|Uso típico|
|---|---|---|---|---|
|B+|+1 a +5|−27|~28|FTTH urbano|
|C|+3 a +7|−30|~32|FTTH denso|
|C+|+5 a +9|−32|~35|FTTH rural|
|C++|+7 a +11|−35|~38|Backbone|

---

## 6. Relação com atenuação da fibra

A atenuação típica da fibra monomodo:

- ~0,35 dB/km (1310 nm)
- ~0,22 dB/km (1550 nm)
    

Mas o vilão real são:

- Splitters (ex: −13,5 dB em 1:16)
- Conectores (−0,2 dB)
- Emendas (−0,05 a −0,3 dB)
    

Quanto mais splitters e emendas, **maior a classe necessária**.

---

## 7. Erros comuns em ISPs

❌ Usar C++ em enlace curto  
→ saturação de ONT

❌ Usar B+ em topologia longa  
→ sinal instável no limite

❌ Pensar só em km  
→ ignorar splitters e perdas passivas

**Classe de SFP se escolhe por orçamento, não por distância.**