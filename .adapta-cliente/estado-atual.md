# Estado atual — refinamentos

## Direção vigente — confirmação do consultor em 27/10/2026 17:43

Objetivo único das etapas restantes: refinar, validar e concluir a plataforma atual. Executar REF-01 a REF-12, depois os controles locais de qualidade/conversão previstos na fase 4, e finalizar com validação ponta a ponta e encerramento na fase 5. Novo mapeamento somente APÓS concluir a fase 5, em outro processo, sem entrega adicional presumida neste plano.

Não solicitar credenciais, desenhar integrações externas ou incluir escopo de outro sistema nas tasks atuais. Os quatro cards de integração/painel e a subtarefa ficam suspensos, não concluídos, somente para rastreabilidade. Não iniciar nem discutir novo escopo durante os refinamentos. Histórico de decisões não é orientação de execução.

Uma implementação por vez, insumos operacionais perguntados à cliente na própria task, prova técnica e teste humano explícito. Primeira ação: REF-01, diagnóstico da Fila. Prazos a combinar. Nada é marcado concluído por esta atualização documental.

## Controle do orquestrador

- task_id: cf0687e4-1384-44ba-ae1b-6675124d27f0 (REF-04 — Corrigir o endereço e eliminar a oferta duplicada de freepass)
- champion: Karol e Márcio
- spec: 04_fase-atual/specs/spec-4-004-refinamento-formulario-fila-visao.md (seção REF-04)
- etapa: aguardando_autorizacao
- insumos_recebidos: NENHUM — coleta inicia nesta task
- insumos_pendentes: (1) endereço exato aprovado e em quais superfícies deve aparecer; (2) momento correto da oferta (onde o freepass/prêmio deve aparecer e onde NÃO); (3) texto do prêmio final e se é o mesmo benefício ("Aula Experimental Gratuita")
- autorizacao_implementacao: ausente
- teste_humano: pendente
- verificacao_automatica: pendente
- aprendizado: pendente
- ultima_acao: análise REF-04 concluída — inventário de endereço e de menções de prêmio/freepass no código (30/10/2026, somente leitura)
- proxima_acao: coletar insumos na própria task, uma pergunta por vez, a partir do endereço exato aprovado
- atualizado_em: 2026-10-30T19:50:00Z

## Fechamento REF-03 — 30/10/2026 (v0.0.93, commit 9ba9ab8)

- Teste humano aprovado pelo operador Ricardo em 30/10/2026 16:31 (literal: "Teste OK — pode concluir a REF-03").
- Revalidação independente do fechamento (30/10): working tree do Skip confere com o implementado em 29/10 (Index.tsx FORM_VERSION v1.1.0 com listas aprovadas, secundária condicional obrigatória, Outros com texto, limpeza na troca de rotina, gravação em lead_submissions/evento/lead_handoffs; Agendar.tsx transporta profissão com fallback para ocupação); migração `0059_ref03_ocupacao_profissao` status applied; schema de `lead_submissions` com select `ocupacao` (7 valores aprovados) + texto `profissao` (160); QA Skip verde (suite inexistente, ran=false).
- Documentação atualizada: fase.md (checkbox + nota CONCLUÍDA), STATUS.md, changelog.md, controle.md e AP-2026-10-30-1640.
- Pendências de limpeza acumuladas (decisão humana): 3 submissões sintéticas ("Teste REF02 Sintetico", "Teste REF02 Fechamento", "Teste REF03 Sintetico") + 1 agendamento de teste em `slot-2026-09-21-1130`.
- Próxima task elegível pela SPEC: REF-04 (endereço/freepass), pré-condição REF-03 aceita satisfeita; insumos a coletar na própria task.

## REF-01 — Fila (ABERTA, não corrigida)

- Diagnóstico somente leitura 29/10: `/fila` abre no preview; gate da Fila aceita só `champion`/`consultor` (a Visão aceita também `gestao`/`supervisora`); nenhum link de navegação para `/fila` no app; produção 404; leitura de `lead_handoffs`/`lead_appointments` responde 200 sem autenticação, com 0 registros no teste (`agenda_slots` expôs 2 horários).
- Relato da cliente em 29/10 (literal): "abrir novamente a fila e abriu, anteriormente estava aparecendo um erro. agora funcionou normalmente".
- Status: ABERTA — erro não reproduzido; por especificação, diagnóstico inconclusivo e task não declarada corrigida. Se recorrer, coletar tela/link, papel, aparelho, passos e mensagem de erro, sem senha.

