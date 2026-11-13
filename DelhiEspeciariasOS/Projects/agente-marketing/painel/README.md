# Painel DelhiAgente: como foi criado, como funciona e como reconstruir

Este documento e os arquivos desta pasta guardam **tudo** o que é preciso para entender o painel e reconstruí-lo do zero se ele for apagado ou quebrar.

| Arquivo | O que é |
|---|---|
| `README.md` | Este guia |
| `index.html` | **Cópia exata do código do painel** (página, estilos, cálculos, gráficos, botões) |
| `fontes.json` | **Cópia exata das configurações** do painel: título, idioma e cada fonte de dados (consultas ao Windsor e arquivo do radar) |
| `exemplo-programacao.json` | Exemplo do arquivo da programação semanal (a programação de teste de 16/11/2026) |
| `exemplo-radar.json` | Exemplo do arquivo do radar no formato certo (as pautas são de teste; serve só como modelo de formato) |

**Backup atualizado em:** 13/11/2026.

---

## 1. O que é o painel

- **Link atual:** https://claude.ai/artifact/SmGrnXxVVgLobi7tg7KWuY
- **Tipo:** artefato do claude.ai criado a partir do tipo **"Data" (Dashboard)**, endereço do tipo: https://claude.ai/artifact/GZLZthZ2sQjn7T16skfdeF
- **Título:** "Painel DelhiAgente" · **Idioma:** pt-BR
- **Dono:** conta do Brayan. Privado até ser compartilhado pelo menu de compartilhamento.

Um painel desse tipo não é uma página fixa: ele guarda os dados num "armazenamento" próprio (documentos) e cada vez que alguém abre, **as consultas rodam de novo** com o acesso de quem está abrindo.

### Como o armazenamento é organizado

| Documento | Conteúdo |
|---|---|
| `dash/meta` | `{title: "Painel DelhiAgente", lang: "pt-BR"}` |
| `datasets/<id>` | Cada fonte de dados (ver seção 3). Cópia em `fontes.json` |
| `files/index.html` | O código da página. Cópia em `index.html` (campo `text` do documento) |
| `feedback/<id automático>` | Avaliações 👍/👎 gravadas pelo próprio painel (seção 5) |
| `data/users/me/check`, `runs`, `page` | Diagnóstico gerado pelo painel quando alguém o abre (`check.status = "passed"` significa que funcionou) |

Arquivos (como o `radar.json`) são enviados como **asset** do painel e recebem um endereço `/_blob/<id>`.

---

## 2. O que o painel mostra

O painel tem **duas abas** (botões no topo): **"Marketing"** (abre por padrão; link `#radar-diario`, e `#programacao` ou `#marketing` também abrem ela) e **"Semanal: redes sociais"** (`#semanal`). A aba "Marketing" tem a programação semanal no topo e o radar diário abaixo.

### Aba "Marketing": programação semanal (abaixo do Radar de pautas)
Título "Programação semanal" e os cards (sem texto explicativo nem cabeçalho da semana, decisão de 12/11/2026). Os campos do item `semana` (foco, público, horário, revisão, o que precisamos) continuam no arquivo, mas não aparecem no painel.
1. **Um card por dia (seg a sex):** para cada item (feed e stories): canal · formato · horário · objetivo; **nota /100** (só o número, sem barras), selo **✅ Postar** e, se for o caso, **🧪 Teste da semana** e **🔄 Atualizado em DD/MM** (post trocado pelo radar de terça a sexta; campo `trocado` com `em`; só o selo, sem explicação); título e motivo (resumo da ideia); botão **Ver ideia completa**. Ao abrir: produto, **Estratégia**, **Por que neste dia**, **Por que neste horário**, tipo de foto, quem faz a imagem, hipótese do teste, telas (imagem, texto na arte, adesivo, prompt do Gemini + "Copiar prompt"), legenda + hashtags + "Copiar legenda", TikTok e atenção. Numa linha só: status **A fazer / Pronto / Postado** e **👍 Boa ideia / 👎 Fraca** (com motivo opcional). Dia sem pauta com nota 75 ou mais mostra **"Sem pauta forte para este dia"**. Sem links de fontes (decisão de 12/11/2026).
2. **Conferência da semana anterior:** só aparece quando o arquivo traz itens `conferencia`: para cada post do feed, nota, esperado, desempenho, veredito (✅ acertou · ❌ errou · 📈 subestimou · ⏸ não postado), métricas e o que o agente aprendeu.

**Avaliações da programação:** cada 👍/👎 grava um documento na coleção **`feedback_programacao`** com `item`, `titulo`, `semana`, `voto`, `motivo` e `em`. O DelhiAgente só lê.

