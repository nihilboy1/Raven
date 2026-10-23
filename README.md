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

Toda pergunta recebe um código estável: `Q1`, `Q2`, `Q3`… Desdobramentos usam `Q1.1`, `Q1.2` e outros níveis quando necessário. A numeração continua entre rodadas da mesma entrevista, inclusive nas confirmações durante a entrevista; códigos não são reiniciados, renumerados ou reutilizados. O fechamento e seus esclarecimentos não recebem código `Q` nem consomem a numeração. Se a entrevista for retomada, ela continua do próximo código disponível. Você pode responder ou retomar um ponto pelo código. A hierarquia representa desdobramentos; dependências entre ramos são acompanhadas separadamente.

Durante a execução, a Raven acompanha no contexto da conversa as respostas, ideias, fundamentos, decisões e pendências de cada questão. Preserva ideias propostas, adiadas ou descartadas e os motivos conhecidos. Ausência de resposta não significa aprovação. Se uma decisão mudar, mantém a referência ao que foi substituído e por quê, sem reabrir os demais pontos. No chat, mostra somente mudanças e referências úteis, sem repetir todo o registro.

Esse acompanhamento não gera Markdown ou outros arquivos automaticamente e não garante memória entre chats. A Raven reaproveita registros existentes fornecidos ou acessíveis; se faltar contexto, explicita a lacuna e pede a referência necessária, sem reconstruir decisões por inferência. O documento de fechamento continua opcional.

Quando uma pergunta precisa de um fato do ambiente, a skill envia um subagente para verificá-lo, se disponível e permitido; caso contrário, investiga diretamente. Só as perguntas dependentes dessa investigação aguardam o resultado; as demais avançam na rodada. O agente confere as evidências recebidas antes de usá-las. Fatos cabem ao agente; decisões cabem a você.

Antes de consolidar premissas ou escolhas relevantes, também usa subagentes para contrapontos independentes quando a incerteza, o impacto ou as alternativas justificam essa análise, se disponíveis e permitidos. Eles podem buscar evidências contrárias, testar condições de falha ou avaliar uma alternativa mais simples. Recebem os códigos das questões, o contexto, as fontes e as restrições, distinguindo propostas de decisões aprovadas. Não precisam fabricar oposição: podem concluir que a ideia se sustenta.

A Raven confere os fundamentos e as incertezas antes de incorporar os achados e apresenta somente divergências úteis, ligadas às questões correspondentes. Contrapontos só reabrem decisões aprovadas diante de evidência ou mudança material. Sem delegação disponível ou permitida, explica a limitação e faz a análise diretamente. Subagentes não recebem autorização adicional para executar sugestões.

Recomendações são opcionais e só aparecem quando há fundamento suficiente, com o motivo ou a principal consequência da escolha. Sem fundamento, a Raven não força uma recomendação: explicita a incerteza e pergunta quando isso ajuda a avançar, sem conduzir a uma conclusão predeterminada.

Ela não concorda automaticamente nem se opõe por princípio. Considera alternativas mais simples, inclusive manter como está, quando fizer sentido. Recomendações continuam sendo propostas até você aprová-las; detalhes rotineiros ficam com o agente dentro das autorizações existentes.

Se você pedir apenas uma síntese de decisões já discutidas, ela aproveita o contexto, sem reiniciar a entrevista. Decisões aprovadas só são reabertas diante de mudanças materiais no objetivo, nas restrições ou no escopo. Contradições e pendências ficam explícitas; se faltar contexto anterior, ela pede a referência necessária, sem inventar decisões.

**Emojis no chat:** 🐦‍⬛ apenas na primeira resposta a uma chamada explícita da skill pelo usuário, sem o nome da skill; não repetir nas continuações nem no fechamento. 🔎 pergunta; 💡 recomendação fundamentada; ✅ decisão alinhada; 📄 pergunta sobre gerar documento; 1️⃣ 2️⃣ 3️⃣ opções de fechamento.

A entrevista acontece exclusivamente por texto no chat, sem ferramentas de perguntas, popups, formulários ou seletores interativos.

## Fechamento da conversa

Quando o objetivo da conversa estiver atendido e não houver decisões materiais abertas, a Raven resume o entendimento, os principais achados ou decisões e as limitações relevantes. Depois, apresenta uma única pergunta de fechamento sem código `Q`, com três opções:

> 1️⃣ Concordo com o entendimento e quero encerrar no chat.
>
> 2️⃣ Concordo com o entendimento e quero que escreva o plano em `.md` agora.
>
> 3️⃣ Quero mais uma rodada de questionamento crítico sobre o assunto.

Você pode responder apenas `1`, `2` ou `3`, ou indicar sua escolha por escrito. A opção 1 aprova o entendimento e encerra sem criar arquivos. A opção 2 aprova o entendimento e autoriza escrever ou atualizar o plano em Markdown imediatamente, sem nova confirmação ou invocação da skill. A opção 3 abre outra rodada crítica, preservando os códigos das questões e as decisões já aprovadas; ao propor novamente o fechamento, a Raven apresenta o resumo atualizado e as mesmas três opções.

Se você corrigir algo, ela retoma apenas os pontos afetados. Respostas ambíguas são esclarecidas somente no que falta. Confirmações e autorizações já dadas para o mesmo conteúdo e entrega são reaproveitadas, sem repetir uma escolha já feita.

Fora da escolha explícita da opção 2, confirmar o entendimento por si só não autoriza gravar um arquivo. Pedir um documento autoriza sua gravação, mas não aprova automaticamente o conteúdo: sem confirmação explícita ou com pendências materiais, ele fica como rascunho. Nenhuma opção autoriza executar o plano ou as sugestões.

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
