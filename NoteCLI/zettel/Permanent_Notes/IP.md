## IP (Internet Protocol) 

### O que é

IP é o **endereço lógico** que identifica um dispositivo numa rede.  
Sem IP, não existe comunicação. É como tentar mandar uma carta sem endereço.

### Tipos de IP

- **IPv4** → `192.168.0.1` (4 bytes, ~4 bilhões de endereços)
- **IPv6** → `2001:0db8:85a3::8a2e:0370:7334` (128 bits, praticamente infinito)
    

### IP Público vs Privado

- **Privado** → usado dentro da rede local
    
    - `192.168.0.0/16`
    - `10.0.0.0/8`
    - `172.16.0.0/12`
        
- **Público** → visível na internet (normalmente fica no roteador/ONU)
    

### IP Estático vs Dinâmico

- **Estático** → nunca muda (servidores, links corporativos)
- **Dinâmico (DHCP)** → muda com o tempo (clientes comuns)
    

---

## 2 Máscara de sub-rede

Define **qual parte do IP é rede** e **qual é host**.

Exemplo:

```json
IP:      192.168.1.10 
Máscara: 255.255.255.0  (/24) 
Rede:    192.168.1.0
```

Tradução:

> “Todo mundo que começa com 192.168.1.* mora no mesmo bairro.”

---

## Gateway 

O **gateway padrão** é o IP do dispositivo que leva sua rede para fora  
(normalmente o roteador ou ONU).

Sem gateway:
- Rede local funciona
- Internet **não**
    

---

## 4️ DNS 

Converte:

`google.com → 142.250.79.206`

Sem DNS:

- Internet até funciona
    
- Mas só por IP (ninguém merece)
    

DNS comuns:

- Google → `8.8.8.8`
    
- Cloudflare → `1.1.1.1`
    
- ISP → geralmente automático
    

---

## 5️⃣ ICMP — o “oi, tá vivo?” da rede

### O que é

Protocolo de **controle e diagnóstico**, não transporta dados de aplicação.

### Usos clássicos

- Ver se um host responde
    
- Medir latência
    
- Detectar perdas
    

### Exemplos de mensagens ICMP

- Echo Request / Echo Reply (ping)
    
- Destination Unreachable
    
- Time Exceeded
    

---

## 6️⃣ PING — teste cardíaco da rede ❤️

### O que faz

Envia pacotes ICMP Echo Request e espera resposta.

### Exemplo

`ping 8.8.8.8`

### Interpretação

- **Tempo (ms)** → latência
    
- **Perda (%)** → instabilidade
    
- **Sem resposta** → bloqueio, queda ou firewall
    

💡 **Suporte raiz**:

- Ping no gateway → testa LAN
    
- Ping no IP público → testa internet
    
- Ping no domínio → testa DNS
    

---

## 7️⃣ TRACEROUTE — o GPS do pacote 🛰️

### O que faz

Mostra **todos os saltos (hops)** até o destino.

### Como funciona

- Usa ICMP com TTL crescente
    
- Cada roteador decrementa o TTL
    
- Quando chega a zero → responde
    

### Comandos

- Linux/macOS:
    

`traceroute google.com`

- Windows:
    

`tracert google.com`

### Uso prático (ISP)

- Descobrir onde há latência
    
- Identificar gargalo
    
- Ver se o problema é:
    
    - cliente
        
    - backbone
        
    - trânsito
        
    - destino
        

---

## 8️⃣ IPCONFIG / IFCONFIG / IP

### ipconfig (Windows)

Mostra configuração de rede.

`ipconfig ipconfig /all ipconfig /release ipconfig /renew`

Campos importantes:

- IPv4
    
- Máscara
    
- Gateway
    
- DNS
    
- MAC Address
    

### ifconfig (Linux antigo) / ip (Linux moderno)

`ip a ip route`

---

## 9️⃣ ARP — quem tem esse IP?

Resolve:

`IP → MAC`

Exemplo:

`arp -a`

Muito usado para:

- Detectar conflitos de IP
    
- Ver dispositivos na LAN
    
- Diagnosticar ataque ARP spoofing
    

---

## 🔟 TTL — expectativa de vida do pacote

- Evita loops infinitos
    
- Cada roteador decrementa
    
- Quando chega a zero → ICMP Time Exceeded
    

TTL alto = rota longa  
TTL baixo = destino próximo

---

## 🧠 Visão prática de suporte / ISP

### Fluxo de diagnóstico rápido

1. Tem IP?
    
2. IP é válido?
    
3. Gateway responde?
    
4. DNS resolve?
    
5. Ping externo responde?
    
6. Traceroute onde quebra?
    

Se travar em algum ponto → achou o problema.

---

## 🔮 Visão arquitetural (pra quem pensa grande)

- IP é **endereço lógico**, não físico
    
- ICMP é **observabilidade da rede**
    
- Traceroute é **telemetria de caminho**
    
- DNS é **desacoplamento entre nome e infraestrutura**
    

Redes bem feitas são **silenciosas**.  
Se você ouve muito “ping”, algo está errado 😄