# Processo 6: Radar diário (segunda a sexta)

Inspirado no "Dexter": achar pautas em alta, dar uma nota a cada uma, separar as melhores e aprender com as avaliações da equipe.

**Painel:** https://claude.ai/artifact/SmGrnXxVVgLobi7tg7KWuY (aba "Marketing", seções do radar)

## 0. Já rodou hoje?

Leia `datasets/radar` do painel. Se `updated.at` for **de hoje**:

- **Na rotina automática (tarefa agendada):** não faça um novo radar. Só avise o Brayan que o radar de hoje já existe.
- **Se o Brayan pedir numa conversa para rodar** (por exemplo "roda o DelhiAgente", "roda o radar", "refaz o radar"): faça um radar novo **direto, sem perguntar**, e substitua o de hoje. Decisão do Brayan em 12/11/2026. No arquivo novo:
  - **mantenha** a nota do radar anterior no histórico, com o id `n-AAAA-MM-DD-1`;
  - dê à nota nova o id `n-AAAA-MM-DD-2` (ou `-3`, e assim por diante);
  - avise no final que o radar de hoje foi refeito.

## 1. Aprender com as avaliações

1. Leia a coleção `feedback` do painel (somente leitura). Cada documento tem `pauta`, `titulo`, `data_radar`, `voto` ("bom" ou "fraco"), `motivo` e `em`.
2. Considere só as avaliações **depois** da data do último registro em `Projects/agente-marketing/aprendizados-radar.md`.
3. Para cada 👎 com motivo, decida se muda algo no radar de hoje. Por exemplo: um formato rejeitado perde pontos de "público", ou um tema rejeitado deixa de ser pesquisado. Para cada 👍, procure o que a pauta tinha de diferente e repita.
4. **Acrescente** no fim do arquivo de aprendizados uma entrada no modelo abaixo. Se não houver avaliação nova, escreva "sem avaliações novas".

```markdown
### AAAA-MM-DD
- Avaliações lidas: N (👍 X · 👎 Y)
- Aprendizado: …
- O que muda no radar: …
```

## 2. Pesquisar

- Siga as regras de `processos/3-oportunidades.md`: temas, filtro do que nunca vira pauta, qualidade da evidência e fontes de no máximo 12 meses.
- Procure de **6 a 10 pautas**. Cada pauta começa por **um produto Delhi**.
- Uma pauta descartada antes pode voltar se o sinal dela crescer, com nota nova.
- Formatos de vídeo em alta ("mostre o prato pronto primeiro" etc.) contam como sinal, desde que tenham fonte.

### 2a. Google Trends (uma consulta por dia)

O Google Trends mostra o que as pessoas **buscam no Brasil**: é a evidência mais forte da regra de qualidade (comportamento do consumidor). A leitura automática comum é bloqueada pelo Google, então use o **navegador do Claude** (built-in browser) deste computador.

1. Abra **uma única** comparação, com até **5 termos em português**, Brasil, últimos 90 dias. Modelo de endereço:
   `https://trends.google.com/trends/explore?geo=BR&q=TERMO1,TERMO2,TERMO3,TERMO4,TERMO5&date=today%203-m&hl=pt-BR`
   (troque espaços por `%20` e acentos pela forma codificada, ou deixe o navegador codificar).
2. **Espere os dados carregarem:** a página leva cerca de 25 a 30 segundos. Confira a cada 5 segundos, por até 60 segundos, se o texto da página já tem "Média" e "Pesquisas relacionadas". Depois **role até o fim da página** algumas vezes para carregar as buscas de cada termo.
3. **Leia:** a linha "Média" (interesse relativo entre os termos, de 0 a 100) e, para cada termo, as **Pesquisas relacionadas** ("Em ascensão" ou "Principais").
4. **Se aparecer "Ops, ocorreu um erro"** ou nada carregar em 60 segundos: recarregue **uma vez** e repita o passo 2. Se falhar de novo, registre "Trends indisponível hoje" no motivo da nota do radar e siga com a pesquisa normal. **Nunca invente** números do Trends.
5. **Faça só uma consulta por dia**, para não ser bloqueado pelo Google.
6. **Reveze os termos** pela lista fixa abaixo (decisão do Brayan em 13/11/2026). Use **termos com contexto de cozinha**, nunca palavras soltas que misturam outros assuntos: em 13/11, "curry" trouxe buscas sobre o ator Tim Curry e "chai" trouxe novelas e aplicativos. Se um termo da lista não trouxer nada, troque por uma variação do mesmo produto e anote no motivo da nota do radar.

   | Dia | Termos da consulta (até 5) |
   |---|---|
   | Segunda | manteiga ghee · chai latte · molho de tahine · frango ao curry · açafrão da terra |
   | Terça | garam masala · raspador de língua · arroz com cúrcuma · homus · adoçante natural |
   | Quarta | receita com ghee · chá chai receita · curry de legumes · tahine · açúcar de coco |
   | Quinta | frango garam masala · arroz com ghee · ceia sem lactose · receitas de natal* · chai gelado |
   | Sexta | os 5 termos que mais renderam na semana, ou variações novas de produtos sem resultado |

   \* Na quinta, o termo sazonal acompanha a data mais próxima da lista de datas sazonais (por exemplo, "receitas de natal" em novembro e dezembro, "bebidas geladas" no verão).
