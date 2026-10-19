# Fullplan

Uma skill para questionar a raiz de um problema, testar premissas e construir um caminho conforme as respostas, com fechamento confirmado pelo usuário e plano Markdown opcional.

O fluxo combina a entrevista em rodadas da `grilling` com a síntese documental da `to-spec`, em uma única skill independente. Nenhuma delas precisa estar instalada.

## Instalação

Com o CLI Skills:

```sh
npx skills add nihilboy1/fullplan --skill fullplan
```

Selecione o agente e o escopo de instalação desejados no instalador.

Para instalar manualmente no Codex, copie `SKILL.md` e a pasta `agents/` deste repositório para `~/.codex/skills/fullplan/`. Se `CODEX_HOME` estiver definido, use sua pasta `skills/fullplan/`. Preserve eventuais personalizações de uma instalação anterior antes de substituí-la.

## Uso

No Codex:

```text
$fullplan Quero planejar uma funcionalidade de notificações.
```

Também é possível pedir em linguagem natural:

```text
#fullplan Quero discutir esta ideia e gerar o plano em Markdown.
```

`$fullplan` é a invocação de skill; `#fullplan` é um texto reconhecido pelas instruções da skill, não um comando especial do aplicativo.

## Como funciona

1. Consulta as instruções do projeto e investiga os fatos relevantes.
2. Investiga causas, testa premissas, riscos e alternativas e adapta as perguntas e recomendações às respostas.
3. Usa subagentes para buscas independentes quando disponíveis e permitidos.
4. Quando considera o escopo definido, resume o entendimento e pergunta se está correto e podem fechar.
5. Pergunta separadamente se você quer salvar ou atualizar um `.md` ou encerrar somente no chat. Grava o plano apenas quando autorizado e apresenta o arquivo para revisão.

O objetivo é colocar a proposta à prova antes de fechar um caminho, considerando inclusive soluções mais simples ou não implementar. Confirmar o escopo não autoriza automaticamente gravar um arquivo ou iniciar a implementação. Você pode encerrar somente no chat; se quiser o documento, basta responder, sem outro comando. Se pedir o arquivo antes de resolver todas as decisões, recebe um rascunho com as pendências explícitas.

No chat, cada decisão aparece em um bloco próprio, com 💬 **Pergunta** e 💡 **Recomendação** separadas por uma linha em branco. Alternativas ficam em itens separados; ✅ identifica decisões alinhadas e 📌 destaca contexto ou pendências quando necessário. Esse padrão de comunicação não altera o modelo do plano salvo.

A entrevista acontece exclusivamente por texto no chat. A skill não usa ferramentas de perguntas do Codex ou de outras plataformas, nem abre popups, formulários ou seletores interativos para coletar respostas ou aprovações.

## Estrutura do plano

- Problema e solução.
- Histórias de uso.
- Decisões de implementação e de teste.
- Fora do escopo.
- Critérios de aceite.
- Etapas de implementação e dependências.
- Questões abertas e notas relevantes.

O plano segue o idioma da conversa e as convenções documentais do projeto. Na ausência delas, usa `docs/plans/<nome-descritivo-em-ingles>.md`.

## Limites

A skill conduz o planejamento crítico e grava Markdown local quando solicitado ou autorizado. Implementação, publicação, commits e escritas em banco dependem de uma etapa posterior e das autorizações do projeto. Ela não concede permissões adicionais nem substitui os SSOTs existentes.

O comportamento depende do agente e das ferramentas disponíveis. A skill não exige um servidor MCP específico nem as skills de origem.

## Manutenção

`SKILL.md` é a fonte das instruções e do modelo do plano. `agents/openai.yaml` contém os metadados de apresentação no Codex. Alterações neste repositório não atualizam automaticamente cópias já instaladas; reinstale ou sincronize os arquivos após revisar as mudanças.

## Créditos e licença

Adaptação por [nihilboy1](https://github.com/nihilboy1), baseada nos fluxos de [grilling](https://github.com/mattpocock/skills/tree/main/skills/productivity/grilling) e [to-spec](https://github.com/mattpocock/skills/tree/main/skills/engineering/to-spec), de Matt Pocock.

Distribuída sob a [licença MIT](LICENSE), preservando os créditos da origem.
