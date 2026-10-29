# Estado atual — refinamentos

## Direção vigente — confirmação do consultor em 27/10/2026 17:43

Objetivo único das etapas restantes: refinar, validar e concluir a plataforma atual. Executar REF-01 a REF-12, depois os controles locais de qualidade/conversão previstos na fase 4, e finalizar com validação ponta a ponta e encerramento na fase 5. Novo mapeamento somente APÓS concluir a fase 5, em outro processo, sem entrega adicional presumida neste plano.

Não solicitar credenciais, desenhar integrações externas ou incluir escopo de outro sistema nas tasks atuais. Os quatro cards de integração/painel e a subtarefa ficam suspensos, não concluídos, somente para rastreabilidade. Não iniciar nem discutir novo escopo durante os refinamentos. Histórico de decisões não é orientação de execução.

Uma implementação por vez, insumos operacionais perguntados à cliente na própria task, prova técnica e teste humano explícito. Primeira ação: REF-01, diagnóstico da Fila. Prazos a combinar. Nada é marcado concluído por esta atualização documental.

## Controle do orquestrador

- task_id: d2aebe4c-2a02-48dc-a4fa-3ec1519b2ace (REF-03 — Atualizar as opções de rotina e a pergunta de profissão)
- champion: Karol e Márcio
- spec: 04_fase-atual/specs/spec-4-004-refinamento-formulario-fila-visao.md (seção REF-03)
- etapa: aguardando_autorizacao
- insumos_recebidos: (1) lista CLT — Ricardo, 29/10/2026 16:18, literal: "Assistente administrativo; vendedor; técnico enfermagem; médico; engenheiro; outros (se selecionar outros, colocar campo para escrever qual)" — texto livre aprovado para Outros do CLT; (2) obrigatoriedade — Ricardo, 29/10/2026 16:23, literal: "obrigatória para CLT e Autônomo"; (3) lista Autônomo — Ricardo, 29/10/2026 16:23, literal: "cabeleireiro; eletricista; advogado; dentista; médico; outros (se selecionar outros, colocar campo para escrever qual)" — texto livre aprovado para Outros do Autônomo; confirmação: "retirar as categorias genéricas (saúde/educação/plantonista)". NOTA: a lista aprovada NÃO inclui nutricionista (que a SPEC citava como exemplo do documento) — vale a lista literal aprovada; (4) rótulo Executivo/Gestor — Ricardo, 29/10/2026 16:25, literal: "Diretor ou alta gerência"
- insumos_pendentes: NENHUM — 4/4 coletados
- autorizacao_implementacao: AUSENTE — portão atual
- teste_humano: pendente
- verificacao_automatica: pendente
- aprendizado: pendente
- ultima_acao: insumos 4/4 completos (último: rótulo "Diretor ou alta gerência")
- proxima_acao: aguardar autorização explícita do Ricardo para implementar
- atualizado_em: 2026-10-29T19:28:00Z

## REF-01 — Fila (ABERTA, não corrigida)

- Diagnóstico somente leitura 29/10: `/fila` abre no preview; gate da Fila aceita só `champion`/`consultor` (a Visão aceita também `gestao`/`supervisora`); nenhum link de navegação para `/fila` no app; produção 404; leitura de `lead_handoffs`/`lead_appointments` responde 200 sem autenticação, com 0 registros no teste (`agenda_slots` expôs 2 horários).
- Relato da cliente em 29/10 (literal): "abrir novamente a fila e abriu, anteriormente estava aparecendo um erro. agora funcionou normalmente".
- Status: ABERTA — erro não reproduzido; por especificação, diagnóstico inconclusivo e task não declarada corrigida. Se recorrer, coletar tela/link, papel, aparelho, passos e mensagem de erro, sem senha.

## REF-02 — concluída (29/10/2026, Skip v0.0.92 db03c5f)

- Triagem leva o contexto ao agendamento pelo estado do roteador (nada na URL, sem armazenamento local); `/agendar` pré-preenche "Seus dados" e reusa o mesmo `lead_submission_id` (B3-03).
- Acesso direto sem triagem mantém o comportamento anterior; falha de leitura mantém o formulário vazio sem sucesso falso.
- Teste humano aprovado pelo operador; persistência entre visitas segue fora do recorte.
- Pendências de limpeza (decisão humana): 2 submissões sintéticas ("Teste REF02 Sintetico", "Teste REF02 Fechamento") + 1 agendamento de teste em `slot-2026-09-21-1130`.

## Análise REF-03 — resumo sanitizado (29/10/2026)

- Estado atual do código (v0.0.92): OCUPACOES tem 7 opções — CLT; Autônomo/Empresário (juntos); Executivo/Gestor; Estudante; Aposentado; "Profissional da saúde, educação ou outra área com horário irregular" (categorias genéricas); "Prefiro não informar". Não existe pergunta secundária de profissão.
- Valor interno = rótulo hoje (ex.: o que vai para `ocupacao` é "CLT", "Autônomo/Empresário"...). Mudanças de lista alteram valores futuros; histórico antigo continua legível (texto puro), sem recálculo (regra 5 da SPEC).
- Contrato da SPEC: Autônomo e Empresário separados; categorias genéricas retiradas; Executivo/Gestor exibido como "Diretor ou alta gerência"; CLT e Autônomo abrem pergunta secundária pertinente; "Outros" não coleta texto livre sem aprovação; não inventar profissões.
- Insumos bloqueantes da implementação: TODOS coletados em 29/10 (lista CLT; obrigatoriedade; lista Autônomo + retirada das genéricas; rótulo "Diretor ou alta gerência").
- Recorte técnico previsto: ajuste de OCUPACOES + pergunta secundária condicional no Index.tsx; transporte do contexto para /agendar (REF-02) atualizado se a profissão passar a ser coletada na triagem; nenhuma migração (campo ocupacao é texto); versão do formulário registrada.

- fase_5: planejada, liberar somente pelo ritual após F4
