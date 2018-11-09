# DESENVOLVIMENTO
## DESCRIÇÃO
Melhorar a comunicação entre o atendimento e o comercial desenvolvendo uma aplicação na salesforce para substituir as planilhas Sugestão de melhorias de anúncio, Correção de anúncio e Incompatibilidade.

## REQUISITOS

- [ ] Criar uma página para o Comercial interagir com a Salesforce.
- [ ] Criar um componente personalizado do console para o atendimento procurar e inserir informações sobre os produtos.
- [ ] Recuperar da API Shopping de Preços as informações através do DK quando o atendimento digitar o DK no componente.
- [ ] Criar objeto personalizado para registrar as solicitações.

## MENU
- SUGESTÃO DE ANÚNCIO
	- Vendas
	- Compras
- CORREÇÃO / INCOMPATIBILIDADE
- 	- Vendas
	- GCA

## SUGESTÃO DE ANÚNCIO
|Inserido por| Nome do campo | Tipo | Campo Salesforce | Criado? |
|--|--|--|--|--|
| Sistema | Status| String | status__c | :heavy_check_mark:
| Sistema | Data/hora | Datetime | CreatedDate | :heavy_check_mark:
| Sistema | Setor| Picklist | CreatedBy.Departamento| :heavy_check_mark:
| Sistema | Nome do atendente| String | CreatedBy.Name | :heavy_check_mark:
| Sistema | Canal de venda| String | canalVenda__c | :heavy_check_mark:
| Atendimento | Pedido| String | pedido__c | :heavy_check_mark:
| Atendimento | DK| String | codigoExterno__c | :heavy_check_mark:
| Atendimento | Link do anúncio| String | linkProduto__c | :heavy_check_mark:
| Atendimento | Pergunta| String | pergunta__c | :heavy_check_mark:
| Vendas | Resposta| String | respostaVendas__c | :heavy_check_mark:
| Vendas | Data/hora limite| Datetime | dataLimiteVendas__c | :heavy_check_mark:
| Vendas | Data/hora tratativa| Datetime | dataTratativaVendas__c | :heavy_check_mark:
| Vendas | Ação| String | acaoVendas__c | :heavy_check_mark:
| Vendas | Observação | String | observacaoVendas__c | :heavy_check_mark:
| Compras | Data/hora limite| Datetime | respostaCompras__c | :heavy_check_mark:
| Compras | Data/hora limite| Datetime | dataLimiteCompras__c | :heavy_check_mark:
| Compras | Data/hora tratativa| Datetime | dataTratativaCompras__c | :heavy_check_mark:
| Compras | Ação| String | acaoCompras__c | :heavy_check_mark:
| Compras | Observação| String | observacaoCompras__c | :heavy_check_mark:


## CORREÇÃO DE ANÚNCIO
|Inserido por| Nome do campo | Tipo |
|--|--|--|
| Atendimento | Data/hora | Datetime |
| Atendimento | Solicitante | String |
| Atendimento | Canal de venda | String |
| Atendimento | DK Pai | String |
| Atendimento | DK Filho | String |
| Atendimento | Categoria | String |
| Atendimento | Correção sugerida | String |
| Atendimento | Link do produto | String |
| Vendas | Responsável | String |
| Vendas | Validação vendas (Aprovado/Reprovado/Corrigido/Verificando)| String |
| Vendas | Comentários| String |
| Vendas | Prazo (Verificando = 3 dias úteis / Else = 1 dia útil)| Datetime |
| Vendas | Data/hora conclusão| Datetime |
| Vendas | Status (Verificando/Concluído/Atrasado/No prazo para tratar) | String |
| GCA | Responsável | String |
| GCA | Validação GCA (Finalizado/Não finalizado) | String |
| GCA | Comentários | String |
| GCA | Verificou KITS | String |
| GCA | Prazo (1 dia útil) | String |
| GCA | Data/hora finalização | Datetime |
| GCA | Status| String |


## INCOMPATIBILIDADE
|Inserido por| Nome do campo | Tipo |
|--|--|--|
| Atendimento | Data/hora | Datetime |
| Atendimento | Atendente | String |
| Atendimento | Pedido | String |
| Atendimento | DK | String |
| Atendimento | Categoria | String |
| Atendimento | Link do anúncio| String |
| Atendimento | Comentário do cliente| String |
| Atendimento | Observação / informação complementar| String |
| Vendas | Prazo (se now() < 12:00 => 18:00 se não 12:00 (+1) | Datetime |
| Vendas | Responsável| String |
| Vendas | E-mail| String |
| Vendas | Status| Picklist {Respondido; Aguardando fornecedor ; Atendimento enviar fotos} |
| Vendas | Ação tomada| String |
| Vendas | Redmine| String |

## CATEGORIAS
> Iluminação: cinza
> Motocicleta: vermelho
> Áudio e vídeo: laranja
> Importados: verde
> Acessórios: azul
> Som: amarelo



## INFORMAÇÕES
**API Shopping de preço:** http://192.99.185.73:8071/swagger/ui/index#!/Anuncio/Anuncio_Listar

## Perguntas
- [ ] Inserir nota na resposta :question:
- [x] Inserir tela de inventário para colaborador responsável limpar o histório
- [x] Dar carga do histórico existente
- [ ] Botão para passar como sugestãoa de melhoria
- [ ] Botão de copiar no atendimento para contar 
- [ ] Ao responder a pergunta no portal, a pergunta do ML e LV ser respondidoa automaticamente.

## Correção de Anúncio
**Ações:**
> Enviar para vendas
> Enviar para GCA
> Enviar para GA

- Dispara e-mail quando entrar uma solicitação.

## Incompatibilidade

## Configurações
- Cadastro e atualização do e-mail do líder de vendas.
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTM2Njc2OTk3LC0xODMxMjYyMTE1LDExOT
I5NjY0MzgsNjI3NzY5MDc4LC0yMDk4MjgxMDY2LC0xMDExMjg3
NjcyXX0=
-->