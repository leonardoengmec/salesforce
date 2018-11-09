# FLUXO DE CANCELAMENTO

## DESCRIÇÃO

Serviço para o cancelamento do pedido e tratativas posteriores.

## FLUXO

https://www.goconqr.com/pt-BR/mind_maps/15833240/edit

https://www.draw.io/?lightbox=1&highlight=0000ff&edit=_blank&layers=1&nav=1#G14RRmoepLE20cBwyRYwzcr3Ntj5BxpLmM

## FLUXO PROCESS BUILDER

1. Service é criado ou alterado.
2. Valida se o service é do tipo de registro Cancelamento e Devolução. :heavy_check_mark:
3. Se mudou o status, atualiza o campo Data do Status para NOW(). :heavy_check_mark:
4. Se **Devolver ao atendimento = verdadeiro**: atualiza o status para **Aguardando correção**. :heavy_check_mark:
5. Se **Ação backoffice = Não realizado**: atualiza o status para **Service cancelado.** :heavy_check_mark:
6. ***Devolução Realizada:*** Se **Status = Aguardando devolução** e **devoluçãoRelizada = Verdadeiro**: atualiza o status para **Devolução realizada**. :heavy_check_mark:
7. ***Gerar Vale-crédito:*** Se **Status = Gerar vale-crédito** ou **Status = Reativar vale-crédito** e **Número do vale-crédito != nulo** e **Valor do vale-crédito != nulo** e **Data da validade do crédito != nulo**: atualiza o status para **Vale-crédito gerado**. :heavy_check_mark:
8. Se **Criado pelo departamento = Trocas** ou **Criado pelo departamento = Pré-análise** e **Ação = Devolução** e **Ação backoffice = nulo**:  atualiza o campo Ação backoffice para **Cancelamento realizado**.
9. Valida qual o tipo da ação.

### Acão: Vale-crédito

- ***Vale: Ação backoffice***: **Ação = Vale-crédito** e **Ação backoffice != nulo**
  - ***Ação 1:*** Se **Ação backoffice = Cancelamento realizado**: atualiza o status para **Gerar vale-crédito** e data da ação para NOW(). :heavy_check_mark:
  - ***Ação 2:*** Se **Ação backoffice = Seguir com devolução**: atualiza o status para **Aguardando devolução** e data da ação para NOW(). :heavy_check_mark:
  - ***Ação 3:*** Se **Ação backoffice = Passar para reversão**: atualiza o status para **Aguardando reversão** e data da ação para NOW(). :heavy_check_mark:
  - ***Ação 4:*** Se **Ação backoffice = Vale-crédito alterado**: atualiza o status para **Vale-crédito alterado** e data da ação para NOW(). :heavy_check_mark:
  - ***Ação 5:*** Se **Ação backoffice = Vale-crédito reativado** e **Número do vale-crédito != nulo** e **Valor do vale-crédito != nulo** e **Data da validade do crédito != nulo**: atualiza o status para **Vale-crédito gerado** e data da ação para NOW(). :heavy_check_mark:
- **Vale: Sub-ações**: **Ação = Vale-crédito** e **Ação backoffice = nulo**
  - ***Sub-ação 1:*** Se **Sub-ação = Criar**: atualiza o status para **Aguardando cancelamento**. :heavy_check_mark:
  - ​***Sub-ação 2:*** Se **Sub-ação = Inativar**: atualiza o status para **Inativar vale-crédito**. :heavy_check_mark:
  - ***Sub-ação 3:*** Se **Sub-ação = Reduzir valor**: atualiza o status para **Alterar vale-crédito**. :heavy_check_mark:
  - ***Sub-ação 4***: Se **Sub-ação = Aumentar valor**: atualiza o status para **Alterar vale-crédito**. :heavy_check_mark:
  - ***Sub-ação 5***: Se **Sub-ação = Reativar**: atualiza o status para **Reativar vale-crédito**. :heavy_check_mark:

### Ação: Devolução

- **Devolução: Reativar o pedido**
  - **Ação 1**: Se **Pedido reativado = Verdadeiro**: atualiza status para **Revertido**. :heavy_check_mark:

- **Devolução: Aguardando reversão**
  - **Ação 1:** Se **Tratativa da reversão = Seguir com devolução**: atualiza o status para **Aguardando devolução**. :heavy_check_mark:
  - **Ação 2:** Se **Tratativa da reversão = Vale-crédito**: atualiza o status para **Gerar vale-crédito**. :heavy_check_mark:
  - **Ação 3:** Se **Tratativa da reversão = Pedido revertido**: atualiza o status para **Reativar o pedido**. :heavy_check_mark:
  - **Ação 4:** Se **Tratativa da reversão = Novo pedido**: atualiza o status para **Revertido**. :heavy_check_mark:
