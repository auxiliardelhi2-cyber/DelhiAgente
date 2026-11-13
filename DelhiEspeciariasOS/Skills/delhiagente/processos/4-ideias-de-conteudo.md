# Regras de roteiro, prompts e legenda (usadas pelo radar diário)

**A Delhi produz o conteúdo principalmente com IA** (vídeos e fotos gerados), e não gravando receitas. Decisão do Brayan em 12/11/2026. Toda pauta deve ser pensada para ser feita **só com IA**, a partir de fotos reais dos produtos.

**Por enquanto, só imagens** (decisão do Brayan em 12/11/2026): use `formato_ia` "foto" ou "carrossel". Nada de vídeo até o Brayan liberar.

Valem para as pautas que recebem `hook`, `roteiro`, `prompts` e `legenda` no radar (no mínimo as 3 de maior nota). Cada uma tem:

- **Produto Delhi** (prioridade para a marca própria).
- **Formato de IA** (`formato_ia`): "vídeo" (Reels/TikTok), "foto" (post único) ou "carrossel" (várias imagens). Escolha o que rende mais para a pauta.
- **Público:** alterne entre 60+ (cliente atual, principalmente mulheres) e 20 a 50 anos (público a conquistar).
- **Hook:** a frase ou o texto na tela do 1º segundo (ou da capa do carrossel).
- **Roteiro:** a sequência de cenas, curta, com a duração total.
- **Prompts para IA:** uma lista de cenas, cada uma com prompt pronto para colar na ferramenta (ver abaixo).
- **Legenda pronta.**
- **Por que agora:** ligação com o sinal da pauta.

## Como escrever os prompts

A ferramenta de IA ainda não foi definida. Escreva prompts **genéricos**, que funcionem na maioria das ferramentas de imagem e vídeo.

Cada cena em `prompts` tem:

- `cena`: número e nome curto (ex.: "1. Abertura").
- `tipo`: "imagem" ou "vídeo".
- `duracao`: para vídeo, em segundos (cenas de 3 a 5 s); para imagem, vazio.
- `prompt`: em português, descrevendo assunto, ação, cenário, luz, enquadramento e estilo. Sempre inclua: **formato vertical 9:16** (ou 4:5 para foto e carrossel), **produto em destaque**, estilo da marca (tons de laranja `#FC7D44`, dourado e terrosos, luz natural, composição limpa e premium) e o que **não** deve aparecer.
- `referencia`: qual foto real usar como referência, por exemplo "foto real da embalagem do Ghee Delhi". Sempre que o produto aparecer, a cena deve partir da **foto real** (de imagem para vídeo ou de imagem para imagem).
- `texto_tela`: o texto que entra **depois, aplicado pelo Claude** (decisão do Brayan em 13/11/2026; não é mais feito no Canva). Não peça texto dentro do prompt, porque a IA erra letras.

## Texto na arte: aplicado pelo Claude

Decisão do Brayan em 13/11/2026: o texto das telas **não é mais colocado no Canva**. O fluxo é:

1. A equipe gera a imagem com o prompt (sem texto) e envia a imagem ao Claude numa conversa, dizendo qual post e qual tela é.
2. O Claude aplica o `texto_tela` (ou o `texto` da tela, na programação) e devolve o **PNG final**: 1080×1350 para feed e carrossel (4:5) e 1080×1920 para stories (9:16).
3. Antes de aplicar, o Claude confere se o texto bate com o produto (ver a regra de atributos abaixo) e avisa se algo não confere.

**Padrão visual das artes: "modelo Ghee"** (decisão do Brayan em 13/11/2026, a partir do carrossel do Ghee: "mais natural e moderno"):

- **Fotos com fundo claro e neutro** (bege, creme, linho, madeira clara), com **espaço livre** para o texto no topo ou na lateral. Todo prompt pede isso. Evite fundos escuros (pedra escura, preto): com eles o modelo não funciona bem.
- Texto **direto sobre a foto**, sem cartão e sem tarja. Se precisar, só um clareado suave atrás do texto.
- Linha de cima: palavra curta em **maiúsculas espaçadas, cor cobre** (Poppins Medium), por exemplo "O QUE É", "COMO USAR", "ONDE COMPRAR".
- Um **traço curto laranja `#FC7D44`** abaixo dela.
- Título em **letra serifada (Lora SemiBold)**: primeira parte em **marrom escuro**, parte de destaque em **cobre**.
- Se precisar, uma linha de apoio menor em Poppins, marrom.
- Nunca cobrir o produto; usar o espaço livre da foto.
- **Não usar:** cartão creme e letras douradas (testados no carrossel do Garam Massala e reprovados).
- **Alternativa (só quando necessário ou pedido):** título branco em letra de bastão (Poppins Bold) com tarja laranja `#FC7D44` e escurecido suave na foto, por exemplo em fotos escuras. O padrão continua sendo o modelo Ghee.

**Atributos do produto no texto** (orientação do Brayan em 13/11/2026): com certeza sobre a informação (brand.md, rótulo, laudo ou confirmação do Brayan), use o atributo direto, sem "no rótulo". Sem certeza, use só o que está no rótulo e não invente nada.

## Regras de fidelidade (obrigatórias)

- **O produto Delhi sempre aparece.** Toda peça (vídeo, foto ou carrossel) tem **pelo menos uma cena com a embalagem real** do produto, gerada a partir da foto de referência. De preferência na abertura ou no fechamento: no vídeo, a última cena; no carrossel, a capa ou a última tela. As outras cenas podem mostrar só o prato, a bebida ou o ingrediente. **Nunca** entregue uma peça com "sem produto em cena": sem a embalagem, o conteúdo vira propaganda genérica e não da Delhi.
- **O produto nunca é inventado.** Embalagem, rótulo, cor, textura e tamanho do produto vêm da foto real. Se a pauta pedir um produto sem foto disponível, avise no campo `nota`.
- **Nada de texto gerado pela IA** na imagem: rótulos, letreiros e legendas entram depois, aplicados pelo Claude.
- **Pessoas: só mãos, sem rostos.** Nada de pessoas comendo nem de rostos gerados. O produto é o protagonista.
- **Nada de resultado prometido:** nada de cenas de corpo, antes/depois, cura, emagrecimento ou "transformação".
- **Ingredientes e atributos** só se estiverem no rótulo ou no `brand.md`. Na dúvida, preencha `nota` com "Confira no rótulo…".
- **Rótulo de IA:** lembre no campo `nota` de marcar o post como conteúdo gerado por IA quando a rede pedir (Instagram e TikTok têm regras para isso; confira as atuais antes de publicar).

## Regras da legenda

- Tom do `Context/brand.md`: educativo, acolhedor e confiável, com toques casuais.
- Termine com: "Confira nossa lista completa de produtos acessando: www.delhiespeciarias.com.br / Ou pelo link na Bio."
- **Proibido:** preço, desconto, promoção, promessa de saúde, número de eficácia ("remove 99%"), religião, espiritualidade, política.
- Não descreva a cena como se fosse real ("veja como eu preparo"): a legenda fala do produto e do uso, não de quem gravou.

## Prioridade

A 1ª ideia ataca o maior problema da semana, por exemplo muitos dias sem post ou um canal em queda. Quando a conta estiver parada, prefira o formato mais rápido de gerar: **foto ou carrossel** antes de vídeo.
