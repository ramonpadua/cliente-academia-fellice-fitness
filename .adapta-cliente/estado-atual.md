# Estado atual — refinamentos

## Direção vigente — confirmação do consultor em 27/10/2026 17:43

Objetivo único das etapas restantes: refinar, validar e concluir a plataforma atual. Executar REF-01 a REF-12, depois os controles locais de qualidade/conversão previstos na fase 4, e finalizar com validação ponta a ponta e encerramento na fase 5. Novo mapeamento somente APÓS concluir a fase 5, em outro processo, sem entrega adicional presumida neste plano.

Não solicitar credenciais, desenhar integrações externas ou incluir escopo de outro sistema nas tasks atuais. Os quatro cards de integração/painel e a subtarefa ficam suspensos, não concluídos, somente para rastreabilidade. Não iniciar nem discutir novo escopo durante os refinamentos. Histórico de decisões não é orientação de execução.

Uma implementação por vez, insumos operacionais perguntados à cliente na própria task, prova técnica e teste humano explícito. Primeira ação: REF-01, diagnóstico da Fila. Prazos a combinar. Nada é marcado concluído por esta atualização documental.

## Controle do orquestrador

- task_id: 547994b2-a335-4fd9-878a-52b67b6c0b60 (REF-05 — Criar pontuação de ocupação para priorizar o atendimento)
- champion: Karol e Márcio
- spec: 04_fase-atual/specs/spec-4-004-refinamento-formulario-fila-visao.md (seção REF-05)
- etapa: aguardando_autorizacao
- insumos_recebidos: NENHUM — coleta inicia nesta task
- insumos_pendentes: (1) escala e pesos por opção de rotina (7 opções aprovadas na REF-03); (2) faixas de prioridade, desempate e tratamento de "Prefiro não informar"/resposta ausente; (3) onde a equipe vê a prioridade (Fila, Visão ou ambos)
- autorizacao_implementacao: ausente
- teste_humano: pendente
- verificacao_automatica: pendente
- aprendizado: pendente
- ultima_acao: análise REF-05 concluída — inventário de onde a pontuação pode nascer e das telas de exibição (06/11/2026, somente leitura)
- proxima_acao: coletar insumos na própria task, uma pergunta por vez, a partir da escala e dos pesos por opção
- atualizado_em: 2026-11-06T13:40:00Z

## Fechamento REF-03 — 30/10/2026 (v0.0.93, commit 9ba9ab8)

- Teste humano aprovado pelo operador Ricardo em 30/10/2026 16:31 (literal: "Teste OK — pode concluir a REF-03").
- Revalidação independente do fechamento (30/10): working tree do Skip confere com o implementado em 29/10 (Index.tsx FORM_VERSION v1.1.0 com listas aprovadas, secundária condicional obrigatória, Outros com texto, limpeza na troca de rotina, gravação em lead_submissions/evento/lead_handoffs; Agendar.tsx transporta profissão com fallback para ocupação); migração `0059_ref03_ocupacao_profissao` status applied; schema de `lead_submissions` com select `ocupacao` (7 valores aprovados) + texto `profissao` (160); QA Skip verde (suite inexistente, ran=false).
- Documentação atualizada: fase.md (checkbox + nota CONCLUÍDA), STATUS.md, changelog.md, controle.md e AP-2026-10-30-1640.
- Pendências de limpeza acumuladas (decisão humana): 3 submissões sintéticas ("Teste REF02 Sintetico", "Teste REF02 Fechamento", "Teste REF03 Sintetico") + 1 agendamento de teste em `slot-2026-09-21-1130`.
- Próxima task elegível pela SPEC: REF-04 (endereço/freepass), pré-condição REF-03 aceita satisfeita; insumos a coletar na própria task.

## Fechamento REF-04 — 06/11/2026 (v0.0.94, commit f569edc)

