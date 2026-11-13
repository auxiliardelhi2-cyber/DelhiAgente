# Processo 7: Programação semanal (segunda-feira)

Toda segunda, depois do Radar diário e do Semanal, monte a **programação completa de segunda a sexta** da semana que começa. Cada post passa pela **mesma análise das pautas do radar**: nota de 0 a 100, só entra com 75 ou mais, e cada escolha de post, dia e horário tem um porquê. Nada de chute. Decisão do Brayan e do Natajhi em 12/11/2026.

**Painel:** https://claude.ai/artifact/SmGrnXxVVgLobi7tg7KWuY (aba "Marketing", no topo)

Leia antes: `Context/estrategias-marketing.md` (a teoria) e `Projects/agente-marketing/aprendizados-programacao.md` (o que já funcionou ou falhou na Delhi).

## Regras fixas da semana

| Item | Regra |
|---|---|
| Feed do Instagram | **3 posts:** segunda, quarta e sexta. Foto única ou carrossel |
| Stories | **Todos os dias**, de segunda a sexta, de 2 a 4 telas |
| TikTok | Os **carrosséis** do feed são repostados como carrossel de fotos, com a mesma legenda |
| Vídeo | **Nada de vídeo por enquanto:** só imagens (decisão de 12/11/2026) |
| Venda direta | No máximo **1 post de venda** por semana no feed |
| Variedade | Não repita o mesmo produto no feed na mesma semana. Passe por pelo menos 3 pilares de conteúdo |
| Teste | **1 post por semana** é o teste da semana (ver passo 5) |

## 1. Conferir a semana anterior e aprender

Faça isto **antes** de montar a semana nova. Na primeira semana, pule para o passo 2.

1. **Status:** leia a coleção `programacao_status` do painel (somente leitura): vale o registro mais recente de cada `item` ("a_fazer", "pronto" ou "postado").
2. **Avaliações:** leia a coleção `feedback_programacao` (somente leitura): `quem` (id da pessoa), `item`, `titulo`, `semana`, `voto` ("bom" ou "fraco"), `motivo`, `em`. Cada documento é o voto atual de uma pessoa num post (no máximo um por pessoa); ignore documentos sem `quem`.
3. **Resultados:** pelo Windsor (`instagram`: `timestamp`, `media_type`, `media_reach`, `media_views`, `media_saved`, `media_shares`, `media_permalink`), ache cada post do feed da semana anterior pela data e confira os números. Stories não entram na conferência (o Instagram só guarda os dados por 24 horas); para eles, vale só o status.
4. **Base de comparação:** a mediana do alcance dos posts do feed das 4 semanas anteriores à semana conferida. Se houver menos de 3 posts nesse período, use a mediana dos posts da própria semana conferida e diga isso.
5. **Desempenho** de cada post: "acima" (alcance de 120% da base ou mais), "na média" (de 80% a 120%) ou "abaixo" (menos de 80%). Se o objetivo do post era ensinar, olhe também os salvamentos; se era atrair, os compartilhamentos.
6. **Expectativa** pela nota que você deu: 82 ou mais = "acima"; de 75 a 81 = "na média".
7. **Veredito:**
   - desempenho igual à expectativa → **"acertou"**;
   - desempenho pior → **"errou"** (escreva o motivo provável: tema, formato, dia, horário, capa, ou post não publicado);
   - desempenho melhor → **"subestimou"** (escreva o que funcionou além do esperado).
   - Post não marcado como "postado" e não encontrado no Instagram → **"não postado"**: não conta como acerto nem erro.
8. **Aprenda sempre, acertando ou errando.** Acrescente no fim de `Projects/agente-marketing/aprendizados-programacao.md` uma entrada no modelo do próprio arquivo, com o que se confirmou, o que se contradisse, os números e o que muda na próxima semana. Leve em conta os 👍/👎 e os motivos.
9. **Sugestão para o OS:** se algum aprendizado da semana vale além do marketing (uma preferência geral do Brayan ou da Delhi), escreva-o como sugestão de princípio no resumo semanal (`processos/5-painel-e-resumo.md`). **Nunca escreva em `Context/principios.md`:** só o Brayan aprova.
10. Monte um item `conferencia` para cada post do feed conferido (ver passo 6).

