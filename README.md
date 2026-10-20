<p align="center">
  <img src="logo.png?v=angular" alt="Raven" width="420">
</p>

# Raven

Uma skill de entrevista crítica para questionar premissas, avaliar ideias ou trabalhos e aprofundar decisões, com sugestão de gerar um documento ao final. Serve para discutir uma história, uma decisão ou um problema técnico, conforme o que você trouxer.

Inspirada na entrevista em rodadas da `grilling` e na síntese documental da `to-spec`, a Raven é independente: nenhuma delas precisa estar instalada ou ser carregada.

## Instalação

Com o CLI Skills:

```sh
npx skills add nihilboy1/raven --skill raven
```

Selecione o agente e o escopo de instalação desejados no instalador.

Para instalar manualmente no Codex, copie `SKILL.md` e a pasta `agents/` deste repositório para `~/.codex/skills/raven/`. Se `CODEX_HOME` estiver definido, use sua pasta `skills/raven/`. Preserve eventuais personalizações de uma instalação anterior antes de substituí-la.

## Uso

No Codex:

```text
$raven Os usuários estão perdendo prazos. Quero entender a causa e discutir se notificações resolveriam.
```

Para discutir uma história:

```text
$raven Quero avaliar esta história: questione as motivações dos personagens e a coerência do desfecho comigo.
```

Também é possível pedir em linguagem natural:

```text
#raven Quero colocar esta ideia à prova e aprofundar minhas decisões.
```

`$raven` é a invocação de skill; `#raven` é um texto reconhecido pelas instruções da skill, não um comando especial do aplicativo.

## Como funciona

A Raven entende o que você trouxe e o que pretende alcançar, questiona premissas e explora fragilidades, consequências e alternativas. Não exige um problema previamente identificado nem cria modos específicos para cada área. Ao avaliar um trabalho, considera sua intenção e sustenta os apontamentos no material, distinguindo fatos, interpretações e preferências.

Antes de investigar, consulta as instruções e fontes pertinentes e respeita as regras do projeto. Reaproveita fatos verificados, decisões aprovadas e documentos existentes. Não pergunta por fatos que consegue verificar; quando não consegue, explica a limitação e seu impacto. Uma interpretação subjetiva não é tratada como erro objetivo.

As perguntas vêm em rodadas, organizadas por dependência: questões independentes podem aparecer juntas; as que dependem de respostas anteriores ficam para depois. A Raven espera suas respostas antes de avançar e adapta as próximas perguntas ao que mudou. Se houver muitas questões, prioriza as que mais esclarecem o restante.

Quando uma pergunta precisa de um fato do ambiente, a skill envia um subagente para verificá-lo, se disponível e permitido; caso contrário, investiga diretamente. Só as perguntas dependentes dessa investigação aguardam o resultado; as demais avançam na rodada. O agente confere as evidências recebidas antes de usá-las. Fatos cabem ao agente; decisões cabem a você.

Recomendações são opcionais e só aparecem quando há fundamento suficiente, com o motivo ou a principal consequência da escolha. Sem fundamento, a Raven não força uma recomendação: explicita a incerteza e pergunta quando isso ajuda a avançar, sem conduzir a uma conclusão predeterminada.

Ela não concorda automaticamente nem se opõe por princípio. Considera alternativas mais simples, inclusive manter como está, quando fizer sentido. Recomendações continuam sendo propostas até você aprová-las; detalhes rotineiros ficam com o agente dentro das autorizações existentes.

Se você pedir apenas uma síntese de decisões já discutidas, ela aproveita o contexto, sem reiniciar a entrevista. Decisões aprovadas só são reabertas diante de mudanças materiais no objetivo, nas restrições ou no escopo. Contradições e pendências ficam explícitas; se faltar contexto anterior, ela pede a referência necessária, sem inventar decisões.

**Emojis no chat:** 🐦‍⬛ apenas na primeira resposta a uma chamada explícita da skill pelo usuário, sem o nome da skill; não repetir nas continuações nem no fechamento. 🔎 pergunta; 💡 recomendação fundamentada; ✅ decisão alinhada; 📄 pergunta sobre gerar documento.

A entrevista acontece exclusivamente por texto no chat, sem ferramentas de perguntas, popups, formulários ou seletores interativos.

## Fechamento da conversa

