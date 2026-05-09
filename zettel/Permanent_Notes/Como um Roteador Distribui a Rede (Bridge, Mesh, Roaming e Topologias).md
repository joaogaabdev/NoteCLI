## 1. Papel do roteador na rede (visão de redes de computadores)

Um **roteador** é o elemento que:
- Conecta **redes diferentes** (WAN ↔ LAN)
- Distribui endereços IP (DHCP)
- Realiza **NAT**
- Controla tráfego (firewall, QoS)
- Pode atuar também como **Access Point Wi-Fi**
    

Em termos de camadas:
- Atua principalmente na **Camada 3 (Rede)**
- O Wi-Fi opera na **Camada 2 (Enlace)**
    

---

## 2. Funções principais de um roteador doméstico/ISP

Um único equipamento geralmente acumula várias funções:

```json
[ Internet ]      
 ↓ 
[ Modem / ONU ]
 ↓ 
[ Roteador ]    
 ├─ NAT    
 ├─ DHCP    
 ├─ Firewall    
 ├─ Switch (LAN)    
 └─ Access Point (Wi-Fi)
```

Isso explica por que ele “faz tudo” — e também por que mal configurado vira gargalo.

---

## 3. Modos de operação de um roteador

### 3.1 Modo Router (padrão)

**Cria uma nova rede**
- Ativa NAT
- Ativa DHCP
- Sub-rede própria (ex: 192.168.1.0/24)
    

Ideal quando:
- É o roteador principal
- Está ligado diretamente ao modem/ONU
    

---

### 3.2 Modo Bridge (Ponte)

**Não cria rede nova, apenas repassa**
- NAT 
- DHCP 
- Atua como **camada 2**
- Funciona como:
    - Access Point
    - Switch
    - Conversor de mídia
        

Muito usado quando:
- Um roteador secundário expande Wi-Fi 
- ONT está em bridge e o roteador “manda”
    

Analogia:

> Bridge é um viaduto — não decide para onde você vai, só deixa passar.

---

## 4. Dois roteadores na mesma rede (controlador + satélites)

### Cenário: 1 roteador principal + outros conectados a ele

```json
Internet    
  ↓ 
Roteador Principal (Controller)    
 ├─ DHCP    
 ├─ NAT    
 └─ Wi-Fi         
      ↓    
 Roteadores Secundarios (Bridge/AP)
 ````
	
**Comportamento da rede:**
- Uma única sub-rede
- Um único servidor DHCP
- Todos os dispositivos “se enxergam”
- IPs no mesmo range
    

Essencial:
- Secundários em **modo bridge/AP**
- DHCP desativado neles
    

---

## 5. Roaming Wi-Fi (sem Mesh)

### O que é roaming?

É a capacidade de um dispositivo:
- Se desconectar de um AP fraco
- Se conectar a outro mais forte
- Mantendo a mesma rede
    

Importante:
- **O roaming é decisão do cliente**, não do roteador
- Celular/notebook decide quando trocar
    

### Problema comum:

- Mesmo SSID e senha
- Mas APs independentes
- Troca lenta ou “travada”
    
 Resultado:

- Wi-Fi parece cair
- Streaming pausa
- Chamadas falham
    

---

## 6. Mesh Wi-Fi (rede inteligente)

### O que é Mesh?

**Mesh é uma arquitetura**, não apenas repetidores.

Características:

- Um **controlador central**
- Nós/satélites coordenados 
- Mesma rede, mesmo SSID
- Decisões inteligentes de handoff
    

```json
[ Controller ]      
	 ├─ Node 1
	 ├─ Node 2      
	 └─ Node 3
```

### Tecnologias usadas no Mesh:

- **802.11k** — informações de vizinhança
- **802.11v** — sugestão de transição
- **802.11r** — fast roaming (troca rápida)
    

Resultado:
- Troca quase imperceptível
- Ideal para casas grandes, empresas, ISPs
    

Mesh é como um **Waze da rede**: ele sugere o melhor caminho antes do congestionamento.

---

## 7. Roteadores distribuindo a MESMA rede

### Exemplo:

- SSID: `Casa_WiFi`
- Senha: única
- IPs na mesma sub-rede
    

Funciona bem quando:

- Mesh nativo
- Ou APs bem posicionados
    

**Comportamento:**

- Dispositivos transitam entre ambientes
- Não percebem mudança de AP
- Serviços continuam ativos
    

---

## 8. Roteadores distribuindo redes DIFERENTES (Sala / Quarto)

### Exemplo:

- Sala: `WiFi_Sala`
- Quarto: `WiFi_Quarto`
    

**O que acontece:**

- Cada SSID é uma rede lógica diferente
- Troca manual
- Desconexão total ao mudar
    

Mesmo que:

- IP seja do mesmo roteador
- A sub-rede seja igual
    

Para o dispositivo:

> “Saí de um bairro, entrei em outro.”

---

## 9. Dois roteadores criando redes diferentes (erro clássico)

```json
Internet    
 ↓ 
Roteador 1 (192.168.1.1)    
 ↓ 
Roteador 2 (192.168.0.1)
```

⚠️ Problemas:

- Duplo NAT
- Dispositivos não se veem
- Port forwarding vira pesadelo
- Jogos e chamadas sofrem
    

Só faz sentido:

- Em redes isoladas
- Laboratórios 
- Segmentação proposital
    

---

## 10. Comparativo rápido

|Cenário|Sub-rede|Roaming|Complexidade|
|---|---|---|---|
|Router + AP|Única|Médio|Baixa|
|Vários SSIDs|Única ou múltipla|Ruim|Baixa|
|Mesh|Única|Excelente|Média|
|Duplo NAT|Múltipla|Péssimo|Alta|

---

## 11. Conexão com redes de computadores

- **Bridge** → Camada 2
- **Router** → Camada 3
- **Mesh** → Coordenação distribuída
- **Roaming** → Decisão do host + protocolos 802.11
    

Nada disso é “mágica Wi-Fi” — é **engenharia de redes aplicada à vida real**.

---

## 12. Síntese mental (mapa rápido)

```json
Internet    
↓ 
Roteador Controlador    
├─ DHCP / NAT    
├─ SSID único    
└─ Coordena APs         
	├─ Bridge         
	├─ Mesh         
	└─ Roaming assistido
```