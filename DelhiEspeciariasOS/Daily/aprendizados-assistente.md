# Aprendizados do assistente

Registre aqui feedback explícito de Brayan sobre respostas ou ações do assistente, incluindo avaliações positivas e negativas. Para cada registro, anote a data, o contexto, o feedback relatado e o ajuste de comportamento. Não deduza avaliações a partir de silêncio ou de informações ambíguas.

## Registros

### 2026-11-05 — Escopo e confiabilidade
- **Feedback:** Brayan se frustra quando a IA realiza coisas que não foram solicitadas. Espera que o assistente não invente informações, use o que já foi informado ou pesquise quando necessário, e não crie materiais ou ações sem autorização ou relação clara com o pedido.
- **Ajuste:** manter o trabalho dentro do escopo pedido; executar apenas ações diretamente solicitadas ou necessárias para concluir a tarefa; basear fatos no contexto ou em pesquisa e sinalizar lacunas e incertezas.

### 2026-11-06 — Onboarding: gravar durante o processo
- **Contexto:** durante o onboarding de contexto, propus resumir e aguardar aprovação antes de gravar arquivos.
- **Feedback:** Brayan disse que posso ir gravando nos arquivos enquanto avançamos pelas seções.
- **Ajuste:** gravar cada seção em `Context/` logo após confirmar o resumo com Brayan, sem esperar o fim do onboarding. Continuar sinalizando lacunas com `[PENDENTE DE VALIDAÇÃO]` e avisando o que foi gravado.

### 2026-11-09 — Agente de marketing: formato do relatório
- **Contexto:** construção do DelhiAgente; propus um relatório semanal em texto.
- **Feedback:** Brayan quer o relatório dinâmico, com cards, dashboards, métricas e gráficos. Relatório em texto fica lento.
- **Ajuste:** entregas de análise em formato visual (painel), com texto curto só onde ajuda.

### 2026-11-09 — Agente de marketing: foco na Delhi
- **Contexto:** a seção de tendências do painel trazia dados de mercado genéricos.
- **Feedback:** Brayan prefere o foco no "para a Delhi", com tendências mais ligadas aos produtos da empresa.
- **Ajuste:** cada tendência começa por um produto Delhi e uma ação concreta; o dado de mercado vem como justificativa.

### 2026-11-12 — Painel: sem cards de "cuidado"
- **Contexto:** o painel trazia um card de alerta ("Cuidado: cúrcuma, ervas e linha Delhi Ayurveda").
- **Feedback:** Brayan não considera esses cards importantes e não quer cards que falem de cuidados por enquanto.
- **Ajuste:** o painel e o agente não criam mais cards de alerta. As regras de cuidado continuam valendo nas legendas, sem aparecer no painel.

### 2026-11-12 — Programação semanal: análise, não chute
- **Contexto:** a primeira programação semanal listava o que postar sem mostrar por que, e parte dela (dia, horário, bastidores) não tinha análise.
- **Feedback:** Brayan quer que cada post da programação siga a mesma lógica do radar (nota, confirmação de que vale postar, porquê do dia e do horário), com base em estratégias de marketing, e que o agente aprenda toda semana com a conferência, acertando ou errando. No card, só a nota (sem as barras dos critérios) e sem links de fontes. O agente deve ser o especialista, para o Brayan não precisar estudar marketing.
- **Ajuste:** processo 7 com nota ≥ 75, "Sem pauta forte", teste da semana e conferência semanal; `Context/estrategias-marketing.md` e `Projects/agente-marketing/aprendizados-programacao.md` criados.

### 2026-11-13 — Atributos do produto: certeza, rótulo e nada inventado
- **Contexto:** na arte do carrossel do Ghee, usei "No rótulo: 0% caseína", mas o rótulo não traz caseína (o Ghee é 0% caseína, com laudo).
- **Feedback:** Brayan achou estranho o "no rótulo". Quando houver certeza sobre a informação do produto, pode usar o atributo; quando não houver, usar só o que está no rótulo e não inventar nada.
- **Ajuste:** atributos confirmados (brand.md, rótulo, laudo ou confirmação do Brayan) entram direto, sem "no rótulo". Sem confirmação, só o que está no rótulo. Registrado também em `Projects/agente-marketing/aprendizados-radar.md` para o DelhiAgente.

### 2026-11-13 — Artes: texto com destaque
- **Contexto:** nas telas 1 e 3 do carrossel do Garam Massala (fotos escuras), coloquei o texto direto sobre a foto, em creme e dourado.
- **Feedback:** Brayan achou os textos muito parecidos com a imagem e sem destaque.
- **Ajuste:** em fotos escuras ou com cores parecidas, o texto vai num cartão claro (creme, cantos arredondados) com título grande em marrom ou cobre. Regra registrada em `Skills/delhiagente/processos/4-ideias-de-conteudo.md`.

### 2026-11-13 — Artes: estilo A aprovado
- **Contexto:** o cartão creme e o dourado nas telas do Garam Massala não agradaram.
- **Feedback:** entre duas opções testadas na capa, Brayan escolheu a A: título branco em letra grossa, tarja laranja e escurecido suave na foto.
- **Ajuste:** esse passa a ser o padrão das artes, sem cartão creme e sem dourado (registrado em `processos/4-ideias-de-conteudo.md`).

### 2026-11-13 — Artes: o padrão é o modelo do Ghee
- **Contexto:** depois do estilo A (título branco, tarja laranja) no carrossel do Garam Massala.
- **Feedback:** Brayan disse que o carrossel do Ghee é o melhor ("mais natural e moderno") e deve ser o padrão; o Garam, mesmo refeito, ficou +/-.
- **Ajuste:** padrão = modelo Ghee (texto direto sobre foto clara, palavra em cobre, traço laranja, título serifado marrom e cobre). O estilo A (título branco em letra de bastão e tarja laranja) fica como alternativa, só quando necessário ou pedido (ajuste do Brayan no mesmo dia). Os prompts passam a pedir fundo claro e espaço livre para o texto, porque as fotos escuras do Garam (prompt com "pedra escura") foram a causa do problema.

### 2026-11-13 — Grafia "Garam Massala" e anis-estrelado
- **Feedback:** Brayan confirmou que o nome do produto é **Garam Massala** (com dois "s", como Chai Massala). Também disse que o anis-estrelado pode aparecer nas fotos como enfeite, mesmo não estando no rótulo.
- **Ajuste:** usar "Garam Massala" em artes, legendas e pautas. Nas buscas do Google Trends, o termo continua "garam masala", que é como as pessoas pesquisam.

### 2026-11-13 — O OS aprende com cada decisão
- **Contexto:** os aprendizados ficavam presos em cada agente (radar, programação) e no registro de feedbacks, sem virar regra geral.
- **Feedback:** Brayan quer que o OS inteiro aprenda com cada decisão e feedback, de forma geral e não só no caso específico, porque o DelhiAgente reflete os feedbacks dele e isso deve refletir no OS.
- **Ajuste:** criado `Context/principios.md` (10 princípios iniciais tirados das decisões até aqui); regra 17 no CLAUDE.md e no AGENTS.md; o DelhiAgente sugere princípios no resumo de segunda. Princípio novo só entra com aprovação do Brayan (opção A).
