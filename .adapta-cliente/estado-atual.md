# Estado atual — refinamentos

## Direção vigente — confirmação do consultor em 27/10/2026 17:43

Objetivo único das etapas restantes: refinar, validar e concluir a plataforma atual. Executar REF-01 a REF-12, depois os controles locais de qualidade/conversão previstos na fase 4, e finalizar com validação ponta a ponta e encerramento na fase 5. Novo mapeamento somente APÓS concluir a fase 5, em outro processo, sem entrega adicional presumida neste plano.

Não solicitar credenciais, desenhar integrações externas ou incluir escopo de outro sistema nas tasks atuais. Os quatro cards de integração/painel e a subtarefa ficam suspensos, não concluídos, somente para rastreabilidade. Não iniciar nem discutir novo escopo durante os refinamentos. Histórico de decisões não é orientação de execução.

Uma implementação por vez, insumos operacionais perguntados à cliente na própria task, prova técnica e teste humano explícito. Primeira ação: REF-01, diagnóstico da Fila. Prazos a combinar. Nada é marcado concluído por esta atualização documental.

## Controle do orquestrador

- task_id: d2aebe4c-2a02-48dc-a4fa-3ec1519b2ace (REF-03 — Atualizar as opções de rotina e a pergunta de profissão)
- champion: Karol e Márcio
- spec: 04_fase-atual/specs/spec-4-004-refinamento-formulario-fila-visao.md (seção REF-03)
- etapa: concluida
- insumos_recebidos: (1) lista CLT — Ricardo, 29/10/2026 16:18, literal: "Assistente administrativo; vendedor; técnico enfermagem; médico; engenheiro; outros (se selecionar outros, colocar campo para escrever qual)" — texto livre aprovado para Outros do CLT; (2) obrigatoriedade — Ricardo, 29/10/2026 16:23, literal: "obrigatória para CLT e Autônomo"; (3) lista Autônomo — Ricardo, 29/10/2026 16:23, literal: "cabeleireiro; eletricista; advogado; dentista; médico; outros (se selecionar outros, colocar campo para escrever qual)" — texto livre aprovado para Outros do Autônomo; confirmação: "retirar as categorias genéricas (saúde/educação/plantonista)". NOTA: a lista aprovada NÃO inclui nutricionista (que a SPEC citava como exemplo do documento) — vale a lista literal aprovada; (4) rótulo Executivo/Gestor — Ricardo, 29/10/2026 16:25, literal: "Diretor ou alta gerência"
- insumos_pendentes: NENHUM — 4/4 coletados
- autorizacao_implementacao: Ricardo, 29/10/2026 16:26, literal: "Autorizar implementação"
- teste_humano: aprovado — Ricardo, 30/10/2026 16:31, literal: "Teste OK — pode concluir a REF-03"
- verificacao_automatica: QA Skip verde (setup, estática, build, integrações; suite inexistente, ran=false) + prova técnica no preview concluída
- aprendizado: capturado:06_notas/aprendizado-continuo/AP-2026-10-30-1640-listas-aprovadas-valem-sobre-spec.md
- ultima_acao: fechamento REF-03 — revalidação independente (working tree, migração 0059 aplicada, schema de lead_submissions, QA Skip) e fechamento documental em fase.md, STATUS.md, changelog.md e controle.md (30/10/2026)
- proxima_acao: nova task somente por ordem do consultor — próxima elegível pela SPEC é REF-04 (endereço/freepass), com insumos a coletar na própria task
- atualizado_em: 2026-10-30T19:40:00Z

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

- fase_5: planejada, liberar somente pelo ritual após F4