## 2. Escolher os candidatos

- **Fontes, nesta ordem:** pautas do radar de hoje e da semana anterior com nota 75 ou mais (hot ideas primeiro), datas sazonais dos próximos 60 dias e os aprendizados da programação.
- **Público:** use o dado de idade e gênero dos seguidores (Windsor `instagram`: `audience_gender_age_name`, `audience_gender_age_size`).
- Confira feriados da semana.
- Siga `processos/3-oportunidades.md` (filtro do que nunca vira pauta) e `processos/4-ideias-de-conteudo.md` (regras de prompt, fidelidade e legenda).

## 3. Dar nota a cada post (0 a 100)

Use **a mesma tabela do radar** (`processos/6-radar-diario.md`, passo 3): `fit` (25), `momento` (20), `sinal` (20), `publico` (15), `facilidade` (10, produção só com imagens) e `perene` (10). Nos posts da programação, considere também:

- **Momento:** a ligação com o dia escolhido (data próxima, feriado, véspera de compra, sequência da semana).
- **Aprendizados:** uma estratégia ou formato confirmado na conferência pode somar até **+10**; um que falhou pode tirar até **-10**. Escreva o ajuste e o motivo em `ajuste`.
- A nota de um post que vem de uma pauta do radar pode mudar na programação (outro formato, outro dia). Recalcule; não copie.
- Seja honesto: não infle notas para preencher a semana.

**Só entra o que tiver 75 ou mais**, também nos stories. Se nenhum candidato chegar a 75 para um dia ou canal, **não preencha com uma pauta fraca**: crie um item `sem_pauta` para aquele dia e canal (decisão do Brayan em 12/11/2026).

## 4. Dia, horário e estratégia

- **`estrategia`:** o nome de uma estratégia do catálogo de `Context/estrategias-marketing.md`.
- **`por_que_dia`:** por que este post neste dia (data, feriado, sequência "ensinar antes de vender", aprendizado de dia que funcionou).
- **`por_que_horario`:** com dado, quando houver. Regra:
  - Enquanto houver menos de 6 posts do feed com resultado conferido, o horário é **teste**: alterne 12h e 19h, marque `horario_teste: true` e diga isso.
  - Depois, use o horário com maior alcance médio nas últimas 4 semanas e escreva os números.
  - **Nunca** apresente um horário genérico da internet como se fosse dado da Delhi.
- **`motivo`:** a frase que justifica postar (aparece ao lado do selo ✅ Postar).

## 5. Teste da semana

Marque **1 post** com `teste_semana: true` e escreva a `hipotese` (ex.: "Foto única de produto rende menos alcance que carrossel"). Escolha:

- algo ainda não testado (formato, tema, horário, tipo de capa); ou
- algo que falhou há mais de 4 semanas (pode ter mudado); ou
- uma nova versão de algo que acertou, para ver se continua funcionando.

Mude **uma variável só** em relação ao que já se sabe. O post de teste também precisa de nota 75 ou mais.

## 6. Montar o arquivo `programacao.json`

Uma lista JSON. Itens:

