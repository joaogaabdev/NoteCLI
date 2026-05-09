Mapa de comandos via CMD/Terminal para auxiliar no diagnóstico de problemas de redes.
### **ping**
O comando mais básico para testar a conectividade entre dois nós.
- **Para que serve:** Verifica se um host remoto está ativo e mede o tempo de resposta (latência).
- 

```powershell
ping <ip> (host)
Ex:
	ping 192.168.0.31
```

Esse comando enviará 4 pacotes via TCP/IP para o endereço selecionado.

```powershell
Disparando 192.168.0.31 com 32 bytes de dados:
Resposta de 192.168.0.31: bytes=32 tempo<1ms TTL=128
Resposta de 192.168.0.31: bytes=32 tempo<1ms TTL=128
Resposta de 192.168.0.31: bytes=32 tempo<1ms TTL=128
Resposta de 192.168.0.31: bytes=32 tempo<1ms TTL=128
```

Caso possua resposta, o IP está ativo e recebe pacotes via TCP.

## Para testar a conexão com a rede local

```powershell
ping 192.168.1.1 (gateway padrao do roteador/ont)
```
## Para testar a conexão externa (Rede local x Rede externa)

```powershell
ping google.com
```

Como profissional de suporte técnico, ter um domínio sólido do CMD e do PowerShell é essencial para diagnosticar problemas de conectividade de forma rápida e precisa.

Aqui está um guia prático dos comandos fundamentais, organizados por categoria, para o seu dia a dia.

---
### **tracert** (Trace Route)

- **Para que serve:** Mostra o caminho exato que um pacote percorre até o destino, listando todos os roteadores (saltos) no caminho.
    
- **Como usar:** `tracert google.com`
    
- **Diagnóstico:** Se o rastreio parar em um IP específico, o problema de rede provavelmente está naquele ponto ou logo após ele.

### **pathping**

- **Para que serve:** Uma combinação do `ping` com o `tracert`. Ele rastreia a rota e, depois, envia pings por um período para calcular a perda de pacotes em cada salto.
    
- **Como usar:** `pathping google.com`
    
- **Dica:** É mais lento que o tracert, mas fornece uma análise muito mais detalhada sobre qual nó da rede está causando perda de dados.

## Configuração e Interface de Rede

Úteis para entender como o computador local está configurado.

### **ipconfig**

- **Para que serve:** Exibe todos os detalhes da configuração de rede TCP/IP atual.
    
- **Comandos essenciais:**
    
    - `ipconfig /all`: Mostra detalhes completos (MAC Address, DHCP, DNS).
        
    - `ipconfig /release`: Libera o endereço IP atual (desconecta).
        
    - `ipconfig /renew`: Solicita um novo endereço IP ao servidor DHCP.
        
    - `ipconfig /flushdns`: Limpa o cache do DNS (essencial quando um site não carrega após mudanças de servidor).
        

### **getmac**

- **Para que serve:** Retorna o endereço físico (MAC) das placas de rede instaladas.
    
- **Como usar:** `getmac /v`
    

---

## 3. Diagnóstico de Portas e Conexões Ativas

### **netstat** (Network Statistics)

- **Para que serve:** Mostra todas as conexões de rede ativas, portas abertas e estatísticas de Ethernet.
    
- **Como usar:**
    
    - `netstat -an`: Lista todas as conexões e portas de escuta em formato numérico.
        
    - `netstat -ano`: Adiciona a coluna "PID" (Process ID), permitindo que você veja qual programa está usando aquela porta (cros-reference com o Gerenciador de Tarefas).
        

### **arp -a**

- **Para que serve:** Exibe a tabela ARP (Address Resolution Protocol), que mapeia endereços IP para endereços MAC na sua rede local.
    
- **Uso:** Útil para identificar conflitos de IP ou descobrir dispositivos na mesma rede.
    

---

## 4. Resolução de Nomes (DNS)

### **nslookup**

- **Para que serve:** Testa a resolução de nomes DNS. Você pode descobrir qual IP pertence a um domínio ou vice-versa.
    
- **Como usar:** * `nslookup google.com`
    
    - `nslookup 8.8.8.8` (Para verificar quem é o dono do IP).
        
    - **Modo Interativo:** Digite apenas `nslookup`, e dentro dele você pode trocar o servidor de teste (ex: `server 1.1.1.1`) para verificar se o problema é o DNS da empresa.
        

---

## 5. Super Comandos no PowerShell

O PowerShell oferece comandos mais modernos (Cmdlets) que são mais poderosos que os do CMD.

### **Test-NetConnection** (O "Canivete Suíço")

Este é, provavelmente, o comando mais útil para suporte técnico moderno.

- **Para que serve:** Além de pingar, ele pode testar se uma **porta específica** está aberta no destino.
    
- **Como usar:** * `Test-NetConnection google.com -Port 443` (Verifica se a porta HTTPS está acessível).
    
    - `Test-NetConnection 192.168.1.10 -CommonTCPPort RDP` (Verifica se o Acesso Remoto está aberto).
        

### **Resolve-DnsName**

- **Para que serve:** Uma versão mais moderna e detalhada do `nslookup`.
    
- **Como usar:** `Resolve-DnsName google.com`
    

---

### Tabela de Consulta Rápida

| **Problema**                            | **Comando Recomendado**                 |
| --------------------------------------- | --------------------------------------- |
| Testar se a internet caiu               | `ping 8.8.8.8 -t`                       |
| Site não abre, mas o ping funciona      | `ipconfig /flushdns`                    |
| Identificar lentidão na rota            | `tracert` ou `pathping`                 |
| Verificar se o IP está correto          | `ipconfig /all`                         |
| Saber se um app está travando uma porta | `netstat -ano`                          |
| Testar se o Firewall bloqueia uma porta | `Test-NetConnection [IP] -Port [Porta]` |