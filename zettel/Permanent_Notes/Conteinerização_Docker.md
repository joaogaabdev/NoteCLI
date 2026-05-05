Referees: #Backend 
É o processo de empacotar uma aplicação e todas as suas dependências, garantindo que a aplicação rode da mesma forma em qualquer ambiente. Contêineres compartilham o kernel do sistema operacional, isolando apenas o necessário.

# Contêiner Vs. Máquina Virtual(VM)


|             | Máquina Virtual          | Conteiner                 |
| ----------- | ------------------------ | ------------------------- |
| Isolamento  | Hardware + SO            | SO (Kernel compartilhado) |
| Peso        | Pesada                   | Leves                     |
| Performance | Mais lentas              | Rápidas                   |
| Boot        | Minutos                  | Segundos/instantâneos     |
| Uso         | VMs para múltiplos S.O's | Contêineres para Apps     |

# Por que usar Docker?

- Elimina o problemas do "na minha máquina funciona".

- Padroniza ambientes de desenvolvimento e produção

- Facilita a escalabilidade de aplicações

- Deploy mais rápido e reprodutível

- Melhora testes automatizados

# Caso de uso na prática

- Desenvolvimento em local isolado

- Testes de integração

- Microsserviço: cada serviço no seu contêiner.

- Ambientes temporários(Labs/testes)

- Deploy em servidores(AWS, Azure, GCP)