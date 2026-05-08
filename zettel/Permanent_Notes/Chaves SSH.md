Referees: #Backend 
# SSH(Secure Shell)
É um protocolo que permite comunicação segura entre dois computadores. 
A chave SSH é uma forma de autenticação baseada em criptografia que substitui senhas, ela vem em um par:
* Chave pública(public key): Distribui para quem quiser autenticar.
* Chave privada(private key): Fica guardada com você 

## Pra que serve no mundo real?

1. Acesso remoto seguro a servidores
2. Clonagem e push/pull em repositórios Git com autenticação sem senha
3. Deploy automático com CI/CD
4. Gerenciamento de infraestrutura com ferramentas como Ansible, Terraform
5. Conexão entre containers ou máquinas em ambientes distribuídos.

## Como Funciona na Prática?

1. Você **gera um par de chaves** com:
    
``` bash

    ssh-keygen -t ed25519 -C "seuemail@dominio.com"
```
    
2. Sua chave pública vai para o **servidor ou serviço (ex: GitHub)**.
    
3. Quando você tentar se conectar, o servidor usa a **chave pública** para te desafiar com um "puzzle" criptográfico que **só a chave privada consegue resolver**.

Chave privada - SuachavePrivada123
