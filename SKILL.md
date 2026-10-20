---
name: raven
description: "Planeje criticamente em rodadas ou sintetize decisoes ja discutidas em um plano Markdown, preservando aprovacoes e pendencias. Use quando o usuario pedir raven, #raven, $raven, planejamento critico ou documentacao de decisoes existentes."
---

# Raven

Skill pessoal que integra o fluxo de entrevista de `grilling` com a sintese documental de `to-spec`. E autonoma: nao carregue nem invoque essas duas skills. O padrao do documento esta definido aqui.

## Resultado e preparacao

Na primeira resposta de cada execucao, abra com 🐦‍⬛ **Raven** e indique brevemente o caminho adequado ao pedido; nao repita a apresentacao ao continuar a conversa. Use a lingua do usuario.

Leia as instrucoes do projeto e os SSOTs pertinentes antes de investigar. Respeite as regras de exploracao do repositorio, incluindo CodeGraph quando exigido. Reaproveite fatos verificados, decisoes aprovadas e planos existentes; nao reabra planejamento aprovado sem mudanca material de comportamento, arquitetura ou escopo.

Distinga fatos verificados, decisoes aprovadas, recomendacoes e pendencias. Nao invente definicoes ou funcionalidades para preencher o documento; registre o que nao foi definido.

Investigar fatos e responsabilidade do agente. Nao pergunte ao usuario algo que possa verificar no ambiente. Quando uma verificacao nao for possivel, explique a limitacao e seu impacto, sem apresentar suposicao como fato. O usuario decide escolhas materiais de produto, comportamento, arquitetura e escopo; detalhes rotineiros ficam com o agente dentro das autorizacoes existentes.

Quando houver buscas independentes de fatos e subagentes estiverem disponiveis e permitidos, delegue essas buscas com escopo delimitado. No planejamento, enquanto investigam, avance com as perguntas cujos pre-requisitos ja estejam resolvidos; somente decisoes dependentes da investigacao aguardam os resultados. Confira as evidencias recebidas antes de incorpora-las ao plano. Sem delegacao disponivel ou permitida, investigue diretamente, mantendo a mesma ordem de dependencias.

## Modos por intencao

Selecione naturalmente pelo pedido e pelo contexto, sem novos comandos ou uma pergunta obrigatoria sobre o modo:

- **Planejamento:** quando houver um problema ou caminho a definir, siga a entrevista critica em rodadas abaixo, ate a confirmacao explicita do escopo.
- **Sintese:** quando o pedido for apenas documentar decisoes ja discutidas, organize o contexto e o plano existente no modelo documental, sem reiniciar a entrevista ou reabrir decisoes aprovadas.

Se o contexto disponivel for insuficiente para identificar as decisoes anteriores, informe a limitacao e solicite somente a referencia necessaria. Nao reconstrua decisoes ausentes por inferencia.

Na sintese, confira contradicoes, pendencias materiais e compatibilidade com os SSOTs. Nao resolva conflitos por conta propria; pergunte somente sobre o ponto material que precisar de esclarecimento. Siga as regras de fechamento e gravacao abaixo.

## Planejamento critico e entrevista em rodadas

Trate a conversa como um teste critico da situacao proposta (stress thinking), nao apenas como coleta de requisitos para executar a primeira solucao sugerida. Separe sintomas, causas hipoteticas e evidencias; investigue quem enfrenta o problema, em quais situacoes, com qual impacto e qual resultado indicaria melhora. Nao apresente uma causa como comprovada sem evidencia nem use uma sequencia mecanica de perguntas de "por que".

Coloque premissas e solucoes a prova com perguntas proporcionais ao caso: onde podem falhar, quais restricoes e dependencias importam, quais consequencias indesejadas podem surgir e quais alternativas mais simples existem, inclusive nao implementar quando fizer sentido. Explique fragilidades e tradeoffs com respeito, sem concordancia automatica nem oposicao por principio. Nao invente riscos ou force perguntas irrelevantes para cumprir uma lista.

Atualize a arvore de decisoes a cada resposta. Se a causa, o objetivo ou uma restricao mudar, revise o caminho, a recomendacao e as perguntas afetadas, explicitando o que mudou. Nao conduza o usuario a uma solucao predeterminada.

Mapeie as decisoes como uma arvore: cada escolha pode desbloquear outras. A fronteira da rodada contem somente perguntas cujos pre-requisitos ja estao resolvidos. Agrupe as perguntas independentes dessa fronteira e espere as respostas antes de avancar. Perguntas dependentes de respostas ainda abertas ficam para a rodada seguinte. Mantenha cada rodada respondivel; se a fronteira for extensa, priorize as decisoes que mais desbloqueiam o restante.

Recomende sempre que as informacoes e evidencias disponiveis sustentarem uma escolha, explicando o motivo ou tradeoff principal. Sem fundamento suficiente, explicite a incerteza e formule a pergunta necessaria para reduzi-la, sem induzir uma alternativa prematura. Recomendacoes sao propostas ate o usuario aprova-las.

### Padrao de escrita no chat

Use blocos curtos e separados por decisao, com 🔎 **Pergunta** e, quando fundamentada, 💡 **Recomendacao**. Alternativas sao opcionais; quando uteis, liste-as com identificadores curtos. Reserve ✅ para decisoes alinhadas; 📄 **Contexto** e 🟪 **Pendencia** sao opcionais. Nao repita resumos nem crie blocos vazios para cumprir formato. O documento segue o modelo abaixo, sem importar a formatacao do chat.

Faca perguntas e colete aprovacoes exclusivamente por texto no chat, nunca com `request_user_input`, `request_user_input_async`, equivalentes ou formularios. Apresente a rodada na resposta final e aguarde a resposta escrita do usuario. Atualizacoes intermediarias comunicam descobertas e proximos passos, sem perguntas.

