# Estado atual — refinamentos

## Direção vigente — confirmação do consultor em 27/10/2026 17:43

Objetivo único das etapas restantes: refinar, validar e concluir a plataforma atual. Executar REF-01 a REF-12, depois os controles locais de qualidade/conversão previstos na fase 4, e finalizar com validação ponta a ponta e encerramento na fase 5. Novo mapeamento somente APÓS concluir a fase 5, em outro processo, sem entrega adicional presumida neste plano.

Não solicitar credenciais, desenhar integrações externas ou incluir escopo de outro sistema nas tasks atuais. Os quatro cards de integração/painel e a subtarefa ficam suspensos, não concluídos, somente para rastreabilidade. Não iniciar nem discutir novo escopo durante os refinamentos. Histórico de decisões não é orientação de execução.

Uma implementação por vez, insumos operacionais perguntados à cliente na própria task, prova técnica e teste humano explícito. Primeira ação: REF-01, diagnóstico da Fila. Prazos a combinar. Nada é marcado concluído por esta atualização documental.

## Controle do orquestrador

- task_id: 547994b2-a335-4fd9-878a-52b67b6c0b60 (REF-05 — Criar pontuação de ocupação para priorizar o atendimento)
- champion: Karol e Márcio
- spec: 04_fase-atual/specs/spec-4-004-refinamento-formulario-fila-visao.md (seção REF-05)
- etapa: coletando_insumos
- insumos_recebidos: (1/3) escala e pesos — 06/11/2026, respostas literais do formulário da task: escala 0–10; CLT 5; Autônomo 6; Empresário 7; Diretor ou alta gerência 9; Estudante 7; Aposentado 7; Prefiro não informar 5; (2/3) faixas e desempate — 06/11/2026, respostas literais: Alta = nota ≥ 7; Baixa = nota ≤ 5 (entre eles, Média); desempate = ordem de chegada (mais antigo primeiro); resposta ausente/inválida = nota 0, cai em Baixa e exibe "Sem pontuação"
- insumos_pendentes: (2b) pesos por profissão da sub-pergunta (CLT e Autônomo) — observação literal do consultor: "as sub perguntas da triagem, dos itens clt, autonomo e o que mais tiver, precisa ter peso também"; (3) onde a equipe vê a prioridade (Fila, Visão ou ambos) e se a Fila reordena ou só exibe
- autorizacao_implementacao: ausente
- teste_humano: pendente
- verificacao_automatica: pendente
- aprendizado: pendente
- ultima_acao: insumo 2/3 (faixas, desempate, ausentes) recebido; consultor abriu o sub-insumo 2b (pesos por profissão) (06/11/2026)
- proxima_acao: coletar insumo 2b — peso por profissão, com as listas literais extraídas do código
- atualizado_em: 2026-11-06T13:50:00Z

## Fechamentos anteriores — histórico canônico em outros documentos

- REF-02 (v0.0.92 `db03c5f`), REF-03 (v0.0.93 `9ba9ab8`) e REF-04 (v0.0.94 `f569edc`): concluídas e aceitas — detalhes em `04_fase-atual/fase.md`, `STATUS.md`, `changelog.md` e APs correspondentes (todos byte-verificados pela API).
- Pendência humana acumulada: 3 submissões sintéticas + 1 agendamento de teste (limpeza a decidir).
- Este arquivo foi enxugado em 06/11/2026 após 3 degradações seguidas de transcrição inline (~13,6 KB); o histórico completo permanece nos documentos canônicos e no histórico Git deste arquivo.

## REF-01 — Fila (ABERTA, não corrigida)

