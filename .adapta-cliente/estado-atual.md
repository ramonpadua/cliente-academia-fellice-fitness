# Estado atual — refinamentos

## Direção vigente

Texto integral em `04_fase-atual/direcao-vigente.md` (confirmação do consultor em 27/10/2026 17:43). Resumo: concluir REF-01 a REF-12, depois os controles locais da fase 4, validação ponta a ponta e encerramento na fase 5; sem novo escopo, sem credenciais, sem integração externa; uma implementação por vez, insumos na própria task, prova técnica e teste humano explícito.

## Controle do orquestrador

- task_id: cbd0b8db-f55b-4f4c-93b8-c4bd9fd10e81 (REF-06 — Mostrar agendamento somente para quem atende às regras de perfil)
- champion: Karol e Márcio
- spec: 04_fase-atual/specs/spec-4-004-refinamento-formulario-fila-visao.md (seção REF-06)
- etapa: aguardando_autorizacao (análise concluída; nada implementado)
- insumos_recebidos: NENHUM ainda — ressalva da REF-04 ("o prêmio está disponível para todos, independente da triagem...") registrada como insumo antecipado
- insumos_pendentes: (1) matriz explícita de respostas que qualifica/desqualifica; (2) tratamento de informações ausentes; (3) exceções (ex.: ajuda humana, acesso direto sem triagem); (4) próximo passo de quem não se qualifica; (5) relação com o score da REF-05 (se houver, qual limiar — não presumir)
- autorizacao_implementacao: ausente — aguardar insumos e aprovação do plano
- teste_humano: pendente (roteiro após implementação)
- aprendizado: pendente
- ultima_acao: análise somente leitura da REF-06 (Agendar.tsx, lead_submissions, hooks) — 06/11/2026
- proxima_acao: coletar insumo 1/5 (matriz de perfil) na própria task, uma pergunta por vez; depois plano concreto e autorização
- atualizado_em: 2026-11-06T19:45:00Z

## Estado por task

- REF-01 (Fila): ABERTA — erro não reproduzido; diagnóstico 29/10 inconclusivo por SPEC; se recorrer, coletar tela/link, papel, aparelho, passos e mensagem de erro, sem senha.
- REF-02, REF-03, REF-04 e REF-05: concluídas e aceitas (v0.0.92 `db03c5f`, v0.0.93 `9ba9ab8`, v0.0.94 `f569edc`, v0.0.95–98 `916b9ec`/`e811f84`/`19ba697`/`5f5c25f`) — histórico em `04_fase-atual/fase.md`, `STATUS.md`, `changelog.md` e APs correspondentes.
- Task nova decidida pelo consultor em 06/11 (exibir triagens sem agendamento na Visão): na fila, análise e plano a preparar após os refinamentos ou por ordem do consultor; não abre automaticamente.
- Pendência humana acumulada: 3 submissões sintéticas + 1 agendamento de teste (limpeza a decidir); usuário de teste teste.r1@fellice-fitness.local (0061) a remover ao finalizar o projeto.
- Este arquivo foi enxutado em 06/11/2026: detalhes por task vivem em documentos dedicados; aqui fica só o bloco vivo de controle.

- fase_5: planejada, liberar somente pelo ritual após F4