- Teste humano aprovado pelo operador Ricardo em 06/11/2026 10:28 (literal: "o teste está ok"), com ressalva registrada: "o prêmio está disponível para todos, independente da triagem, a triagem é feita para qualificar o perfil do nosso cliente".
- A ressalva confirma o recorte acordado: a oferta única pós-triagem foi implementada na REF-04; a condicionalidade por qualificação/perfil (elegibilidade) é escopo da REF-06 e depende da matriz de perfil ainda não aprovada. A frase do Ricardo fica registrada como insumo antecipado da REF-06.
- Revalidação independente do fechamento (06/11): working tree v0.0.94 (commit f569edc) com Index.tsx v1.1.1 e Agendar.tsx; bundle do preview (index-DtdHmEAH.js) rebaixado e conferido — endereço aprovado 3×+1 parcial; 0 ocorrências dos textos de prêmio pré-triagem; oferta restante somente pós-triagem (3×); QA Skip verde (suite inexistente, ran=false).
- Pendências de limpeza acumuladas (decisão humana): 3 submissões sintéticas + 1 agendamento de teste.
- Próxima task elegível pela SPEC: REF-05 (pontuação de ocupação), pré-condição REF-03 aceita satisfeita; insumos (pesos por opção, escala, faixas, desempate) a coletar na própria task.

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

## Implementação REF-04 — concluída 06/11/2026 (v0.0.94, commit f569edc)

- Index.tsx (FORM_VERSION v1.1.1): header e rodapé com o endereço aprovado; microcopy das etapas 6 e 7 sem menção a prêmio; erro do consentimento sem "resgatar o prêmio"; botão final "Concluir" (sem "Resgatar Prêmio"); checkbox de consentimento sem "Aula Experimental Gratuita".
- Agendar.tsx: header e confirmação de reserva com o endereço aprovado.
- Tela de sucesso e mensagem do WhatsApp preservadas (momento aprovado da oferta; insumo 3: mesmo benefício "Aula Experimental Gratuita").
- Sem migração, sem mudança de coleção, sem nova promessa comercial; condicionalidade por perfil segue para REF-06.
- QA Skip verde (setup, estática, build, integrações; suite inexistente, ran=false). Provas no bundle index-DtdHmEAH.js: endereço 3×+1 parcial; 0 textos de prêmio pré-triagem; oferta só pós-triagem.

## Análise REF-04 — resumo sanitizado (30/10/2026, somente leitura)

- Endereço no código: header do formulário "Terrazzo R1 Sports Club · Alto do Itaigara" (Index.tsx, bloco do cabeçalho); rodapé do formulário "Terrazzo R1 Sports Club · Rua Rosa dos Ventos, Alto do Itaigara" (Index.tsx, rodapé); Agendar.tsx cita "Terrazzo R1 Sports Club" sem rua (2 ocorrências); telas internas (Fila/Visão/Funil/Dashboard/Saude/NotFound) sem endereço voltado a lead.
- Menções de prêmio/freepass no formulário (Index.tsx): microcopy da etapa 6 ("desbloquear seu prêmio"); microcopy da etapa 7 ("garanta sua Aula Experimental Gratuita"); mensagem de erro do consentimento ("resgatar o prêmio"); mensagem do WhatsApp pós-triagem ("agendar minha Aula Experimental Gratuita"); tela de sucesso com 2 menções ("Seu prêmio de Aula Experimental Gratuita está desbloqueado..." e "Resgate sua Aula Experimental Gratuita agora"); botão final ("Concluir & Resgatar Prêmio"); checkbox de consentimento ("Aula Experimental Gratuita, avisos e informações").
- Agendar.tsx não menciona prêmio/freepass.
- Nenhuma alteração feita nesta etapa; insumos bloqueiam implementação (regra da emenda: não escolher endereço por pesquisa pública, não criar promessa comercial).

## Análise REF-05 — resumo sanitizado (06/11/2026, somente leitura)

- Fonte das respostas: `lead_submissions.ocupacao` (select com as 7 opções aprovadas na REF-03 — migração 0059); respostas antigas anteriores à REF-03 têm valores de rótulo (texto puro) e não estão na lista nova.
- Recorte da SPEC: pesos aprovados pela cliente; cálculo determinístico e versionado, com valor e motivo rastreáveis; respostas ausentes/inválidas não geram nota favorável inventada; não ordenar/repriorizar histórico sem decisão própria; esta task NÃO decide quem pode agendar (elegibilidade é REF-06; score só entra lá se a cliente vincular formalmente).
- Superfícies de exibição candidatas: Fila (`/fila`, Queue.tsx — gate champion/consultor) e Visão (`/visao`, Visao.tsx — gate champion/consultor/gestao/supervisora); onde a equipe quer ver é insumo.
- Persistência candidata: campo(s) novo(s) em `lead_submissions` (valor + versão da matriz + motivo) via migração 0060 — decisões de estrutura só após insumos e autorização.
- Nada alterado nesta etapa; a SPEC proíbe inferir pesos de cargo/renda e criar mapa de calor não solicitado.

- fase_5: planejada, liberar somente pelo ritual após F4