**Status:** cada clique grava um documento na coleção **`programacao_status`** com `item` (id do post), `semana`, `status` e `em`. Vale o mais recente de cada item. O DelhiAgente só lê.

### Aba "Marketing": radar diário (Radar de pautas no topo; Ideias alternativas e Datas abaixo da programação)
1. **Radar de pautas:** card com a **nota do radar** (0 a 10, meta 8,5), cobertura/fontes/frescor, motivo da nota e histórico das notas; card "Pautas com nota 75 ou mais" (total e quantas acima de 85).
2. **💡 Ideias alternativas:** pautas com nota 75 ou mais que **não** estão na programação (campo `na_programacao` diferente de `true` no `radar.json`). Se todas estiverem na programação, aparece "Todas as pautas boas de hoje já estão na programação."
3. **Datas que se aproximam:** datas sazonais com contagem regressiva (destaque se faltam 21 dias ou menos).

Pautas **abaixo de 75 não aparecem** (decisão de 12/11/2026). Não existem cards de alerta/"cuidado" (decisão de 12/11/2026).

**Card de pauta (fechado):** produto · formato (ou "IA: vídeo/foto/carrossel") · público · nota /100 · tier · qualidade do radar · título · rótulos · 6 barras da nota (Fit Delhi /25, Momento /20, Sinal /20, Público /15, Produção IA /10, Perene /10) · **Por que combina com a Delhi** · botão **Ler mais** · 👍 Boa pauta / 👎 Fraca (👎 abre campo opcional de motivo).

**Ao clicar em "Ler mais":** Qualidade do radar (motivo) · Hook · Roteiro · Legenda + botão "Copiar legenda" · Prompts para IA (cada cena com tipo, duração, prompt, referência e texto na tela, + botão "Copiar prompt") · observação (`nota`) · fontes com links.

### Aba "Semanal: redes sociais"
1. Frase de abertura: semana analisada, visualizações do Instagram, posts e quanto os dias com post rendem a mais.
2. **Resumo da semana:** cards de Visualizações no Instagram, Seguidores no Instagram (hoje), Visualizações no TikTok, Vendas no TikTok Shop (GMV) e Dias sem post. Variação **só contra a semana anterior** (média de 4 semanas desativada, ver seção 6).
3. **TikTok Shop:** gráfico de GMV semanal (últimas 4 semanas), pedidos e ticket médio da semana. (A seção "Vendas por canal" com o teste do Bling foi retirada em 13/11/2026.)
4. **Redes sociais:** visualizações por dia do Instagram (pontos marcam dias com post) e do TikTok (4 semanas) + card "O que os dados mostram" (média de visualizações em dias com e sem post).
5. Rodapé "Como ler este painel" com as definições.

---

## 3. Fontes de dados (cópia exata em `fontes.json`)

Todas as consultas usam o conector **Windsor.ai**, ferramenta `get_data`, somente leitura. Período **`last_28d`** por causa do limite do plano de teste do Windsor (30 dias).

| id | Conector Windsor | Campos | Período |
|---|---|---|---|
| `ig_diario` | `instagram` | date, views, reach, accounts_engaged, total_interactions | last_28d |
| `ig_posts` | `instagram` | timestamp, media_type, media_like_count, media_comments_count, media_permalink | last_28d |
| `ig_seguidores` | `instagram` | followers_count | (atual) |
| `tt_diario` | `tiktok_organic` | date, video_views, likes, comments, shares, profile_views | last_28d |
| `shop_diario` | `tiktok_shop` | date, shop_performance_gmv_amount, shop_performance_orders, shop_performance_units_sold, shop_performance_product_page_views | last_28d |
| `vendas_teste` | (arquivo, **sem uso no painel desde 13/11/2026**) | `vendas-teste.json` com totais por canal (canal, pedidos, faturamento, ticket), tirado do Bling em 12/11/2026 às 13h06. Teste; sem dados de clientes | só 12/11/2026 |
| `programacao` | (arquivo) | `programacao.json` enviado como asset, formato JSON, `fixed: true` | trocado toda segunda (processo 7) |
| `radar` | (arquivo) | `radar.json` enviado como asset, formato JSON, `fixed: true` | trocado pelo radar diário |

Formato completo do `programacao.json`: ver `Skills/delhiagente/processos/7-programacao-semanal.md` e o `exemplo-programacao.json`. O campo `telas` também chega como texto JSON (usa `lerJson`).

Formato completo do `radar.json`: ver `Skills/delhiagente/processos/6-radar-diario.md` e o `exemplo-radar.json`.

