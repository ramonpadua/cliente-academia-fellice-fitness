# Estado atual — refinamentos

## Direção vigente

Texto integral em `04_fase-atual/direcao-vigente.md` (confirmação do consultor em 27/ 10/2026 17:43). Resumo: concluir REF-01 a REF-12, depois os controles locais da fase 4, validação ponta a ponta e encerramento na fase 5; sem novo escopo, sem credenciais, sem integração externa; uma implementação por vez, insumos na própria task, prova técnica e teste humano explícito.

## Controle do orquestrador

- task_id: 547994b2-a335-4fd9-878a-52b67b6c0b60 (REF-05 — Criar pontuação de ocupação para priorizar o atendimento)
- champion: Karol e Márcio
- spec: 04_fase-atual/specs/spec-4-004-refinamento-formulario-fila-visao.md (seção REF-05)
- etapa: coletando_insumos
- insumos_recebidos: (1/3) escala e pesos — 06/11/16, respostas literais do formulário da task: escala 0–10; CLT 5; Autônomo 6; Empresário 7; Diretor ou alta gerência 9; Estudante 7; Aposentado 7; Prefiro não informar 5; (2/3) faixas e desempate — 06/11/2026, respostas literais: Alta = nota ≥ 7; Baixa = nota ≤ 5 (entre eles, Média); desempate = ordem de chegada (mais antigo primeiro); resposta ausente/inválida = nota 0, cai em Baixa e exibe "Sem pontuação"
- insumos_pendentes: (2b) pesos por profissão da sub-pergunta (CLT e Autônomo) — observação literal do consultor: "as sub perguntas da triagem, dos itens clt, autonomo e o que mais tiver, precisa ter peso também"; (3) onde a equipe vê a prioridade (Fila, Visão ou ambos) e se a Fila reordena or só exibe
or só exibe
- autorizacao_implementacao: ou ausente
- teste_humano: pendente
- verificacao_automatica: pendente
- aprendizado: pendente
- ultima_acao: insumo 2/3 (faixas, de desempate, ausentes) recebido; consultor abriu o sub-insumo 2b (pesos por profissão) (06/11/2026)
- proxima_acao: coletar insumo 2b — peso por profissão, com as listas literais extraídas do código
- atualizado_em: 2026-11-06T13:50:00Z

## Estado por task

- REF-01 (Fila): ABERTA — erro não reproduzido; diagnóstico 29/10 inconclusivo por SPEC; se recorrer, coletar tela/link, papel, aparelho, passos e mensagem de erro, sem senha.
- REF-02, REF-03 e REF-04: concluídas e aceitas (v0.0.92 `db03c5f`, v0.0.93 `9ba9ab8`, v.0.94 `f569edc`) — histórico em `04_fase-attual/fase.md`, `STATUS.md`, `changelog.md` e APs correspondentes.
- REF-05: análise e insumos em `04_fase-atual/ref05-insumos.md`.
- Pendência humana acumulada: 3 submissões sintéticas + 1 agendamento de teste (limpeza a decidir).
- Este arquivo foi enxutado em 06/11/2026: detalhes por task vivem em documentos dedicados; aqui fica só o bloco vivo de controle.

- fase_5: planejada, liberar somente pelo ritual após F4