Quando o objetivo da conversa estiver atendido e não houver decisões materiais abertas, a Raven resume o entendimento, os principais achados ou decisões e as limitações relevantes. Depois, pergunta separadamente, quando essas respostas ainda não tiverem sido dadas:

> Esse resumo corresponde ao que discutimos? Podemos fechar assim?
>
> Quer que eu gere um documento Markdown com esse entendimento ou prefere encerrar somente no chat?

Se você corrigir algo, ela retoma apenas os pontos afetados. Se responder a uma das perguntas, esclarece somente a outra. Confirmações e autorizações já dadas para o mesmo conteúdo e entrega são reaproveitadas.

Confirmar o entendimento não autoriza gravar um arquivo ou executar as sugestões. Pedir o documento autoriza sua gravação, mas não aprova o conteúdo: sem confirmação explícita ou com pendências materiais, ele fica como rascunho. Se dispensar o documento, a conversa termina no chat, sem criar arquivos. Se quiser o documento, basta responder, sem outra invocação da skill.

## Documento opcional

O documento acompanha o assunto e reúne somente o que for pertinente: contexto, achados ou decisões, fundamentos e pendências. Recomendações não aprovadas continuam identificadas como propostas. Não há um modelo técnico obrigatório.

Uma avaliação de história pode reunir observações sobre o texto e sugestões discutidas. Um plano técnico pode incluir responsabilidades, contratos, testes, critérios de aceite e etapas, distinguindo verificações propostas das executadas. A entrevista não vira um roteiro para preencher seções.

O documento segue o idioma da conversa e as convenções locais. Reutiliza o arquivo da mesma iniciativa e preserva o trabalho existente. Sem convenção definida, usa `docs/<nome-descritivo-em-ingles>.md` em kebab-case; planos de implementação ficam em `docs/plans/`.

Quando disponível e permitido, um subagente revisa o documento salvo contra a conversa e as fontes: fidelidade das decisões, fundamentos, pendências e links. O agente principal confere os achados antes de ajustar o arquivo; sem subagente, faz a revisão diretamente. A entrega inclui o link do documento, um resumo curto e eventuais bloqueios.

## Limites

A skill conduz a entrevista crítica ou a síntese de decisões e grava Markdown local quando solicitado ou autorizado. Executar sugestões, implementar, reescrever a obra, publicar, fazer commits ou escrever em banco depende de uma solicitação explícita posterior e das autorizações aplicáveis. Ela não concede permissões adicionais nem substitui as fontes de referência existentes.

O comportamento depende do agente e das ferramentas disponíveis. A skill não exige um servidor MCP específico nem as skills de origem.

## Manutenção

`SKILL.md` é a fonte das instruções da entrevista e da documentação opcional. `agents/openai.yaml` contém os metadados de apresentação no Codex. Alterações neste repositório não atualizam automaticamente cópias já instaladas; reinstale ou sincronize os arquivos após revisar as mudanças.

## Validação

O workflow `.github/workflows/validate-skill.yml` executa a validação em pushes, pull requests e acionamentos manuais no GitHub Actions. O validador fica em `scripts/quick_validate.py`, adaptado do `skill-creator` do Codex, sem depender da instalação local do aplicativo.

Para executar localmente, na pasta do repositório:

```sh
python -m venv .venv
```

No PowerShell:

```powershell
.\.venv\Scripts\python.exe -m pip install -r requirements-dev.txt
.\.venv\Scripts\python.exe -X utf8 scripts/quick_validate.py .
```

Em Linux ou macOS:

```sh
.venv/bin/python -m pip install -r requirements-dev.txt
.venv/bin/python -X utf8 scripts/quick_validate.py .
```

A validação verifica o frontmatter, as regras de nome e descrição e placeholders inacabados. Ela não avalia o comportamento da entrevista. A pasta `.venv/` é ignorada pelo Git.

## Créditos e licença

Adaptação por [nihilboy1](https://github.com/nihilboy1), baseada nos fluxos de [grilling](https://github.com/mattpocock/skills/tree/main/skills/productivity/grilling) e [to-spec](https://github.com/mattpocock/skills/tree/main/skills/engineering/to-spec), de Matt Pocock.

Distribuída sob a [licença MIT](LICENSE), preservando os créditos da origem.
