---
name: fullplan
description: "Conduza uma entrevista de planejamento em rodadas e transforme as decisoes alinhadas em um plano padronizado em Markdown local, antes da implementacao. Use quando o usuario pedir fullplan, #fullplan, $fullplan ou esse fluxo completo de planejamento."
---

# Fullplan

Skill pessoal que integra o fluxo de entrevista de `grilling` com a sintese documental de `to-spec`. E autonoma: nao carregue nem invoque essas duas skills. O padrao do documento esta definido aqui.

## Resultado e preparacao

Desde o inicio, trabalhe para entregar um plano `.md` concreto, revisavel e suficiente para orientar a implementacao. Avise brevemente que fara as perguntas necessarias e salvara o plano ao final, sem exigir um segundo comando. Use a lingua do usuario.

Leia as instrucoes do projeto e os SSOTs pertinentes antes de investigar. Respeite as regras de exploracao do repositorio, incluindo CodeGraph quando exigido. Reaproveite fatos verificados, decisoes aprovadas e planos existentes; nao reabra planejamento aprovado sem mudanca material de comportamento, arquitetura ou escopo.

Investigar fatos e responsabilidade do agente. Nao pergunte ao usuario algo que possa verificar no ambiente. Quando uma verificacao nao for possivel, explique a limitacao e seu impacto, sem apresentar suposicao como fato. O usuario decide escolhas materiais de produto, comportamento, arquitetura e escopo; detalhes rotineiros ficam com o agente dentro das autorizacoes existentes.

Quando houver buscas independentes de fatos e subagentes estiverem disponiveis e permitidos, delegue essas buscas com escopo delimitado. Enquanto investigam, avance com as perguntas cujos pre-requisitos ja estejam resolvidos; somente decisoes dependentes da investigacao aguardam os resultados. Confira as evidencias recebidas antes de incorpora-las ao plano. Sem delegacao disponivel ou permitida, investigue diretamente, mantendo a mesma ordem de dependencias.

## Entrevista em rodadas

Mapeie as decisoes como uma arvore: cada escolha pode desbloquear outras. A fronteira da rodada contem somente perguntas cujos pre-requisitos ja estao resolvidos. Agrupe as perguntas independentes dessa fronteira, apresente sua recomendacao para cada uma e espere as respostas antes de avancar. Perguntas dependentes de respostas ainda abertas ficam para a rodada seguinte. Mantenha cada rodada respondivel; se a fronteira for extensa, priorize as decisoes que mais desbloqueiam o restante.

Use este formato no canal de resposta final da rodada, ou a ferramenta de perguntas disponivel quando ela se adequar melhor:

```text
Q1 — Titulo da decisao
Pergunta objetiva, com contexto e alternativas quando ajudarem.
Recomendacao: escolha sugerida e motivo ou tradeoff principal.

Q2 — Titulo da proxima decisao independente
Pergunta e recomendacao.
```

Nao faca perguntas ao usuario em atualizacoes intermediarias de progresso. Durante investigacoes longas, comunique descobertas e proximos passos sem transformar atualizacoes em novas rodadas.

Ao longo das rodadas, cubra os pontos pertinentes ao documento final: problema, atores, resultado esperado, escopo e exclusoes, cenarios de uso e falha, contratos, fronteiras tecnicas, dependencias, criterios observaveis de aceite e estrategia de testes. Resolva as escolhas materiais sobre limites de teste na entrevista; nao abra outra entrevista na fase de sintese. Nao invente funcionalidades nem force decisoes irrelevantes para preencher secoes.

Distinga fatos verificados, decisoes do usuario, recomendacoes ainda nao aprovadas e pendencias. A cada resposta, atualize a arvore e questione os pontos ainda materiais. Encerre quando nao houver decisoes materiais abertas, sem prolongar a entrevista por detalhes rotineiros.

## Sintese e gravacao automatica

Ao terminar a entrevista, sintetize diretamente o contexto e as evidencias no modelo abaixo. Nao peca outro comando nem confirmacao para criar o rascunho: salve primeiro e apresente o artefato para aprovacao. Nao encerre apenas com um resumo no chat.

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

Releia o arquivo salvo contra a conversa: cobertura do escopo, fidelidade das decisoes, criterios testaveis, dependencias, pendencias explicitas, links corretos e ausencia de contradicoes com os SSOTs. Nenhuma secao pode converter uma recomendacao nao aprovada em decisao do usuario.

Entregue o link absoluto clicavel do `.md`, um resumo curto e eventuais bloqueios. Apresente o plano concreto para aprovacao antes de implementar, salvo se aquele mesmo plano ja estiver aprovado. Nao implemente, publique issues, faca commit/push ou execute escritas em banco como parte de `fullplan`. A implementacao posterior segue as autorizacoes do usuario e os gates do projeto.