**Atenção:** campos aninhados do `radar.json` (`criterios`, `rotulos`, `fontes`, `prompts`) chegam ao código como **texto JSON**, não como objeto. O código usa a função `lerJson` para convertê-los. Não remova essa função.

---

## 4. Cálculos (definidos no `index.html` com `dash.calc`)

| id | Entrada | O que calcula |
|---|---|---|
| `ig_semanas` | ig_diario | Visualizações e interações por semana (segunda a domingo), últimas 4 semanas, terminando no último domingo com dados |
| `tt_semanas` | tt_diario | Visualizações e curtidas por semana, mesma regra |
| `shop_semanas` | shop_diario | GMV, pedidos, ticket médio e **quantos dos 7 dias vieram** (`dias`, `completo`) por semana |
| `resumo` | ig_semanas, tt_semanas, shop_semanas | Para ig_views, tt_views, shop_gmv, shop_pedidos e shop_ticket: valor atual, semana anterior e variação %. Se a semana atual ou a anterior do TikTok Shop estiver incompleta, a variação fica vazia e o card mostra "Incompleto: faltam N dia(s)" |
| `efeito_posts` | ig_diario, ig_posts | Média de visualizações em dias com e sem post, multiplicador, último post, dias sem post (mostra "28+" se o último post saiu da janela) e posts na semana |
| `radar_resumo` | radar | Para o radar mais recente: total de pautas com nota ≥ 75, quantas hot (> 85) e quantas ideias (75–85) |

---

## 5. Avaliações 👍/👎

- O painel grava **um voto por pessoa por pauta** na coleção **`feedback`**: documento com id `<pessoa>__<data_radar>_<pauta>` e campos `quem` (id da pessoa no claude.ai ou, sem ele, um id deste navegador), `pauta`, `titulo`, `data_radar`, `voto` ("bom" ou "fraco"), `motivo` e `em`. Clicar de novo no mesmo voto desfaz; clicar no outro troca. A programação faz o mesmo em **`feedback_programacao`** (`item` no lugar de `pauta`).
- O código acessa o banco com `window.claude.use('db')`. Se não conseguir, os botões mostram "Avaliação indisponível nesta visualização".
- O DelhiAgente **só lê** essa coleção (processo 6) e registra o que aprendeu em `Projects/agente-marketing/aprendizados-radar.md`.
- Ao reconstruir o painel, as avaliações antigas **não voltam** (ficavam no painel antigo). Anote o fato em `aprendizados-radar.md`.

---

## 6. Regras e decisões que o código segue

- Página escrita na regra **"um escritor por parte"** do tipo Data (`<meta name="dash-one-writer">` no topo): textos fixos ficam no HTML; tudo que depende de dados é desenhado em elementos `data-draw`.
- Cores e fontes vêm dos tokens do tipo (`--color-*`, `--cds-*`), que seguem o tema claro/escuro. O laranja da marca **`#FC7D44`** aparece na linha do topo e no foco dos botões.
- **Comparação só com a semana anterior** enquanto o Windsor estiver no plano de teste (30 dias de histórico).
- **TikTok Shop incompleto:** se faltar algum dia, o valor aparece com o aviso e sem variação.
- **Sem seção Inbox** e **sem cards de cuidado/alerta**.
- **Produção com IA:** o critério "facilidade" aparece como **"Produção IA"**; cards podem ter `formato_ia` e `prompts`.
- O painel nunca mostra nome, CPF ou endereço de cliente.

---

## 7. Como reconstruir o painel do zero

Só faça isso **quando o Brayan pedir** (por exemplo, "o painel sumiu, reconstrói").

