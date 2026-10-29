# Changelog

## 2026-10-29 — REF-02 concluída (Fase 4, emenda E-F4-REF-20261027)

- Task `ce389a55-5a06-4dbe-b3d6-4516d17a0968` (REF-02 — Levar as respostas já preenchidas até o agendamento) concluída: a triagem leva o contexto ao agendamento pelo estado do roteador (nada na URL, sem armazenamento local); `/agendar` pré-preenche "Seus dados" e reusa o mesmo `lead_submission_id` — sem lead/agendamento duplicado (contrato B3-03).
- Skip v0.0.92 (commit `db03c5f`); QA setup/análise estática/build/integrações OK (suite de testes inexistente no projeto, ran=false).
- Provas no preview (bundle `index-CRXOd1Qj.js`): GREEN 2× — pré-preenchimento de nome, telefone, profissão e e-mail; localidade mapeada ("Trabalho na região do Itaigara" → comercial; "Moro no Itaigara..." → residencial); correção de campo aceita antes de confirmar; reserva efetivada (ocupação do slot `slot-2026-09-21-1130` active=1 em 29/10 19:05 UTC). Negativo: acesso direto a `/agendar` sem triagem mantém o formulário vazio.
- Teste humano: aprovado pelo operador Ricardo em 29/10/2026 (~16:00, mensagem literal "Teste OK — 'Seus dados' veio preenchido"), após RED reproduzido pelo mesmo operador no mesmo dia.
- REF-01 segue ABERTA (erro não reproduzido; diagnóstico inconclusivo por SPEC). Pendências: limpeza das submissões sintéticas de teste em `lead_submissions` + 1 agendamento de teste; produção permanece não publicada (autorização separada).

## 2026-10-27 17:51 — instruções de entrada alinhadas

- README, CLAUDE e AGENTS corrigidos para a Fase 4 atual e retomada pela REF-01; referências de entrada às fases anteriores removidas.
- Sem mudança de fase, tarefa, status de execução ou aceite. Orientações para coleta de insumos e teste humano consistentes.
- Nenhuma execução automática ou atualização de sessão aberta é presumida pela publicação documental.

## 2026-10-27 17:43 — direção final de continuidade

- Consultor confirmou refinamentos e conclusão da plataforma até a F5; novo mapeamento só depois, em outro processo.
- STATUS e retomada ativos limpos; suspensões não geram cobrança de insumos nem bloqueiam as tasks locais.
- F5 planejada ajustada no Plano para validar refinamentos e encerrar o conjunto; não liberada automaticamente.
- Publicação documental autorizada; nenhuma implementação, migração ou mudança em produção.

## 2026-10-27 — E-F4-KOMMO-20261027

- Recorte vigente: refinar, validar e concluir a plataforma atual (REF-01 a REF-12), depois baseline/alvo, loop e ciclo com fontes locais, e revisão do consultor. Fase 5 planejada e não liberada automaticamente.
- Integração Kommo, painel de integração e subtarefa de conector SUSPENSOS (não concluídos): fora do recorte, sem execução, sem insumos, sem credenciais; preservados para rastreabilidade.
- Task 7953f975 e decisões B4 fora do recorte; não pedir insumos B4. Loop/revisão passam a usar somente fontes locais.
- Nada é marcado concluído por esta emenda; prazos a combinar.

## 2026-10-27 — Emenda E-F4-REF-20261027

- 12 cards de refinamento publicados (REF-01 a REF-12) a partir de `pontos_de_melhoria.docx` (16 pedidos); SPEC-4-004 criada com contratos por task e critérios CA-4-R01..R12.
- Aprovação do consultor em 27/10 17:25 ("Aprovo a proposta. Atualize os documentos e publique as novas tasks, preservando as concluídas.").
- Cards anteriores preservados integralmente; fases encerradas e aceites intactos. Aprovação de documentação não equivale a execução ou aceite de produto.

## 2026-10-16

- Ciclo design system A+B concluído: `Index.tsx` migrado para shadcn/Tailwind (v0.0.89, commit `3a3bd99`), contrato de dados preservado; teste humano aprovado.
- Registro B4 de 16/10 documentado em `03_documentos/decisoes-fase-4.md` (base legal, ferramenta/ambiente, mapeamento/unificação) com pendências explícitas; validação documental de Ricardo às 17:12.
- Reparos de integridade aplicados (commits `b05de380`, `a2ac3467`, `956c1b35`); AP-2026-10-16-1600 (conferir size+blob SHA após todo commit via MCP) e AP-2026-10-16-1730 (fundação de design system ociosa) registrados em `06_notas/aprendizado-continuo/`.

## 2026-10-13

- Insumos B4 do Champion (relato de Ricardo) registrados como evidência indireta; confirmação literal com data/hora segue pendente.

## 2026-10-09

- Task 7953f975: respostas B4-01/02/05 registradas como decisão operacional do consultor, sem liberação de execução técnica; gates B4 seguem pendentes de confirmação do Champion.

## 2026-10-02

- Fase 3 encerrada: 9/9 tasks concluídas; SPEC-3-001/002 aceitas (28–30/09); check-fase-3 APROVADO COM RESSALVAS; transição F3→F4 preparada com SPECs 4-001/002/003 liberadas e tasks geradas em 01/10.

## 2026-09-30

- Fechamento da Fase 3 com aceite do Champion; baseline de conversão sem versão congelada registrado como ressalva (B3-05/B4-04).

## 2026-09-24

- Decisões F3-B3 registradas (taxonomia UTM, métrica norte, vínculo triagem→agendamento).

## 2026-08-20

- Criado `03-Projeto/requisitos.md` pela rota padrão da análise crítica.
- Registrados nove requisitos verificáveis, suas fontes, limites, dependências e decisões humanas pendentes.
- Criado `03-Projeto/revisao-do-escopo.md` com painel serial, achados calibrados, alternativas e riscos residuais.
- Criado `03-Projeto/conselho-de-decisao.md` com recomendação não vinculante para a sequência C.
- Criados `03-Projeto/analise-critica.md` e `03-Projeto/analise-do-consultor.md`; o segundo permanece integralmente pendente de autoria humana.
- Criado `STATUS.md` com o gate atual e a próxima ação segura.
- Consolidado `03-Projeto/02-Escopo-Definitivo.md` em cinco fases, incorporando a decisão humana de pré-agendamento e integração direta tardia.
- Criados a matriz de rastreabilidade e o controle interno `.adapta/checks/check-escopo.md` com status PENDENTE.
- Registrada a revisão serial do escopo definitivo; aplicada correção segura de rastreabilidade para não reintroduzir requisitos fora do recorte de pré-agendamento.
- Gerado `03-Projeto/03-Setup-Ethos/` em estado RASCUNHO, incluindo persona, sugestões de conectores, mapa operacional e dois loops candidatos sem ativação.