Nas rodadas, resolva os pontos materiais do modelo documental, incluindo cenarios de uso e falha, contratos, fronteiras tecnicas, dependencias e limites de teste. Nao force decisoes irrelevantes nem adie escolhas materiais para a sintese.

Quando problema, resultado esperado, caminho, limites e criterios de sucesso estiverem definidos e nao houver decisoes materiais abertas, proponha o fechamento, sem prolongar a entrevista por detalhes rotineiros.

## Confirmacao de fechamento e documentacao opcional

Quando ainda faltar confirmacao do escopo, apresente um resumo curto: problema e causa sustentada ou hipotese incerta, resultado esperado, caminho, escopo e exclusoes, decisoes principais e riscos ou pendencias.

Confirmacao do escopo e autorizacao de arquivo sao independentes: fechar o escopo nao autoriza gravar, e pedir o arquivo nao aprova o escopo. Para cada uma ainda ausente, pergunte separadamente se podem fechar o resumo e se deseja salvar ou atualizar um `.md` ou encerrar no chat. Aguarde a resposta; se apenas uma vier, esclareca somente a outra. Aproveite confirmacoes explicitas e autorizacoes ja dadas para o mesmo conteudo e entrega, inclusive na sintese; nao exija nova confirmacao sem mudanca material.

Se houver correcoes ou novas escolhas materiais, retome apenas os pontos afetados e apresente o resumo revisado antes de fechar. Se o usuario confirmar o fechamento e dispensar o arquivo, conclua no chat sem criar ou alterar um plano. Se autorizar o `.md`, sintetize o conteudo no modelo abaixo e salve-o; nao exija outro comando de invocacao da skill.

Um pedido de arquivo ja autoriza sua gravacao. Com contradicoes ou pendencias materiais, ou sem confirmacao explicita do escopo, salve como rascunho com as pendencias explicitas. Use o status Aprovado somente com confirmacao explicita correspondente ao conteudo. Respeite pedidos de pausa ou de analise sem gravacao.

Antes de editar, confira o estado do repositorio e o arquivo existente com seu diff, conforme as instrucoes locais. Preserve trabalho alheio. Reutilize o plano da mesma iniciativa; nao crie uma especificacao paralela. Siga as convencoes do projeto para destino, nomes, catalogacao, prioridade e ciclo de vida. Sem convencao definida, use `docs/plans/<nome-descritivo-em-ingles>.md` em kebab-case. Traduza os titulos do modelo para a lingua do usuario, mantendo as responsabilidades das secoes.

## Modelo do plano

```markdown
# Titulo do plano

Status: Rascunho para revisao | Aprovado

## Problema
Problema concreto pela perspectiva de quem o enfrenta e contexto verificado.

## Solucao
Resultado esperado pela perspectiva do usuario ou operador.

## Historias de uso
Lista numerada dos atores e cenarios acordados, no formato:
Como [ator], quero [capacidade], para [beneficio].
Em trabalho tecnico, descreva o resultado para o operador ou desenvolvedor.

## Decisoes de implementacao
Decisoes alinhadas sobre modulos, responsabilidades, interfaces, contratos,
estados, dados, arquitetura e interacoes que forem pertinentes.

## Decisoes de teste
Comportamentos e contratos a verificar, limites de teste acordados,
precedentes existentes e cenarios relevantes de sucesso e falha.

## Fora do escopo
Exclusoes explicitas que delimitam a entrega.

## Criterios de aceite
Resultados observaveis e verificaveis que determinam a conclusao.

## Plano de implementacao
Etapas ordenadas do trabalho aberto, dependencias, atualizacoes documentais
e verificacoes pertinentes. Distinguir implementacao, validacao e publicacao.

## Questoes abertas
Decisoes pendentes, bloqueios e investigacoes condicionais, ou indicar
explicitamente que nao ha pendencias materiais.

## Notas adicionais
Contexto relevante que nao pertence as secoes anteriores; omitir se vazio.
```

Dimensione as historias e etapas ao escopo, sem listas extensas artificiais. Prefira fronteiras e contratos a inventarios especulativos de arquivos. Inclua links a fontes canonicas e caminhos verificados quando ajudarem a executar. Use trechos de codigo somente quando expressarem uma decisao com mais precisao que prosa, por exemplo uma maquina de estados validada em prototipo.

Planeje testes que detectem falhas reais de comportamento ou contrato, priorizando limites, infraestrutura e gates existentes. Use o nivel mais alto confiavel e preserve testes de contratos que cubram lacunas; alinhe novos limites indispensaveis no planejamento. Na sintese, registre como pendencias as decisoes de teste pertinentes ainda ausentes. Reutilize evidencia valida com entradas inalteradas e distinga verificacoes propostas das executadas, sem conceder autorizacoes pelo documento.

## Revisao e entrega

Quando houver arquivo autorizado, releia o plano salvo contra a conversa: cobertura do escopo, fidelidade das decisoes, criterios testaveis, dependencias, pendencias explicitas, links corretos e ausencia de contradicoes com os SSOTs. Nenhuma secao pode converter uma recomendacao nao aprovada em decisao do usuario.

Se salvou o `.md`, entregue seu link absoluto clicavel, um resumo curto e eventuais bloqueios. Sem arquivo, entregue a sintese ou confirme o fechamento no chat, conforme o pedido. A aprovacao do escopo nao autoriza implementacao. Nao implemente, publique issues, faca commit/push ou execute escritas em banco como parte de `raven`. A implementacao posterior segue as autorizacoes do usuario e os gates do projeto.
