# Whatsapp
- Cliente entra em contato pelo site através de um número
- Atendente vai estar logado no WhatsappWeb.
- Atendente irá trabalhar dentro da Salesforce, envia e recebe as mensagens do Whatsapp. 

## Contato Ativo (teste)
- 3 números de celular
- Somente contato ativo

## Fluxo
- Utilizar o assistente virtual existente no site uma outra opção "Atendimento via Whatsapp". (Connect entrando em contato)
- **Alternativa:** inserir o número do whatsapp no site. Quando o cliente enviar mensagem, retorna um menu automático para criar a solicitação na Salesforce. (Cliente entrando em contato -> pode exceder limite).
- Solicita o número do telefone e o motivo do contato (dúvida sobre produtos, informação de pedido, trocas e devoluções, informações de vale-crédito).
- Aparecer uma mensagem "Em breve um de nossos atendentes entrará em contato".
- Solicitação cria um registro em um OBJETO PERSONALIZADO e cai em uma fila da Salesforce para tratativa do atendimento.
- Atendente abre solicitação e interage com o cliente.
- Quando terminar de resolver o problema do cliente, fecha a solicitação, pra evitar do cliente entrar novamente em contato após o encerramento.
- Caso o cliente entre novamente em contato com o mesmo número, após encerrado o primeiro caso, abre um novo registro na Salesforce.
- 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwMzIwODU5OTNdfQ==
-->