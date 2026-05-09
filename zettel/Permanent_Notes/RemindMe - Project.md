
# O que é o RemindMe?
Um projeto que utiliza OCR(Optical Character Recognition) para reconhecer nomes de clientes ou números de telefone em plataformas de mensagens(WhatsApp, Facebook) e cria um lembrete para você voltar a conversa, evitando problemas como: 
* Deixar o cliente sem resposta;
* Evitar cancelamentos por demora no atendimento;
* Atendimento cair no esquecimento.

# Como funciona o lembrete?
* Envio de E-mails para o seu E-mail contendo o nome do cliente ou número, se possível, com o contexto do atendimento;
* Envio de mensagem no WhatsApp contendo o nome do cliente ou número, se possível, com o contexto do atendimento.

# Tecnologias utilizadas
## Backend
* Java
	* Linguagem de programação responsável pelo backend.
* Docker
	* Para instalar as dependências necessárias, evitando baixar localmente na sua máquina.
* Gosseract
	* Biblioteca responsável por juntar C + Go para utilizar a tecnologia de OCR.
## Frontend
* HTML
	* Estruturação da página Web do projeto.
* CSS
	* Estilização do projeto.
* JS
	* Interatividade na página web.
## API's
* OpenAi
	* Para reconhecer o contexto da conversa.

**LEMBRAR**
* *Alguma API para envio de E-mail
* Alguma API para mandar mensagem para o WhatsApp
* Hospedagem do serviço em alguma plataforma
* 