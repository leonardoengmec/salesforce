# SALESFORCE - ROTINA DE LIMPEZA
## CLIENTES
Excluir os cliente em que a data da última modificação foi a mais de 3 anos.
Classe: Connect_LimpezaClientes

## PEDIDOS
Exluir os pedidos em que a data da última modificação foi a mais de 6 meses.
Classe: Connect_LimpezaPedidos

## E-MAILS
Excluir os e-mails em que data da mensagem foi a mais de 6 meses.
Fazer backup manualmente e inserir no banco criado no SQLServer.
Inicialmente a limpeza será realizada manualmente.
- [ ]  Criar uma classe para validar os e-mails com mais de 6 meses. Criar um check-box para facilitar a extração desses e-mails através do DataLoader.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyNzM4MzE5NF19
-->