- **Devolução: Aguardando validação**
  - **Ação 1:** Se **Validação Comercial = Verdadeiro** e **Canal de venda = Vtex - Connect Parts** e **Evitar Reversão = Falso**: atualiza status para **Aguardando reversão**. :heavy_check_mark:
  - **Ação 2:** Se **Validação Comercial = Verdadeiro** e **Canal de venda = Vtex - Connect Parts** e **Evitar Reversão = Verdadeiro**: atualiza status para **Aguardando devolução**. :heavy_check_mark:
  - **Ação 3:** Se **Validação Comercial = Verdadeiro** e Canal de venda != Vtex - Connect Parts e Canal de venda != 00K - MercadoLibre: atualiza status para **Aguardando devolução**. :heavy_check_mark:
- **Devolução: Aguardando cancelamento**: Se **Status = Aguardando cancelamento** e **Ação backoffice = Cancelamento realizado**:
  - Ação 1: Se **Canal de venda = Vtex - Connect Parts** e **Valor a Devolver >= R$100,00**: atualiza status para **Aguardando validação**. :heavy_check_mark:
  - Ação 2: Se **Canal de venda = Vtex - Connect Parts** e **Evitar Reversão = Verdadeiro** e **Valor a Devolver < R$100,00**: atualiza status para **Aguardando devolução**. :heavy_check_mark:
  - Ação 3: Se **Canal de venda = Vtex - Connect Parts** e **Valor a Devolver >= R$100,00**: atualiza status para **Aguardando validação**. :x:
  - Ação 4: Se **Canal de venda = Vtex - Connect Parts** e **Evitar Reversão = Falso** e **Valor a Devolver < R$100,00**: atualiza status para **Aguardando reversão**. :heavy_check_mark:
  - Ação 5: Se **Canal de venda = 00K - MercadoLibre**: atualiza status para **Aguardando devolução**. :heavy_check_mark:
  - Ação 6: Se **Canal de venda != Vtex- Connect Parts** e **Canal de venda != 00K - MercadoLibre**: atualiza status para **Aguardando validação**. :heavy_check_mark:



- Lista de Status

- Aguardando cancelamento
- Inativar vale-crédito
- Alterar vale-crédito
- Reativar vale-crédito
- Vale-crédito gerado
- Vale-crédito alterado
- Aguardando correção

**CORREÇÕES**

- [x] Trocar o nome do campo Cancelamento para Ação backoffice.
- [x] Trocar o nome do campo Data do cancelamento para Data da ação

## IMPLANTAÇÃO

- [x] Migrar o fluxo do process builder
- [x] Migrar os novos campos
- [x] Migrar o novo layout
- [x] Adicionar tipo de registro do Cancelamento no objeto FC_Service__c
- [x] Alterar todas as filas backoffice para pegar os services de cancelamento
  - [x] Callcenter
  - [x] Ouvidoria
  - [x] Intermediações
  - [x] Perguntas
  - [x] Trocas
- [x] Criar as filas:
  - [x] Financeiro - Devolução concluída
  - [x] Callcenter - Revertidos
- [x] Ativar o tipo de registro nos perfil do administrador
- [x] Criar um service de teste
- [x] Ativar o fluxo do process builder
- [x] Testar com pedido 00K
- [x] Testar com pedido VTEX
- [x] Testar com pedido Marketplace

Correções:

- [x] Deixar como somente leitura o campo do status no layout
- [x] Editar as opções do campo Ação, para conter somente Devolução e Vale-crédito
- [x] Inserir o campo Evitar reversão no layout
- [x] Alterar alerta do service para mudar o icone para verde para os novos status
- [x] Devolver ao atendimento
- [x] Interação ao gerar vale-crédito
- [x] Travar e-mail do vale para a loja virtual
- [x] Quando for Devolução realizada, e marcar dados bancários o service volta para Aguardando correção e vai para a fila de dados bancários.
- [x] Forma de pagamento Cartão, Mercado Pago, Boleto
- [x] Botão reenviar email de vale
- [x] Botão atualizar status do pedido
- [x] Pedido revertido, muda o Status "Reativar o pedido"
- [ ] Alteraçao de DK, Informações de vale-crédito, Intervenção no pedido, Solicitação backoffice

Nova demanda:

1. Sempre que o canal for Mercado Livre ou Connect Parts deverá ter validação do comercial antes de seguir para o financeiro;
2. Montar uma visualforce com um campo para selecionar os itens do pedido que farão parte da devolução.
3. Calcular pela soma do valor qual é a categoria responsável por fazer a validação.
4. Gravar a categoria em um campo de texto (editável).
5. Se a soma dos valores dos itens for menor que R$100,00, seguir para devolução. Se não, seguir para o comercial validar.
6. O service irá cair em filas separadas por categorias e canal (ML ou LV).
7. Controller salva os itens selecionados em produtos de devolução (utilizar produtos do reenvio)

- [x] Integrar os itens de pedidos.
- [x] Atualizar fluxo do cancelamento
- [x] Montar a visualforce page e controller
- [x] Testar controller
- [x] Implantar



```markdown
Criaçaõ: 19/09/2018
Criado por: Leonardo A. Santos - Processos
Modificações: -
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2NTI0ODQxMDhdfQ==
-->