---
name: fullplan
description: "Questione a raiz de um problema, teste premissas e construa um caminho em rodadas de planejamento critico, com fechamento confirmado pelo usuario e plano Markdown opcional. Use quando o usuario pedir fullplan, #fullplan, $fullplan ou esse fluxo completo de planejamento."
---

# Fullplan

Skill pessoal que integra o fluxo de entrevista de `grilling` com a sintese documental de `to-spec`. E autonoma: nao carregue nem invoque essas duas skills. O padrao do documento esta definido aqui.

## Resultado e preparacao

Desde o inicio, trabalhe para compreender a raiz do problema e construir um caminho fundamentado nas respostas do usuario e nas evidencias. Avise brevemente que questionara as premissas, alinhara o escopo e, ao final, confirmara o entendimento e perguntara se o usuario quer um plano `.md`. Use a lingua do usuario.

Leia as instrucoes do projeto e os SSOTs pertinentes antes de investigar. Respeite as regras de exploracao do repositorio, incluindo CodeGraph quando exigido. Reaproveite fatos verificados, decisoes aprovadas e planos existentes; nao reabra planejamento aprovado sem mudanca material de comportamento, arquitetura ou escopo.

Investigar fatos e responsabilidade do agente. Nao pergunte ao usuario algo que possa verificar no ambiente. Quando uma verificacao nao for possivel, explique a limitacao e seu impacto, sem apresentar suposicao como fato. O usuario decide escolhas materiais de produto, comportamento, arquitetura e escopo; detalhes rotineiros ficam com o agente dentro das autorizacoes existentes.

Quando houver buscas independentes de fatos e subagentes estiverem disponiveis e permitidos, delegue essas buscas com escopo delimitado. Enquanto investigam, avance com as perguntas cujos pre-requisitos ja estejam resolvidos; somente decisoes dependentes da investigacao aguardam os resultados. Confira as evidencias recebidas antes de incorpora-las ao plano. Sem delegacao disponivel ou permitida, investigue diretamente, mantendo a mesma ordem de dependencias.

## Planejamento critico e entrevista em rodadas

Trate a conversa como um teste critico da situacao proposta (stress thinking), nao apenas como coleta de requisitos para executar a primeira solucao sugerida. Separe sintomas, causas hipoteticas e evidencias; investigue quem enfrenta o problema, em quais situacoes, com qual impacto e qual resultado indicaria melhora. Nao apresente uma causa como comprovada sem evidencia nem use uma sequencia mecanica de perguntas de "por que".

Coloque premissas e solucoes a prova com perguntas proporcionais ao caso: onde podem falhar, quais restricoes e dependencias importam, quais consequencias indesejadas podem surgir e quais alternativas mais simples existem, inclusive nao implementar quando fizer sentido. Explique fragilidades e tradeoffs com respeito, sem concordancia automatica nem oposicao por principio. Nao invente riscos ou force perguntas irrelevantes para cumprir uma lista.

Adapte o caminho a cada resposta. Se a causa, o objetivo ou uma restricao mudar, revise a recomendacao e as perguntas seguintes, explicitando o que mudou. Nao conduza o usuario a uma solucao predeterminada. Reaproveite decisoes validas e reabra apenas as que forem afetadas por novas evidencias ou mudancas materiais.

Mapeie as decisoes como uma arvore: cada escolha pode desbloquear outras. A fronteira da rodada contem somente perguntas cujos pre-requisitos ja estao resolvidos. Agrupe as perguntas independentes dessa fronteira, apresente sua recomendacao para cada uma e espere as respostas antes de avancar. Perguntas dependentes de respostas ainda abertas ficam para a rodada seguinte. Mantenha cada rodada respondivel; se a fronteira for extensa, priorize as decisoes que mais desbloqueiam o restante.

### Padrao de escrita no chat

Separe contexto, perguntas e recomendacoes em blocos curtos. Use emojis simples com significado estavel e sempre acompanhados de um rotulo escrito: 💬 Pergunta, 💡 Recomendacao, ✅ Decisao alinhada e 📌 Contexto ou pendencia. Use somente os blocos pertinentes; nao repita o resumo completo a cada rodada.

Deixe uma linha em branco entre blocos, entre itens de listas e entre decisoes. Coloque cada alternativa em um item proprio, com identificador curto para facilitar respostas como `Q1: A; Q2: B`. Evite paragrafos que misturem varias perguntas, alternativas e justificativas. Use negrito nos titulos e rotulos, sem transformar paragrafos inteiros em destaque. Reserve os emojis aos rotulos dos blocos, sem decoracao adicional.

Em cada decisao, apresente a pergunta primeiro, as alternativas quando forem uteis e a recomendacao em um paragrafo separado, com o motivo ou tradeoff principal. Uma recomendacao continua sendo uma proposta ate o usuario aprova-la; use ✅ somente para decisoes efetivamente alinhadas. Nao force alternativas em perguntas abertas nem acrescente blocos vazios para completar o formato.

Conduza toda a entrevista exclusivamente por texto no chat. Nao use ferramentas de perguntas ou coleta de respostas do Codex nem de qualquer outra plataforma, incluindo `request_user_input`, `request_user_input_async` e equivalentes. Nao abra popups, formularios, enquetes ou seletores interativos para obter escolhas ou aprovacoes. Apresente as perguntas em texto, encerre a rodada e aguarde a resposta escrita do usuario no chat.