7. **Use como sinal das pautas:** buscas em alta viram pauta ou fortalecem uma pauta (critério `sinal` e `momento`). Na fonte da pauta escreva, por exemplo, `{"nome": "Google Trends: 'receitas com tahine' +150% (Brasil, 90 dias)", "url": "<endereço da consulta>", "data": "<hoje>"}`.
8. **Buscas sobre "benefícios"** (ex.: "benefícios da manteiga ghee") mostram interesse real, mas a regra de saúde continua valendo: responda com atributos do rótulo (0% lactose, 0% caseína), nunca com promessa de saúde.
9. Buscas de **intenção de compra** ("onde comprar", tamanho como "500g") valem destaque: são pautas de produto com chamada para a loja.
10. Feche a aba do Trends ao terminar.

## 3. Dar nota (0 a 100)

| Critério | Máx. | O que mede |
|---|---|---|
| `fit` | 25 | Quanto a pauta depende de um produto Delhi (marca própria vale mais) |
| `momento` | 20 | Está em alta agora ou combina com uma data próxima |
| `sinal` | 20 | Força e qualidade da evidência: dado de comportamento no Brasil vale mais; métrica não verificada vale menos |
| `publico` | 15 | Encaixe com o público 60+ ou 20–50 |
| `facilidade` | 10 | **Produção com IA:** dá para fazer só com IA a partir de fotos reais dos produtos (10). Perde pontos se exigir cozinhar ou gravar de verdade, rostos ou um produto sem foto |
| `perene` | 10 | Continua útil depois (10) ou morre em dias (baixo) |

- `score` = soma dos 6. Confira a soma.
- **Faixas:** acima de 85, 🔥 hot · de 75 a 85, 💡 ideia. **Pautas abaixo de 75 são descartadas:** não entram no `radar.json`, no painel nem na resposta ao Brayan (decisão do Brayan em 12/11/2026).
- `tier`: "A" = pronta para gerar com IA; "B" = precisa de roteiro, foto de referência ou pesquisa antes.
- `qualidade_radar`: "alta", "média" ou "baixa", com o motivo em `qualidade_motivo`.
- **As 3 pautas de maior nota** sempre recebem `hook`, `roteiro`, `prompts` e `legenda`, seguindo `processos/4-ideias-de-conteudo.md` (produção com IA). As outras precisam ao menos de `hook` quando ficarem em 75 ou mais.
- Seja honesto: não infle notas para ter hot ideas. Um dia sem hot idea é normal.

## 4. Nota do radar (0 a 10)

Média de três notas:

- `cobertura`: quantos dos 4 temas tiveram pelo menos uma pauta.
- `qualidade_fontes`: quanto da evidência é dado verificado e quanto é métrica não verificada ou opinião.
- `frescor`: idade das fontes (últimas 2 semanas = 10).

Escreva em `motivo` o porquê da nota, em 1 ou 2 frases. **Meta: 8,5.** Se ficar abaixo da meta, diga em `motivo` o que faria a nota subir.

## 5. Montar o arquivo `radar.json`

Uma lista JSON com:

```json
{"id": "p1", "tipo": "pauta", "data": "AAAA-MM-DD", "titulo": "", "produto": "", "score": 0,
 "criterios": {"fit": 0, "momento": 0, "sinal": 0, "publico": 0, "facilidade": 0, "perene": 0},
 "tier": "A", "rotulos": [""], "qualidade_radar": "média", "qualidade_motivo": "",
 "fit_delhi": "", "formato": "", "publico": "60+ | 20–50 | alternar", "na_programacao": false,
 "formato_ia": "vídeo | foto | carrossel",
 "hook": "", "roteiro": "", "legenda": "", "nota": "",
 "prompts": [{"cena": "1. Abertura", "tipo": "vídeo", "duracao": "4 s", "prompt": "", "referencia": "foto real da embalagem do …", "texto_tela": ""}],
 "fontes": [{"nome": "", "url": "", "data": "AAAA-MM-DD"}]}
{"id": "s1", "tipo": "sazonal", "tema": "", "data": "AAAA-MM-DD", "como_adaptar": ""}
{"id": "n-AAAA-MM-DD", "tipo": "nota_radar", "data": "AAAA-MM-DD", "nota": 0, "cobertura": 0, "qualidade_fontes": 0, "frescor": 0, "motivo": ""}
```

