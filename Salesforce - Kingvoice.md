# Salesforce - Kingvoice
## Autorização Salesforce
### Sandbox
**- Endpoint:** https://cs25.salesforce.com/services/oauth2/token
**- Método:** POST
**Payload:**
```
grant_type:password
client_id:3MVG9eYfd1zvW1E6Sb.AQh_31N7zbKT79SvEdhn8IvbKKqAYSQUgiyf6TfeaJPqgircL.x0Zgu6IUGMESfkvX
client_secret:2966073978840958307↵
username:processos.salesforce@connectparts.com.br.sandboxdev
password:Connect#processos20176RTYKxrDwqYP8pnUmmXMMKEvv
```

### Produção
**- Endpoint:** https://na34.salesforce.com/services/oauth2/token
**- Método:** POST
**Payload:**
```
grant_type:password
client_id:3MVG9KI2HHAq33Rxjo0Y6ZqZSa.tGp2rtUwLFD5N1Mhd23t56jkipRaKwF9m8d5X1HeAvtyHlJMSHyB8.gc4I
client_secret:3552580952912005969
username:connect@forceconsulting.com.br
password:kingvoice20181zCgUqWLFupV8uDAcuK0nyFVT
```

**Resposta exemplo:**
```json
{
    "access_token": "00D1b000000D8CO!ARQAQHSrWOmgkuU3dPNgfTmuSk_LOel91nLsI7EdTTnIqCYlvKaptwxAM.SOSWWF707g.PK38XNpdM8NauvWmnoIqDt8v39k",
    "instance_url": "https://cs25.salesforce.com",
    "id": "https://test.salesforce.com/id/00D1b000000D8COEA0/00561000001TFLRAA4",
    "token_type": "Bearer",
    "issued_at": "1527607166882",
    "signature": "rLNVTcQXU9jWW9/ZlPwXiW83VYH8t3E6nQC2lCjfpcY="
}
```
Utilizar o ***access_token*** na Header nas chamada: 
`"Authorization": "bearer access_token".`

## 1) Rastreio - Transportadora
**Endpoints:** 
	- ***Sandbox:*** https://cs25.salesforce.com/services/apexrest/kingvoice/transportadora
	- ***Produção:*** https://na34.salesforce.com/services/apexrest/kingvoice/transportadora

### Método GET: 
**Função:** Lista todas os pedidos despachados por transportadoras, faturados D-1 com as condições abaixo:
>- Tipo = 'Transportadora'
>- Tentativas de contato <= 3 ou null.
>- Opção do cliente = null ou igual a zero.
>- Telefone do cliente != null
	
**Resposta:**
```json
[
    {
        "attributes": {
            "type": "PedidosURA__c",
            "url": "/services/data/v35.0/sobjects/PedidosURA__c/a0e1b000001wjHWAAY"
        },
        "notaFiscal__c": "604772",
        "telefoneCliente__c": "85981856320",
        "tentativasURA__c": 0,
        "Id": "a0e1b000001wjHWAAY"
    },
    {
        "attributes": {
            "type": "PedidosURA__c",
            "url": "/services/data/v35.0/sobjects/PedidosURA__c/a0e1b000001wjHXAAY"
        },
        "notaFiscal__c": "604475",
        "telefoneCliente__c": "41999696170",
        "tentativasURA__c": 0,
        "Id": "a0e1b000001wjHXAAY"
    }
]
```

### Método POST:
**Função:** atualiza o registro do pedido com os parâmetros passados de codigo de rastreio e a opção que o cliente digitou.
**Payload:**
```json
{
	"pedidoId": "a0e1b000001wjHVAAY",
	"opcaoCliente": 0
}
```
**Parâmetros:**
**pedidoID:** Passar o campo ***Id*** capturado no método GET. `[string]`
**opcaoCliente:** `[integer]`
>***Entendeu a mensagem.*** enviar parâmetro como 1 (um). O pedido irá sair da fila. 
>***Cliente não digitou nada***: enviar parâmetro como 0 (zero).

**Resposta:** 
- ***Status 200:***
```json
{
    "Id": "a0e1b000001wjHVAAY",
    "Message": "Registro atualizado com sucesso!"
}
```
- ***Status 500***
```json
{
    "Message": "List has no rows for assignment to SObject"
}
```


## 2) Reversa - Confirmação de endereço
**Endpoints:** 
	- ***Sandbox:*** https://cs25.salesforce.com/services/apexrest/kingvoice/reversa
	- ***Produção:*** https://na34.salesforce.com/services/apexrest/kingvoice/reversa

### Método GET: 
**Função:** Lista todas as reversas com as condições abaixo:
>- Tentativas de contato <= 3
>- Opção do cliente = null ou igual a zero.
>- Endereço do cliente != null
>- Motivo da reversa = ...

