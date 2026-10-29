# Status do plano

## Direção vigente — confirmação do consultor em 27/10/2026 17:43

Objetivo único das etapas restantes: refinar, validar e concluir a plataforma atual. Executar REF-01 a REF-12, depois os controles locais de qualidade/conversão previstos na fase 4, e finalizar com validação ponta a ponta e encerramento na fase 5. Novo mapeamento somente APÓS concluir a fase 5, em outro processo, sem entrega adicional presumida neste plano.

Não solicitar credenciais, desenhar integrações externas ou inserir escopo de outro sistema nas tasks atuais. Os quatro cards de integração/painel e a subtarefa ficam suspensos, não concluídos, somente para rastreabilidade. Não iniciar nem discutir novo escopo durante os refinamentos. Histórico de decisões não é orientação de execução.

Uma implementação por vez, insumos operacionais perguntados à cliente na própria task, prova técnica e teste humano explícito. Primeira ação: REF-01, diagnóstico da Fila. Prazos a combinar. Nada é marcado concluído por esta atualização documental.

## Estado atual

- Fase atual: 4 — refinamentos da plataforma e validação/conversão local.
- Entregas anteriores: fases 1 a 3 encerradas, arquivos e aceites preservados.
- Cards preservados: 20 de topo; 12 refinamentos + 4 cards locais (baseline, loop, ciclo, revisão final) pendentes; 4 cards suspensos fora do recorte de execução. **REF-02 concluída em 29/10/2026 com teste humano aprovado; REF-01 segue aberta (erro não reproduzido, diagnóstico inconclusivo por SPEC). Nenhum outro aceite registrado.**
- Execução técnica: Skip v0.0.92 (commit `db03c5f`) no preview; produção não publicada. Banco alterado apenas por dados sintéticos de teste (2 submissões + 1 agendamento), pendentes de limpeza por migração.

## Sequência restante

1. REF-01 a REF-10: corrigir e refinar formulário, dados, mídia, priorização, agendamento, Fila e Visão, conforme decisões confirmadas nas próprias tasks. (REF-02 concluída 29/10.)
2. REF-11 e REF-12: regressão do conjunto e aceite da cliente, sem avançar em falha.
3. Baseline/alvo e ciclo local: medir fontes locais autorizadas, registrar cobertura/limitações e veredito humano. Não inventar dados ou declarar ganho sem evidência.
4. Revisão da fase 4 pelo consultor, considerando somente o recorte vigente.
5. Fase 5, planejada e não liberada automaticamente: regressão de todo o sistema, segurança/privacidade/rollback, medição, registro de limitações e decisão humana de encerramento.
6. Depois da fase 5 concluída: novo mapeamento, em outro processo, fora das tasks atuais.

## Próxima ação

REF-03 (Atualizar as opções de rotina e a pergunta de profissão) — pré-condição REF-02 aceita, agora satisfeita; insumos (lista CLT e obrigatoriedade da pergunta secundária) coletados na própria task. Alternativa: retomar REF-01 se a Fila voltar a falhar. Nenhuma conta externa é pré-requisito.
