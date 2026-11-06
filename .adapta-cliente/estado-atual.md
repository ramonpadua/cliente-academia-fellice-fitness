# Estado atual — refinamentos

## Direção vigente

Texto integral em `04_fase-atual/direcao-vigente.md` (confirmação do consultor em 27/10/2026 17:43). Resumo: concluir REF-01 a REF-12, depois os controles locais da fase 4, validação ponta a ponta e encerramento na fase 5; sem novo escopo, sem credenciais, sem integração externa; uma implementação por vez, insumos na própria task, prova técnica e teste humano explícito.

## Controle do orquestrador


- task_id: 547994b2-a335-4fd9-878a-52b67b6c0b60 (REF-05 — Criar pontuação de ocupação para priorizar o atendimento)
- champion: Karol e Márcio
- spec: 04_fase-atual/specs/spec-4-004-refinamento-formulario-fila-visao.md (seção REF-05)
- etapa: aguardando_teste_humano
- insumos_recebidos: TODOS (1/3 escala e pesos; 2/3 faixas e desempate; 2b pesos por profissão com regra "profissão substitui ocupação"; 3/3 exibição) — literais em ref05-insumos.md
- insumos_pendentes: NENHUM
- autorizacao_implementacao: ausente
- teste_humano: pendente
- verificacao_automatica: passou — QA Skip v0.0.95 (commit 916b9ec) verde (setup, estática, build, integrações; suite inexistente, ran=false); migração 0060_ref05_prioridade applied; campos prioridade_nota/faixa/matriz/motivo confirmados por API em lead_submissions e lead_appointments; 26/26 provas no bundle do preview (index-COT7Y_mK.js): pesos literais da matriz v1, faixas (>=7 alta, <=5 baixa), sem_pontuacao, rótulos Alta/Média/Baixa, ordenação da Fila (alta=3), gravação e transporte da prioridade, FORM_VERSION v1.2.0; debug r1 v0.0.96 (e811f84) com 9/9 provas no bundle index-CwBGX3zp.js
- aprendizado: pendente
- ultima_acao: reteste r3 — triagem "teste 6" (Diretor) concluiu com sucesso no código novo; teste da Fila BLOQUEADO: operador sem conta champion/consultor (gate por design); opções apresentadas (conta champion do Márcio, usuário de teste temporário via migração — precedente 0038, removido após o teste, ou credencial do administrador do painel Skip); pedido de exibir triagens sem agendamento na Visão registrado como proposta de task futura (06/11/2026)
- proxima_acao: destravar o teste da Fila pela opção escolhida pelo consultor; fechamento documental somente após confirmação
- atualizado_em: 2026-11-06T14:55:00Z

## Estado por task

- REF-01 (Fila): ABERTA — erro não reproduzido; diagnóstico 29/10 inconclusivo por SPEC; se recorrer, coletar tela/link, papel, aparelho, passos e mensagem de erro, sem senha.
- REF-02, REF-03 e REF-04: concluídas e aceitas (v0.0.92 `db03c5f`, v0.0.93 `9ba9ab8`, v0.0.94 `f569edc`) — histórico em `04_fase-atual/fase.md`, `STATUS.md`, `changelog.md` e APs correspondentes.
- REF-05: análise e insumos em `04_fase-atual/ref05-insumos.md`.
- Pendência humana acumulada: 3 submissões sintéticas + 1 agendamento de teste (limpeza a decidir).
- Este arquivo foi enxutado em 06/11/2026: detalhes por task vivem em documentos dedicados; aqui fica só o bloco vivo de controle.

- fase_5: planejada, liberar somente pelo ritual após F4
