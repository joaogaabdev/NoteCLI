 
# **Ideia central:**  
> Um Sistema Operacional é o **orquestrador** entre **hardware**, **software** e **usuário**.  
> Tudo gira em torno de **gerenciamento de recursos**.

---

## 🧩 1. Fundamentos de Sistemas Operacionais

_(Base teórica — linguagem universal dos SOs)_

- [[O que é um Sistema Operacional]]
    
- [[Kernel — conceito e responsabilidades]]
    
- [[User Space vs Kernel Space]]
    
- [[Chamadas de Sistema (Syscalls)]]
    
- [[Modos de execução — usuário vs kernel]]
    
- [[Tipos de Sistemas Operacionais]]
    
    - Batch
        
    - Time-sharing
        
    - Real-time (RTOS)
        
    - Distribuídos
        
- [[Arquiteturas de Kernel]]
    
    - Monolítico
        
    - Microkernel
        
    - Híbrido
        

---

## ⚙️ 2. Gerenciamento de Processos

_(Onde a mágica da multitarefa acontece)_

- [[Processo vs Thread]]
    
- [[Estados de um Processo]]
    
- [[Escalonamento de Processos]]
    
    - Round Robin
        
    - FIFO
        
    - Prioridade
        
- [[Context Switch]]
    
- [[PID, PPID e Init/Systemd]]
    
- [[Sinais em Sistemas Unix/Linux]]
    
- [[Fork, Exec e Wait]]
    

---

## 🧠 3. Gerenciamento de Memória

_(RAM não é infinita, infelizmente)_

- [[Memória Física vs Memória Virtual]]
    
- [[Paginação]]
    
- [[Segmentação]]
    
- [[Swap]]
    
- [[Alocação de Memória]]
    
- [[Stack vs Heap]]
    
- [[OOM Killer]]
    
- [[Gerenciamento de Memória no Linux]]
    

---

## 💾 4. Sistemas de Arquivos

_(Onde os dados vivem — e às vezes morrem)_

- [[O que é um Sistema de Arquivos]]
    
- [[Estrutura de Diretórios no Linux]]
    
- [[Inode]]
    
- [[Permissões de Arquivos]]
    
- [[Links Simbólicos vs Hard Links]]
    
- [[Montagem de Sistemas de Arquivos]]
    
- [[Sistemas de Arquivos Comuns]]
    
    - ext4
        
    - xfs
        
    - btrfs
        
    - FAT / NTFS
        

---

## 🖥️ 5. Dispositivos e I/O

_(Falando com o mundo físico)_

- [[Dispositivos de Bloco vs Caractere]]
    
- [[Drivers de Dispositivos]]
    
- [[I/O Buffering]]
    
- [[File Descriptors]]
    
- [[stdin, stdout, stderr]]
    
- [[udev]]
    
- [[Interrupções e DMA]]
    

---

## 🔐 6. Segurança e Controle de Acesso

_(Quem pode fazer o quê — e quem não pode)_

- [[Usuários e Grupos no Linux]]
    
- [[Modelo de Permissões Unix]]
    
- [[sudo e privilégios]]
    
- [[Capabilities no Linux]]
    
- [[SELinux / AppArmor]]
    
- [[Isolamento de Processos]]
    
- [[Namespaces e Cgroups]]
    

---

## 🌐 7. Redes no Contexto de SO

_(O SO como cidadão da rede)_

- [[Stack de Rede no Sistema Operacional]]
    
- [[Sockets]]
    
- [[TCP vs UDP no nível do SO]]
    
- [[Interfaces de Rede]]
    
- [[Tabela de Roteamento]]
    
- [[Firewall no Linux — netfilter/iptables/nftables]]
    

---

## 🧰 8. Inicialização e Gerenciamento do Sistema

_(Da energia ao login)_

- [[Boot Process]]
    
    - BIOS / UEFI
        
    - Bootloader (GRUB)
        
    - Kernel
        
    - Init
        
- [[Systemd]]
    
- [[Runlevels e Targets]]
    
- [[Serviços e Daemons]]
    
- [[Logs do Sistema]]
    
    - journalctl
        
    - /var/log
        

---

## 🐧 9. Linux como Estudo de Caso

_(Teoria aplicada — onde você está agora)_

- [[O que é o Linux]]
    
- [[Distribuições Linux]]
    
- [[Kernel Linux]]
    
- [[GNU e Userland]]
    
- [[Shells]]
    
    - bash
        
    - zsh
        
- [[Estrutura de Diretórios Linux (FHS)]]
    

---

## 🧪 10. Observabilidade e Diagnóstico

_(Ver o SO em ação)_

- [[top, htop e atop]]
    
- [[ps, free, vmstat]]
    
- [[strace]]
    
- [[lsof]]
    
- [[dmesg]]
    
- [[procfs e sysfs]]
    

