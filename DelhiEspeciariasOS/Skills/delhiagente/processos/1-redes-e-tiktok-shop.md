# Passo 1: Redes e TikTok Shop

## Fonte

Windsor.ai, **somente leitura** (ferramenta de buscar dados; nunca as de ação ou envio de arquivos).

| Conector Windsor | Conta | Campos usados |
|---|---|---|
| `instagram` | delhiespeciarias | `date`, `views`, `reach`, `accounts_engaged`, `total_interactions`; posts: `timestamp`, `media_type`, `media_permalink`; seguidores: `followers_count` |
| `tiktok_organic` | Delhi Especiarias | `date`, `video_views`, `likes`, `comments`, `shares`, `profile_views` |
| `tiktok_shop` | Delhi Especiarias | `date`, `shop_performance_gmv_amount`, `shop_performance_orders`, `shop_performance_units_sold`, `shop_performance_product_page_views` |

O painel já puxa esses dados sozinho. Neste passo você **confere** os números e **extrai** o que vai para o resumo.

## O que extrair (semana analisada)

- Instagram: visualizações, interações, posts publicados, seguidores (hoje), dias desde o último post.
- TikTok: visualizações, curtidas.
- TikTok Shop: GMV (R$), pedidos, ticket médio (GMV ÷ pedidos).
- Para cada número: variação **contra a semana anterior**. A média de 4 semanas fica desativada enquanto o Windsor estiver no plano de teste, que só guarda 30 dias de histórico. Não tente calculá-la nem a marque como pendente.

## TikTok Shop incompleto

Confira se a semana analisada **e** a anterior vieram com os 7 dias no TikTok Shop. Se faltar algum dia, mesmo depois de repetir a busca:

- Escreva o valor como **"incompleto"**, por exemplo "TikTok Shop: R$ 431,08 em 10 pedidos (**incompleto**, faltou 06/11)".
- **Não calcule variação** nem ticket comparado.
- Não estime o dia que faltou.

O painel faz a mesma marcação sozinho.

## Como buscar

- Use sempre **datas exatas** (`date_from` e `date_to`), não períodos prontos como "últimos 7 dias".
- Confira se a resposta trouxe exatamente os 7 dias da semana analisada. Se faltar ou sobrar um dia (datas deslocadas), repita a busca. Se o problema continuar, registre no resumo.

## Checagens

- **Variação acima de 50%** em relação ao último resumo vira "ponto de atenção", com uma hipótese marcada como hipótese. Exemplo: "Hipótese: subiu porque houve 2 posts".
- Dia com valor vazio: anote e não corrija por conta própria.
- **Interações negativas no Instagram** (ex.: −1) vêm da própria plataforma (curtidas desfeitas). Não corrija e só cite no resumo se mudarem o total da semana.
- **Zero na semana inteira** em uma fonte: trate como possível falha de coleta, não como queda. Escreva "conferir: possível falha de coleta" e não calcule variação para essa fonte.
- **Se o Windsor não responder**, registre: "Redes: sem dados nesta semana (Windsor não respondeu)".