1. **Criar o artefato** a partir do tipo Data (https://claude.ai/artifact/GZLZthZ2sQjn7T16skfdeF), com o título "Painel DelhiAgente". Ele recebe um **link novo**.
2. **Enviar os arquivos do radar e da programação** (a programação mais recente ou, se não houver, gere pelo processo 7). Radar: use o radar mais recente que existir ou, se não houver, gere um novo seguindo o processo 6 (o `exemplo-radar.json` só mostra o formato). Envie como asset e anote o endereço `/_blob/<id>`.
3. **Gravar o armazenamento** em uma única operação em lote:
   - `dash/meta` = valor de `"dash/meta"` em `fontes.json`;
   - `datasets/<id>` = cada item de `"datasets"` em `fontes.json`, trocando em `datasets/radar` o `source.url` pelo novo endereço e atualizando `updated` e `edit` com a hora real;
   - `files/index.html` = `{text: <conteúdo de index.html>, edit: {via: "claude", at: <agora>}}`.
4. **Abrir o painel** e ler `data/users/me/check`: precisa ficar `"passed"`. Se aparecer `failed`, leia `data/users/me/runs` para ver o erro.
5. **Atualizar o link novo em todos os lugares:**
   - `Skills/delhiagente/SKILL.md`;
   - `Skills/delhiagente/processos/5-painel-e-resumo.md` e `6-radar-diario.md`;
   - este `README.md`;
   - o texto da tarefa agendada "DelhiAgente: radar diário + semanal" (precisa da aprovação do Brayan no computador dele).
6. **Conferir com o Brayan:** compartilhamento (o novo link começa privado) e acesso ao Windsor (cada pessoa que abre precisa do conector, ou o Brayan escolhe "Your access" em Fontes).

---

## 8. Manter este backup em dia

**Sempre que o código ou as fontes do painel mudarem**, quem fez a mudança atualiza nesta pasta:
- `index.html` (cópia nova do `files/index.html`);
- `fontes.json` (cópia nova de `dash/meta` e `datasets/*`);
- a data de "Backup atualizado em" e o histórico abaixo.

A troca diária do arquivo do radar e a troca semanal da programação **não** exigem atualizar o backup (o formato não muda).

## 9. Histórico de mudanças do painel

- **09/11/2026:** criado; cards de vendas/redes, oportunidades e 3 ideias.
- **12/11/2026:** janela de 28 dias (limite do Windsor teste); comparação só com a semana anterior; TikTok Shop "incompleto"; sem cards de cuidado; radar de pautas com nota 0–100, hot ideas, ideias, 👍/👎; duas abas (Radar diário / Semanal); produção com IA (critério "Produção IA" e prompts); botão "Ler mais"; seção Inbox removida; teste de vendas do dia pelo Bling (fonte `vendas_teste`) no lugar do aviso "Aguardando o Bling".
- **12/11/2026 (tarde):** teste de vendas do dia pelo Bling; aba **Programação** (primeira) com programação semanal de seg a sex, status A fazer/Pronto/Postado (coleção `programacao_status`) e sugestão de troca vinda do radar.
- **12/11/2026 (fim da tarde):** aba Programação sem título e sem cabeçalho da semana: só os cards dos dias (e a sugestão do radar quando houver).
- **12/11/2026 (fim da tarde):** título "Programação" de volta na aba, sem texto abaixo.
- **12/11/2026 (fim da tarde):** título da aba Programação trocado para "Programação semanal".
- **12/11/2026 (noite):** programação com a lógica do radar: nota por post (≥ 75), selo Postar, estratégia, porquê do dia e do horário, teste da semana, 👍/👎 (`feedback_programacao`), "Sem pauta forte" e seção de conferência da semana anterior.
- **12/11/2026 (noite):** abas "Programação" e "Radar diário" juntas numa aba só, **"Marketing"** (programação no topo, radar abaixo); card da programação enxuto (nota, selo, título e resumo) com botão "Ver ideia completa".
- **12/11/2026 (noite):** radar de terça a sexta passa a trocar posts da programação com nota maior (selo 🔄 Atualizado); bloco de sugestão de troca removido.
- **12/11/2026 (noite):** troca mostrada só com o selo 🔄 (sem a ideia anterior nem o motivo); dias que já passaram nunca são trocados.
- **12/11/2026 (noite):** o post do dia nunca é trocado, mesmo se o radar rodar de novo; trocas só de amanhã até sexta da semana em curso.
- **12/11/2026 (noite):** Radar de pautas movido para o topo da aba Marketing (acima da programação); seções Hot ideas e Ideias juntas em **💡 Ideias alternativas** (só pautas fora da programação, campo `na_programacao`); card de contagem mostra "Pautas com nota 75 ou mais" e quantas acima de 85.
- **12/11/2026 (noite):** área de Vendas por canal redesenhada (cards de total separados, tabela alinhada, canais sem venda numa linha só).
- **13/11/2026:** rótulos "Texto na tela (Canva)" e "Texto na arte (Canva)" trocados por "(Claude)": o texto das artes passa a ser aplicado pelo Claude.
- **13/11/2026:** 👍/👎 com **um voto por pessoa por ideia** (radar e programação): o documento de voto tem id `<pessoa>__<ideia>` e o campo `quem`; clicar de novo no mesmo voto desfaz, clicar no outro troca; o voto da pessoa aparece marcado ao abrir o painel; a contagem ignora votos antigos sem `quem`.
- **13/11/2026 (tarde):** seção "Vendas por canal" (teste do Bling) retirada; a seção passa a se chamar "TikTok Shop" (gráfico mantido); aba renomeada para "Semanal: redes sociais"; nota "Vendas dos outros canais…" removida do rodapé. Obs.: o código também tem as mudanças de votação 👍/👎 (um voto por pessoa) feitas em outra conversa às 13h40.