## REF-02 — concluída (29/10/2026, Skip v0.0.92 db03c5f)

- Triagem leva o contexto ao agendamento pelo estado do roteador (nada na URL, sem armazenamento local); `/agendar` pré-preenche "Seus dados" e reusa o mesmo `lead_submission_id` (B3-03).
- Acesso direto sem triagem mantém o comportamento anterior; falha de leitura mantém o formulário vazio sem sucesso falso.
- Teste humano aprovado pelo operador; persistência entre visitas segue fora do recorte.
- Pendências de limpeza (decisão humana): 2 submissões sintéticas ("Teste REF02 Sintetico", "Teste REF02 Fechamento") + 1 agendamento de teste em `slot-2026-09-21-1130` + 1 submissão sintética REF-03 ("Teste REF03 Sintetico").

## Implementação REF-03 — concluída 29/10/2026 (v0.0.93, commit 9ba9ab8)

- Migração 0059: select `ocupacao` de lead_submissions com a lista aprovada (CLT, Autônomo, Empresário, Diretor ou alta gerência, Estudante, Aposentado, Prefiro não informar) + campo texto `profissao` (160). Down restaura a lista antiga. Histórico não recalculado (regra 5).
- Index.tsx (FORM_VERSION v1.1.0): listas novas; pergunta secundária condicional (só CLT e Autônomo), obrigatória; "Outros" abre campo de texto (aprovado); trocar a rotina limpa profissão e texto; profissão gravada em lead_submissions, payload do evento TRIAGEM_CONCLUIDA e lead_handoffs.
- Agendar.tsx: contexto da triagem leva `profissao` e pré-preenche "Seus dados" (fallback: ocupação).
- Prova técnica no preview: lista nova renderizada; CLT mostra 6 profissões; Autônomo mostra 6 profissões; Seguir sem profissão bloqueia na etapa 6; CLT→Estudante removeu a secundária; submissão Autônomo/Advogado concluída com sucesso; /agendar pré-preencheu Profissão "Advogado". Leitura anônima da API é 403 por design (listRule null).

## Análise REF-03 — resumo sanitizado (29/10/2026)

- Estado anterior do código (v0.0.92): OCUPACOES tinha 7 opções — CLT; Autônomo/Empresário (juntos); Executivo/Gestor; Estudante; Aposentado; "Profissional da saúde, educação ou outra área com horário irregular" (categorias genéricas); "Prefiro não informar". Não existia pergunta secundária de profissão.
- Valor interno = rótulo antes da REF-03; a migração 0059 altera valores futuros; histórico antigo continua legível (texto puro), sem recálculo (regra 5 da SPEC).
- Recorte executado: migração 0059 + Index.tsx + Agendar.tsx; nenhuma outra coleção alterada.

## Análise REF-04 — resumo sanitizado (30/10/2026, somente leitura)

- Endereço no código: header do formulário "Terrazzo R1 Sports Club · Alto do Itaigara" (Index.tsx, bloco do cabeçalho); rodapé do formulário "Terrazzo R1 Sports Club · Rua Rosa dos Ventos, Alto do Itaigara" (Index.tsx, rodapé); Agendar.tsx cita "Terrazzo R1 Sports Club" sem rua (2 ocorrências); telas internas (Fila/Visão/Funil/Dashboard/Saude/NotFound) sem endereço voltado a lead.
- Menções de prêmio/freepass no formulário (Index.tsx): microcopy da etapa 6 ("desbloquear seu prêmio"); microcopy da etapa 7 ("garanta sua Aula Experimental Gratuita"); mensagem de erro do consentimento ("resgatar o prêmio"); mensagem do WhatsApp pós-triagem ("agendar minha Aula Experimental Gratuita"); tela de sucesso com 2 menções ("Seu prêmio de Aula Experimental Gratuita está desbloqueado..." e "Resgate sua Aula Experimental Gratuita agora"); botão final ("Concluir & Resgatar Prêmio"); checkbox de consentimento ("Aula Experimental Gratuita, avisos e informações").
- Agendar.tsx não menciona prêmio/freepass.
- Nenhuma alteração feita nesta etapa; insumos bloqueiam implementação (regra da emenda: não escolher endereço por pesquisa pública, não criar promessa comercial).

- fase_5: planejada, liberar somente pelo ritual após F4
