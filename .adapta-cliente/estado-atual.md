# Estado atual — refinamentos

## Direção vigente

Texto integral em `04_fase-atual/direcao-vigente.md` (confirmação do consultor em 27/10/2026 17:43). Resumo: concluir REF-01 a REF-12, depois os controles locais da fase 4, validação ponta a ponta e encerramento na fase 5; sem novo escopo, sem credenciais, sem integração externa; uma implementação por vez, insumos na própria task, prova técnica e teste humano explícito.

## Controle do orquestrador


- task_id: 547994b2-a335-4fd9-878a-52b67b6c0b60 (REF-05 — Criar pontuação de ocupação para priorizar o atendimento)
- champion: Karol e Márcio
- spec: 04_fase-atual/specs/spec-4-004-refinamento-formulario-fila-visao.md (seção REF-05)
- etapa: concluida
- insumos_recebidos: TODOS (1/3 escala e pesos; 2/3 faixas e desempate; 2b pesos por profissão com regra "profissão substitui ocupação"; 3/3 exibição) — literais em ref05-insumos.md
- insumos_pendentes: NENHUM
- autorizacao_implementacao: concedida — consultor, 06/11/2026 ("Autorizar implementação")
- teste_humano: aprovado — operador Ricardo, 06/11/2026 ("fiz o teste colocando precisa de ajuda e agora aparece"; print "teste 7" com badge "Alta · 9" na Fila; registro no banco: nota 9, faixa alta, matriz v1)
- verificacao_automatica: passou — QA Skip v0.0.95 (916b9ec) e v0.0.96 (e811f84) verdes; migrações 0060/0061/0062 applied; schema das 3 coleções conferido por API; 26/26 provas no bundle index-COT7Y_mK.js e 9/9 no index-CwBGX3zp.js; registro "teste 7" provado por leitura autenticada (nota 9, faixa alta, matriz v1, motivo "ocupacao: Diretor ou alta gerência")
- aprendizado: AP-2026-11-06-1710-prioridade-em-toda-colecao-que-a-tela-le.md (candidato)
- ultima_acao: fechamento documental da REF-05 (changelog, fase.md, STATUS, AP) — 06/11/2026
- proxima_acao: REF-06 (elegibilidade por perfil) — pré-condição REF-05 aceita, satisfeita; insumos a coletar na própria task, uma pergunta por vez; task nova adicional decidida pelo consultor (exibir triagens sem agendamento na Visão) aguarda análise e plano
- atualizado_em: 2026-11-06T18:15:00Z

## Estado por task

- REF-01 (Fila): ABERTA — erro não reproduzido; diagnóstico 29/10 inconclusivo por SPEC; se recorrer, coletar tela/link, papel, aparelho, passos e mensagem de erro, sem senha.
- REF-02, REF-03, REF-04 e REF-05: concluídas e aceitas (v0.0.92 `db03c5f`, v0.0.93 `9ba9ab8`, v0.0.94 `f569edc`, v0.0.95–98 `916b9ec`/`e811f84`/`19ba697`/`5f5c25f`) — histórico em `04_fase-atual/fase.md`, `STATUS.md`, `changelog.md` e APs correspondentes.
- Pendência humana acumulada: 3 submissões sintéticas + 1 agendamento de teste (limpeza a decidir); usuário de teste teste.r1@fellice-fitness.local (0061) a remover ao finalizar o projeto.
- Este arquivo foi enxutado em 06/11/2026: detalhes por task vivem em documentos dedicados; aqui fica só o bloco vivo de controle.

- fase_5: planejada, liberar somente pelo ritual após F4
