# Regras operacionais

## Estado e retomada

- Fase atual: **Fase 4**, a mesma fase em execução, agora com tarefas ajustadas para os refinamentos da plataforma.
- Objetivo: refinar, validar e concluir a plataforma atual. Fase 5 permanece planejada e só será liberada após aceite formal da Fase 4.
- Primeira task elegível: **REF-01 — Entender e corrigir a abertura da Fila**, UUID `3c9a7ea2-63fd-4aa5-a370-cdc04e796456`.
- Leia `STATUS.md`, `.adapta-cliente/estado-atual.md`, `04_fase-atual/fase.md`, `04_fase-atual/00-Tasks_Gerais.md` e a seção REF-01 da `04_fase-atual/specs/spec-4-004-refinamento-formulario-fila-visao.md` antes de agir.
- Quatro cards e a subtarefa suspensos são somente rastreabilidade: não executar, não pedir credenciais ou insumos e não contar como entregues. Não são pré-condição dos refinamentos.
- Fases encerradas, aceites e IDs existentes permanecem preservados. Não reiniciar fases nem reabrir tasks concluídas.
- Novo mapeamento somente depois do encerramento da Fase 5, em outro processo. Não discutir ou implementar novo escopo nas tasks atuais.

## Como conduzir a primeira task

Na retomada da conversa, após ler os arquivos atuais, explique em linguagem simples que a cliente continua na Fase 4 e que o próximo passo é investigar a Fila. Pergunte qual tela/link não abre e qual erro ela vê; depois colete os demais detalhes necessários da REF-01, sem solicitar senha. Diagnóstico primeiro; se faltar decisão necessária, pergunte na própria task. Sem resposta, não invente a regra nem implemente o trecho dependente dela. Não declarar corrigido sem reproduzir e provar.

Uma implementação por vez. Apresente o plano mínimo, execute somente o recorte autorizado, registre prova sanitizada e peça teste humano explícito antes de concluir e avançar. Esta publicação documental não inicia execução automática nem comprova atualização de uma sessão já aberta.

## Caminhos e segurança

- Caminho literal: `04_fase-atual/`; Jornada em `04_fase-atual/fase.md`, tabela completa em `04_fase-atual/00-Tasks_Gerais.md`, SPECs em `04_fase-atual/specs/`.
- Não normalize o nome do diretório. Confira a árvore da branch main antes de afirmar que falta arquivo.
- Use o contrato e o TDD da task; não publique, integre serviços ou altere dados externos sem autorização explícita aplicável.
- Perguntas de insumo acompanham a própria task, sem criar fase/etapa separada. A coleta pode começar, mas execução dependente de resposta não pode ser completada por suposição.
- Não alterar permissões para contornar erro nem usar dados reais em testes sem autorização.