**Resposta:** 
```json
[
    {
        "attributes": {
            "type": "Reversa__c",
            "url": "/services/data/v35.0/sobjects/Reversa__c/a0d1b000000U5RHAA0"
        },
        "codigoRastreio__c": "TNT-000288810-0002-005",
        "telefone__c": "53981389002",
        "enderecoCliente__c": "Avenida Fernando Osório, 1518",
        "tentativasURA__c": 0,
        "Id": "a0d1b000000U5RHAA0"
    },
    {
        "attributes": {
            "type": "Reversa__c",
            "url": "/services/data/v35.0/sobjects/Reversa__c/a0d1b000000U4TGAA0"
        },
        "codigoRastreio__c": "GOL-000538647-0001-005",
        "telefone__c": "81995112931",
        "enderecoCliente__c": "Rua Félix de Brito Melo, 946",
        "tentativasURA__c": 0,
        "Id": "a0d1b000000U4TGAA0"
    }
]   
```

### Método POST:
**Função:** atualiza o registro da reversa com os parâmetros passados de codigo de rastreio e a opção que o cliente digitou.
**Payload:**
```json
{
	"pedidoId":"a0d1b000000U5RHAA0",
	"opcaoCliente":1
}
```
**Parâmetros:**
**pedidoID:** Passar o campo ***Id*** capturado no método GET. `[string]`
**opcaoCliente:** `[integer]`
>***Endereço correto:*** Enviar parâmetro como 1 (um). Pedido vai para uma fila de reenvio.
>***Endereço incorreto:*** Enviar parâmetro como 2 (dois). Pedido vai para uma fila para o SAC entrar em contato com o cliente.
>***Cliente não digitou nada:***: enviar parâmetro como 0 (zero). Pedido continuará na fila e contará +1 no campo tentativas URA.

**Resposta:** 
- ***Status 200:***
```json
{
    "Id": "a0d1b000000U5RHAA0",
    "Message": "Registro atualizado com sucesso!"
}
```
- ***Status 500***
```json
{
    "Message": "List has no rows for assignment to SObject"
}
```
## 4) Reenvio
**Endpoints:** 
	- ***Sandbox:*** https://cs25.salesforce.com/services/apexrest/kingvoice/reenvio
	- ***Produção:*** https://na34.salesforce.com/services/apexrest/kingvoice/reenvio
	
### Método GET: 
**Função:** Lista todas os pedidos despachados como pedido digitado -INT, faturados D-1 com as condições abaixo:
>- Tipo = 'Reenvio'
>- Tentativas de contato <= 3 ou null.
>- Opção do cliente = null ou igual a zero.
>- Telefone do cliente != null

**Resposta:** 
```json
[
    {
        "attributes": {
            "type": "PedidosURA__c",
            "url": "/services/data/v35.0/sobjects/PedidosURA__c/a0e1b000001wjICAAY"
        },
        "codigoRastreio__c": "PP459727253BR",
        "telefoneCliente__c": "1188057587",
        "tentativasURA__c": 1,
        "Id": "a0e1b000001wjICAAY"
    },
    {
        "attributes": {
            "type": "PedidosURA__c",
            "url": "/services/data/v35.0/sobjects/PedidosURA__c/a0e1b000001wjIDAAY"
        },
        "codigoRastreio__c": "604273",
        "telefoneCliente__c": "47997014108",
        "tentativasURA__c": 0,
        "Id": "a0e1b000001wjIDAAY"
    }
]   
```

### Método POST:
**Função:** atualiza o registro com a opção que o cliente digitou.
**Payload:**
```json
{
	"pedidoId": "a0e1b000001wjICAAY",
	"opcaoCliente": 0
}
```
**Parâmetros:**
**pedidoID:** Passar o campo ***Id*** capturado no método GET. `[string]`
**opcaoCliente:** `[integer]`
>***Cliente ouviu a mensagem:*** enviar parâmetro como 1 (um). Pedido sai da fila.
>***Cliente não digitou nada:*** enviar parâmetro como 0 (zero). Pedido continuará na fila e contará +1 no campo tentativas URA.

**Resposta:** 
- ***Status 200:***
```json
{
    "Id": "a0d1b000000U5RHAA0",
    "Message": "Registro atualizado com sucesso!"
}
```
- ***Status 500***
```json
{
    "Message": "List has no rows for assignment to SObject"
}
```
## 5) Ligação Pendente
**Endpoints:** 
	- ***Sandbox:*** https://cs25.salesforce.com/services/apexrest/kingvoice/ligacao
	- ***Produção:*** https://na34.salesforce.com/services/apexrest/kingvoice/ligacao
	
### Método POST:
**Função:** cria um ticket na Salesforce com o telefone e documento do cliente.
**Payload:**
```json
{
	"telefone": "11987654321",
	"CPF": "32145678922"
}
```
**Parâmetros:**
**telefone:** [string] Telefone do cliente que ligou. `[string]` 
**CPF:** documento que o cliente digitou na URA. `[string] [opcional]` 

**Resposta:** 
- ***Status 200:***
```json
{
    "Id": "5001b000003RfvlAAC",
    "Message": "Registro inserido com sucesso!"
}
```
- ***Status 500***
```json
{
    "Message": "List has no rows for assignment to SObject"
}
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1Mjg2NDA1NjRdfQ==
-->