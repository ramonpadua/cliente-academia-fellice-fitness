# Changelog

## 2026-10-29 — REF-02 concluída (Fase 4, emenda E-F4-REF-20261027)

- Task `ce389a55-5a06-4dbe-b3d6-4516d17a0968` (REF-02 — Levar as respostas já preenchidas até o agendamento) concluída: a triagem leva o contexto ao agendamento pelo estado do roteador (nada na URL, sem armazenamento local); `/agendar` pré-preenche "Seus dados" e reusa o mesmo `lead_submission_id` — sem lead/agendamento duplicado (contrato B3-03).
- Skip v0.0.92 (commit `db03c5f`); QA setup/análise estática/build/integrações OK (suite de testes inexistente no projeto, ran=false).
- Provas no preview (bundle `index-CRXOd1Qj.js`): GREEN 2× — pré-preenchimento de nome, telefone, profissão e e-mail; localidade mapeada ("Trabalho na região do Itaigara" → comercial; "Moro no Itaigara..." → residencial); correção de campo aceita antes de confirmar; reserva efetivada (ocupação do slot `slot-2026-09-21-1130` active=1 em 29/10 19:05 UTC). Negativo: acesso direto a `/agendar` sem triagem mantém o formulário vazio.
- Teste humano: aprovado pelo operador Ricardo em 29/10/2026 (~16:00, mensagem literal "Teste OK — 'Seus dados' veio preenchido"), após RED reproduzido pelo mesmo operador no mesmo dia.
- REF-01 segue ABERTA (erro não reproduzido; diagnóstico inconclusivo por SPEC). Pendências: limpeza das submissões sintéticas de teste em `lead_submissions` + 1 agendamento de teste; produção permanece não publicada (autorização separada).

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