Use este formato no canal de resposta final da rodada:

```text
**Q1 — Titulo da decisao**

💬 **Pergunta:** pergunta objetiva sobre uma unica decisao.

- **A.** Primeira alternativa.

- **B.** Segunda alternativa.

💡 **Recomendacao:** alternativa A, pelo motivo ou tradeoff principal.

**Q2 — Titulo da proxima decisao independente**

💬 **Pergunta:** proxima pergunta objetiva.

💡 **Recomendacao:** escolha sugerida e motivo ou tradeoff principal.
```

Esse padrao vale para as mensagens no chat, incluindo atualizacoes e entrega quando houver blocos distintos a separar. O plano salvo segue o modelo documental abaixo e as convencoes do projeto, sem importar automaticamente os emojis ou o formato da entrevista.

Nao faca perguntas ao usuario em atualizacoes intermediarias de progresso. Durante investigacoes longas, comunique descobertas e proximos passos sem transformar atualizacoes em novas rodadas.

Ao longo das rodadas, cubra os pontos pertinentes ao documento final: problema, atores, resultado esperado, escopo e exclusoes, cenarios de uso e falha, contratos, fronteiras tecnicas, dependencias, criterios observaveis de aceite e estrategia de testes. Resolva as escolhas materiais sobre limites de teste na entrevista; nao abra outra entrevista na fase de sintese. Nao invente funcionalidades nem force decisoes irrelevantes para preencher secoes.

Distinga fatos verificados, decisoes do usuario, recomendacoes ainda nao aprovadas e pendencias. A cada resposta, atualize a arvore e questione os pontos ainda materiais. Quando problema, resultado esperado, caminho, limites e criterios de sucesso estiverem suficientemente definidos e nao houver decisoes materiais abertas, proponha o fechamento abaixo, sem prolongar a entrevista por detalhes rotineiros.

## Confirmacao de fechamento e documentacao opcional

Antes de considerar o escopo fechado, apresente um resumo curto do entendimento: problema e causa sustentada ou hipotese ainda incerta, resultado esperado, caminho proposto, escopo e exclusoes, decisoes principais e riscos ou pendencias relevantes. Nao rotule o conjunto como aprovado antes da confirmacao do usuario.

Em seguida, faca duas perguntas separadas em texto no chat: se o resumo corresponde ao que o usuario quer e podem fechar o escopo assim; e se deseja salvar ou atualizar esse entendimento em um arquivo `.md` ou encerrar somente no chat. Aguarde a resposta. Confirmar o fechamento nao implica autorizar a gravacao, e pedir o arquivo nao implica aprovar o escopo. Se apenas uma resposta vier, pergunte somente o que falta, aproveitando autorizacoes explicitas ja dadas para a mesma entrega.

Se houver correcoes ou novas escolhas materiais, retome apenas os pontos afetados e apresente o resumo revisado antes de fechar. Se o usuario confirmar o fechamento e dispensar o arquivo, conclua no chat sem criar ou alterar um plano. Se autorizar o `.md`, sintetize o conteudo no modelo abaixo e salve-o; nao exija outro comando de invocacao da skill.

Se o usuario pedir o plano antes de resolver todas as decisoes, salve um rascunho com as pendencias explicitas. Nao apresente esse rascunho como aprovado ou pronto para implementar. Respeite pedidos de pausa ou de analise sem gravacao.

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

Testes devem detectar falhas reais de comportamento ou contrato, respeitando os gates e autorizacoes do projeto. Reutilize evidencia valida com entradas relevantes inalteradas. O plano propoe verificacoes; nao afirme que foram executadas nem conceda autorizacoes por escrito. Referencie procedimentos e gates existentes sem duplica-los.

Ao escolher os pontos de teste, prefira os limites e a infraestrutura ja existentes. Use o nivel mais alto que consiga verificar o comportamento com confiabilidade, preservando testes de contratos especificos quando necessarios para detectar falhas que esse nivel nao cobre. Evite criar novos pontos de teste espalhados sem necessidade; se um novo limite for indispensavel, proponha-o no nivel mais alto adequado e alinhe a decisao durante a entrevista.

Use o status de aprovado somente quando houver aprovacao explicita correspondente ao conteudo. Mudancas materiais posteriores precisam de novo alinhamento.

## Revisao e entrega

Quando houver arquivo autorizado, releia o plano salvo contra a conversa: cobertura do escopo, fidelidade das decisoes, criterios testaveis, dependencias, pendencias explicitas, links corretos e ausencia de contradicoes com os SSOTs. Nenhuma secao pode converter uma recomendacao nao aprovada em decisao do usuario.

Se salvou o `.md`, entregue seu link absoluto clicavel, um resumo curto e eventuais bloqueios. Se o usuario dispensou o arquivo, confirme o fechamento somente no chat. A aprovacao do escopo nao autoriza implementacao. Apresente o plano concreto para aprovacao antes de implementar, salvo se aquele mesmo plano ja estiver aprovado. Nao implemente, publique issues, faca commit/push ou execute escritas em banco como parte de `fullplan`. A implementacao posterior segue as autorizacoes do usuario e os gates do projeto.
