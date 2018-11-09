# INFORMAÇÕES
## ORIGEM
 - E-mail
 - Chat
 - Telefone
 - Fale Conosco
 - mercadolivre@connectparts.com.br
 - vendas@dakotaparts.com.br
 - informativo@connectparts.com.br
 - vendas@connectparts.com.br
 - Correios
 - Mercado Pago
 - Amazon
 - comunicacao.transportes@connectparts.com.br
 - Mercado Livre
 - Perguntas ML

## DEPARTAMENTO
- Callcenter
- Chat online
- Financeiro
- Int
- Ouvidoria
- Perguntas
- Trocas
- TI

## CANAIS DE ENTRADA
- **Telefone**
- **Chat Online**
	- Chat Online "Dúvidas sobre forma de pagamento"
	- Chat Online "Dúvidas sobre pedidos"
	- Chat Online "Dúvidas sobre produtos"
	- Chat Online "Dúvidas sobre Promoções"
	- Chat Online "Dúvidas sobre Rastreio e posição de entrega"
	- Chat Online "Dúvidas sobre trocas e devoluções"
	- Chat Online "Elogios e Agradecimentos"
	- Chat Online "Realizar uma compra"
	- Chat Online "Reclamações"
- **Mídias Sociais**
	- Facebook
	- Instragram
	- Twitter
	- Youtube
	- Google+
- **Formulário WEB**
	- Formulário WEB " Contato com Comercial e Marketing"
	- Formulário WEB " Criticas e Sugestões"
	- Formulário WEB " Dúvidas sobre forma de pagamento"
	- Formulário WEB " Dúvidas sobre pedidos"
	- Formulário WEB " Dúvidas sobre Produto"
	- Formulário WEB " Dúvidas sobre promoções"
	- Formulário WEB " Dúvidas sobre Rastreio e Posição de Entrega"
	- Formulário WEB " Elogios e agradecimentos"
	- Formulário WEB " Item Faltante"
	- Formulário WEB " Lojista"
	- Formulário WEB " Pessoa Jurídica"
	- Formulário WEB " Reclamações"
	- Formulário WEB " Trocas e Devoluções"
- **Mercado Livre**
	- Mensageria
	- Perguntas
	- Qualificação
		- Positiva
		- Neutro
		- Negativo
- **Loja Virtual**
	- Perguntas
	- E-mail
	- Opiniões - Trustvox
- **Mercado Pago**
	- Reclamação
		- Mercado Livre
		- Loja Virtual
	- Mediação
		- Mercado Livre
		- Loja Virtual
- **Correios**
- **E-bit**
- **ReclameAqui**
- **Marketplace**
- **Marketplace Connect Parts**
- **Transferência de Demanda ou abertura de chamado**
- **Paypal**
	- Reclamação
	- Mediação
- **Contato ativo Pendências**

## ORIGEM DA RECLAMAÇÃO
- Atendimento
- B2B
- Cliente
- Comerical
- Correios
- Embalagem
- Financeiro
- Logística
- Marketing
- Sistema
- Transportadoras

## MOTIVOS DA RECLAMAÇÃO







## REGRAS DE FLUXO
### CASO
1. **Ticket criado atualiza o registro:** Toda vez que o registro é criado ele marca a caixa de seleção para pesquisar o registro na integração com Ábacos, isso foi feito para forçar a busca do registro sempre.
2. ** Emails do ML:** Quando a origem for e-mail do mercado livre ele altera a fila e o canal de entrada certos.
3. **Envia o ticket para spam:** Quando o Checkbox for ativado ele troca o proprietário do registro para SPAM, e essa fila deve ser excluída manualmente por enquanto.
4. **SPAM:** Verifica se o e-mail é igual ao listados na regra, caso seja verdadeiro ele joga para fila de SPAM como proprietário, lembrando que nessa fila os tickets são deletados 1 vez por semana.
5. **Emails do informativo:** Quando a origem do ticket for informativo altera a fila e o canal de entrada do ticket.
6. **Email vendas@connect.com.br:** Quando a origem do ticket for vendas altera o canal de entrada e a fila do ticket.
7. **Inseri o E-mail:** Toda vez que um chamado é criado ele cópia o E-mail da Web para o campo de e-mail certo.
8. **Aloca para fila Certa:** Quando a origem do chamado for Trocas e Devoluções altera para a fila certa.
9. **Altera para a fila certa - canal direto LV:** Quando a origem do chamado for critérios abaixo altera para a fila certa.
10. **Altera para a fila certa - Trocas:** Quando a origem do chamado for Trocas e Devoluções altera para a fila certa.
11. **SLA 96 horas:** Coloca o SLA baseado na Fila e no canal de entrada do Ticket de atendimento.
12. **Chamados Mercado Livre**
13. **Aloca Fila Correios**
14. **SLA 48 horas:** Coloca o SLA baseado na Fila e no canal de entrada do Ticket de atendimento.
15. **SLA 72 horas:** Coloca o SLA baseado na Fila e no canal de entrada do Ticket de atendimento.
16. **SLA 120 horas:** Coloca o SLA baseado na Fila e no canal de entrada do Ticket de atendimento.
17. **SLA 144 horas:** Coloca o SLA baseado na Fila e no canal de entrada do Ticket de atendimento.
18. **SLA Indeterminado:** Coloca o SLA baseado na Fila e no canal de entrada do Ticket de atendimento.
19. **SLA 24 horas:** Coloca o SLA baseado na Fila e no canal de entrada do Ticket de atendimento.
20. **SLA controle:** Coloca o SLA baseado na Fila e no canal de entrada do Ticket de atendimento.
21. **Origem Facebook:** Quando um chamado é de origem facebook, ele altera canal de entrada e departamento.
22. **Quando o ticket é de correios:** Adiciona ele para fila certa.
23. **Copia email texto para campo de email:** BC 23/01/2017- Caso os campos de email da conta estejam em branco, copia o conteúdo do campo "email texto" para o campo de email (nativo).

### MENSAGEM DE E-MAIL
1. **Reabrir o chamado:** Toda vez que um e-mail novo chegar ao ticket e ele estiver com status "Fechado" ele reabre o e-mail para em andamento.   
 
### CONTA
1. **Copia email texto para campo de email:**BC 23/01/2017- Caso os campos de email da conta estejam em branco, copia o conteúdo do campo "email texto" para o campo de email (nativo).

### SERVICE
1. **Fecha o service com a data de hoje:** Quando um service é alterado para concluído ele altera a data de fechamento para NOW().
2. **Altera proprietário do service - Devolução:** Regra pra alterar o proprietário do Service para o departamento do financeiro quando for criado um service de devolução.
3. **Altera proprietário do service - Reversão:** Regra pra alterar o proprietário do Service para a fila de reversão quando for um service de Reversão.

### CARRINHO ABANDONADO
1. **Altera o proprietário para a Fila:** Sempre que um carrinho é criado altera o carrinho para a fila certa.

### FINALIZAÇÃO DE PEDIDOS
1. **Insere a data de fechamento - finalização de pedidos:** Insere a data atual na data de fechamento quando o status é passado para concluído, na finalização de pedido.

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg3MzgwMDIzOF19
-->