- **Pautas:** só as de hoje com nota 75 ou mais.
- **`na_programacao`:** `true` nas pautas que já estão na programação da semana em curso (a mesma ideia, mesmo com outro título ou formato) ou que entraram nela hoje pelo passo 5a. O painel mostra as outras como **💡 Ideias alternativas** (decisão do Brayan em 12/11/2026). Na segunda, quem marca é o processo 7, depois de montar a programação.
- **Datas sazonais:** as dos próximos 60 dias, com o ângulo e nunca o preço.
- **Notas do radar:** copie as do arquivo anterior (até as 30 mais recentes) e acrescente a de hoje. É o histórico que o painel mostra.
- **Validar antes de enviar:** o JSON abre sem erro; todo item tem `id` e `tipo` (`pauta`, `sazonal` ou `nota_radar`); cada `score` é a soma dos critérios; as 3 maiores notas têm hook, roteiro, prompts e legenda; nenhum prompt pede rosto, texto na imagem ou produto inventado; nenhuma legenda tem preço, desconto ou promessa de saúde. Se algo falhar, corrija antes de enviar.

## 5a. Atualizar a programação da semana (terça a sexta)

Decisão do Brayan em 12/11/2026: de terça a sexta, o radar **troca** um post da programação quando encontra uma ideia com nota maior. Na segunda, não faça este passo (a programação acabou de ser montada pelo processo 7).

1. Leia a programação atual (`datasets/programacao`, arquivo `programacao.json`) e a coleção `programacao_status` (somente leitura; vale o registro mais recente de cada item).
2. **Posts que podem ser trocados:** só os de **amanhã até sexta** da **semana em curso** (a programação cuja semana contém o dia de hoje; se a programação no painel for de uma semana que ainda não começou, não troque nada). Decisão do Brayan em 12/11/2026:
   - **o post de hoje nunca muda**, nem se o radar rodar de novo no mesmo dia (por exemplo, às 15h a pedido do Brayan) e nem se o horário dele ainda não chegou, para não causar confusão;
   - **dias que já passaram nunca mudam**, mesmo que estejam "a fazer";
   - dos dias que restam, só os que **não** estejam marcados como "pronto" ou "postado" (a equipe já produziu ou publicou).
   Na sexta, não há o que trocar.
3. Para cada post que pode ser trocado, veja se alguma pauta de hoje, **no mesmo canal** (feed ou stories), teria nota **maior** do que a do post atual. Dê a nota com as regras de `processos/7-programacao-semanal.md` (passo 3), considerando aquele dia e horário. Não copie a nota do radar.
4. **Só troque se** a nota nova for maior e a semana continuar seguindo as regras do processo 7: no máximo 1 "Vender" no feed, sem repetir produto no feed, só imagens, o post de teste da semana mantido (não troque o post com `teste_semana: true`).
5. Um dia com `sem_pauta` também pode ganhar um post, se uma pauta nova chegar a 75 ou mais.
6. **O post novo vem completo**, como no processo 7: nota, motivo, estratégia, por que neste dia, por que neste horário, tipo de foto, quem faz, telas, prompts, legenda. Mantenha o mesmo `id` do item trocado e acrescente:

   ```json
   "trocado": {"em": "AAAA-MM-DD"}
   ```

   Não é preciso explicar a troca: se trocou, é porque a ideia nova tem nota maior (decisão do Brayan em 12/11/2026).
7. Se nada for trocado, **não mexa** no arquivo da programação.
8. Se trocou: envie o novo `programacao.json` como asset e atualize `datasets/programacao` (`source.url`, `updated` com `{at: <agora>, by: "DelhiAgente — programação atualizada em DD/MM/AAAA"}` e `edit`). Diga na resposta ao Brayan quais dias foram trocados.

O card trocado mostra só o selo "🔄 Atualizado em DD/MM" no painel. A conferência da segunda seguinte confere a versão final de cada post.

## 6. Atualizar o painel

1. Envie o `radar.json` para o painel como arquivo (asset). Você recebe um endereço `/_blob/<id>`.
2. Atualize `datasets/radar`: `source.url` com o novo endereço, `updated` com `{at: <agora>, by: "DelhiAgente — radar de DD/MM/AAAA"}` e `edit` com `{via: "claude", at: <agora>}`. Use a versão atual do documento.
3. **Não apague** arquivos antigos do painel.
4. Não altere o código do painel. Não escreva nas coleções `feedback`, `feedback_programacao` e `programacao_status`.
5. **Abra o painel** nesta conversa (ação "abrir/open" da ferramenta de artefatos, com o link do painel), para ele aparecer para o Brayan. Não crie um painel novo.
