# Passo 2: Vendas por canal

> **Pausado em 13/11/2026** (decisão do Brayan): o painel e o resumo semanal mostram só as redes sociais (o TikTok Shop continua). Não rode este passo até o Brayan pedir. Ideia para depois: um gráfico com o total de vendas da semana comparado ao total da semana anterior, para saber se a Delhi está melhorando.

## Situação atual

**Aguardando a conexão do Bling no Windsor**, que precisa de autorização do administrador do Bling. Enquanto isso:

- Pule este passo.
- Registre no resumo: "Vendas por canal: aguardando Bling no Windsor".
- **Não** tente ler pedido por pedido pelo conector direto do Bling. São mais de 100 pedidos por dia, o que é lento e traz dados pessoais de clientes.

## Quando o Bling estiver no Windsor

1. Puxe os pedidos da semana analisada e das 4 anteriores **já somados por dia e por loja** (o Windsor agrega).
2. Traduza o número da loja para o canal usando a tabela de `identidade.md`. As duas integrações do Mercado Livre somam como "Mercado Livre". As duas da Amazon aparecem separadas (Full e envio próprio) e também com o total da Amazon.
3. **Exclua os pedidos cancelados** do faturamento, sem mostrá-los.
4. Calcule por canal: faturamento, pedidos e ticket médio, contra a semana anterior (a média de 4 semanas só volta quando o Windsor tiver histórico suficiente).
5. Magazine Luiza fica fora da análise.

## Regras

- Nunca leia nome, CPF ou endereço de cliente.
- Loja com número desconhecido: liste como "Loja não identificada (nº X)" e avise o Brayan. Não adivinhe o canal.