```json
{"tipo": "semana", "id": "sem-AAAA-MM-DD", "inicio": "AAAA-MM-DD", "fim": "AAAA-MM-DD", "gerada_em": "AAAA-MM-DD", "teste": false,
 "nota_programacao": 0, "nota_motivo": "", "foco": "", "publico": "", "horario": "", "revisao_anterior": "", "precisa": "", "observacao": ""}

{"tipo": "post", "id": "AAAA-MM-DD-feed", "dia": "AAAA-MM-DD", "dia_semana": "Seg", "canal": "feed | stories",
 "nota": 0, "criterios": {"fit": 0, "momento": 0, "sinal": 0, "publico": 0, "facilidade": 0, "perene": 0}, "ajuste": "",
 "motivo": "", "estrategia": "", "por_que_dia": "", "por_que_horario": "", "teste_semana": false, "hipotese": "",
 "horario": "19:00", "horario_teste": true, "objetivo": "Ensinar | Engajar | Vender | Atrair", "formato": "carrossel | foto única | stories (3 telas)",
 "produto": "", "pauta_id": "p1", "titulo": "", "tipo_foto": "", "quem_faz": "",
 "telas": [{"n": 1, "origem": "Arte (Claude) | Gemini | Foto real | Repost", "imagem": "", "texto": "", "prompt": "", "adesivo": ""}],
 "legenda": "", "hashtags": "", "tiktok": "", "nota_extra": ""}

{"tipo": "sem_pauta", "id": "AAAA-MM-DD-stories", "dia": "AAAA-MM-DD", "dia_semana": "Ter", "canal": "feed | stories", "motivo": ""}

{"tipo": "conferencia", "id": "c-AAAA-MM-DD-feed", "item": "AAAA-MM-DD-feed", "dia": "AAAA-MM-DD", "titulo": "", "nota": 0,
 "esperado": "acima | na média", "desempenho": "acima | na média | abaixo | não postado", "veredito": "acertou | errou | subestimou | não postado",
 "metricas": "alcance 0 (base 0) · salvamentos 0 · compartilhamentos 0", "aprendizado": ""}
```

- `nota` = soma dos critérios + ajuste. Confira a soma.
- `nota_programacao` (0 a 10): o quanto a semana está bem embasada (média das notas dos posts dividida por 10, menos 1 ponto por dia `sem_pauta` e menos 1 ponto se o horário ainda for teste). Escreva o porquê em `nota_motivo`.
- `texto` de cada tela: é aplicado pelo Claude na imagem final, não no Canva (decisão de 13/11/2026; fluxo em `processos/4-ideias-de-conteudo.md`).
- `nota_extra`: o que conferir antes de publicar (rótulo, feriado, etiqueta de cliente).
- `precisa`: o que falta para produzir (fotos reais, logo).
- O painel **não mostra** as barras dos critérios nem links de fontes (decisão do Brayan em 12/11/2026). O card fechado mostra canal, formato, horário, objetivo, nota, selo, título e `motivo` (o resumo da ideia, em 1 ou 2 frases curtas); o resto aparece no botão "Ver ideia completa".
- Não repita ids de semanas anteriores.
- **Validar antes de enviar:** o JSON abre sem erro; toda nota é a soma dos critérios + ajuste; todo `post` tem nota 75 ou mais; dias sem candidato têm `sem_pauta`; há 1 `teste_semana`; no máximo 1 "Vender" no feed; toda tela "Gemini" tem prompt; nenhum prompt pede rosto, texto na imagem ou produto inventado; nenhuma legenda tem preço, desconto ou promessa de saúde; toda legenda do feed termina com o fechamento padrão.

## 7. Atualizar o painel

1. Envie o `programacao.json` para o painel como arquivo (asset). Você recebe um endereço `/_blob/<id>`.
2. Atualize `datasets/programacao`: `source.url` com o novo endereço, `updated` com `{at: <agora>, by: "DelhiAgente — programação da semana de DD/MM/AAAA"}` e `edit` com `{via: "claude", at: <agora>}`. Use a versão atual do documento.
3. **Marque o radar de hoje:** no `radar.json` de hoje, ponha `na_programacao: true` nas pautas que entraram na programação (as outras com 75 ou mais aparecem no painel como "Ideias alternativas"). Envie o `radar.json` de novo como asset e atualize `datasets/radar` (`source.url`, `updated`, `edit`).
4. **Não apague** arquivos antigos do painel. Não altere o código do painel. Não escreva nas coleções `programacao_status` e `feedback_programacao` (quem escreve é a equipe).

## Durante a semana (radar de terça a sexta)

Decisão do Brayan em 12/11/2026: de terça a sexta, o radar diário **troca** um post da programação (só de amanhã até sexta; o post do dia nunca muda) quando encontra uma ideia com **nota maior** no mesmo canal, desde que o post ainda esteja "a fazer". Regras completas: `processos/6-radar-diario.md`, passo 5a. O item trocado mantém o `id` e ganha o campo `trocado`. A conferência de segunda avalia a versão final de cada post.