- Diagnóstico somente leitura 29/10: `/fila` abre no preview; gate da Fila aceita só `champion`/`consultor` (a Visão aceita também `gestao`/`supervisora`); nenhum link de navegação para `/fila` no app; produção 404; leitura de `lead_handoffs`/`lead_appointments` responde 200 sem autenticação, com 0 registros no teste (`agenda_slots` expôs 2 horários).
- Relato da cliente em 29/10 (literal): "abrir novamente a fila e abriu, anteriormente estava aparecendo um erro. agora funcionou normalmente".
- Status: ABERTA — erro não reproduzido; por especificação, diagnóstico inconclusivo e task não declarada corrigida. Se recorrer, coletar tela/link, papel, aparelho, passos e mensagem de erro, sem senha.

## Análise REF-05 — resumo sanitizado (06/11/2026, somente leitura)

- Fonte das respostas: `lead_submissions.ocupacao` (select com as 7 opções aprovadas na REF-03 — migração 0059); respostas antigas anteriores à REF-03 têm valores de rótulo (texto puro) e não estão na lista nova.
- Recorte da SPEC: pesos aprovados pela cliente; cálculo determinístico e versionado, com valor e motivo rastreáveis; respostas ausentes/inválidas não geram nota favorável inventada; não ordenar/repriorizar histórico sem decisão própria; esta task NÃO decide quem pode agendar (elegibilidade é REF-06; score só entra lá se a cliente vincular formalmente).
- Superfícies de exibição candidatas: Fila (`/fila`, Queue.tsx — gate champion/consultor) e Visão (`/visao`, Visao.tsx — gate champion/consultor/gestao/supervisora); onde a equipe quer ver é insumo.
- Persistência candidata: campo(s) novo(s) em `lead_submissions` (valor + versão da matriz v1) via migração 0060 — decisões de estrutura só após insumos e autorização.
- Nada alterado nesta etapa; a SPEC proíbe inferir pesos de cargo/renda e criar mapa de calor não solicitado.

## Insumos REF-05 — recebidos do consultor (06/11/2026)

- **Insumo 1/3 — escala e pesos (respostas literais do formulário da task):** escala 0–10; Profissional CLT = 5; Autônomo = 6; Empresário = 7; Diretor ou alta gerência = 9; Estudante = 7; Aposentado = 7; Prefiro não informar = 5.
- Observação registrada: "Prefiro não informar" recebeu peso explícito 5 — decisão do consultor; é distinta do tratamento de resposta AUSENTE/inválida (a definir no insumo 2).
- Observação para o insumo 2 (não é decisão): com esses pesos, se as faixas forem Alta ≥8 / Média 5–7 / Baixa 0–4, nenhuma resposta da lista cai em Baixa — apenas resposta ausente com nota 0.
- **Insumo 2/3 — faixas, desempate e ausentes (respostas literais do formulário da task):** Alta = nota ≥ 7; Baixa = nota ≤ 5 (entre eles, Média); desempate = ordem de chegada (mais antigo primeiro); resposta ausente/inválida = nota 0, cai em Baixa e exibe "Sem pontuação".
- Efeito das faixas aprovadas sobre os pesos do insumo 1: Alta = Diretor ou alta gerência (9), Empresário (7), Estudante (7), Aposentado (7); Média = Autônomo (6); Baixa = CLT (5), Prefiro não informar (5) e resposta ausente (0).
- **Sub-insumo 2b — aberto pelo consultor (observação literal):** "as sub perguntas da triagem, dos itens clt, autonomo e o que mais tiver, precisa ter peso também" — cada profissão da pergunta secundária precisa de peso próprio; listas literais a extrair do código; coleta pendente.
- Listas literais extraídas do código (Index.tsx v1.1.1, working tree Skip, 06/11/2026): PROFISSOES_CLT = Assistente administrativo, Vendedor, Técnico de enfermagem, Médico, Engenheiro, Outros; PROFISSOES_AUTONOMO = Cabeleireiro, Eletricista, Advogado, Dentista, Médico, Outros. Somente CLT e Autônomo têm pergunta secundária; "Outros" abre texto livre (campo `profissao`).

- fase_5: planejada, liberar somente pelo ritual após F4
