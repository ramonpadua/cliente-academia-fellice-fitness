# Estado atual — refinamentos

## Direção vigente — confirmação do consultor em 27/10/2026 17:43

Objetivo único das etapas restantes: refinar, validar e concluir a plataforma atual. Executar REF-01 a REF-12, depois os controles locais de qualidade/conversão previstos na fase 4, e finalizar com validação ponta a ponta e encerramento na fase 5. Novo mapeamento somente APÓS concluir a fase 5, em outro processo, sem entrega adicional presumida neste plano.

Não solicitar credenciais, desenhar integrações externas ou inserir escopo de outro sistema nas tasks atuais. Os quatro cards de integração/painel e a subtarefa ficam suspensos, não concluídos, somente para rastreabilidade. Não iniciar nem discutir novo escopo durante os refinamentos. Histórico de decisões não é orientação de execução.

Uma implementação por vez, insumos operacionais perguntados à cliente na própria task, prova técnica e teste humano explícito. Primeira ação: REF-01, diagnóstico da Fila. Prazos a combinar. Nada é marcado concluído por esta atualização documental.

## Controle do orquestrador

- task_id: ce389a55-5a06-4dbe-b3d6-4516d17a0968 (REF-02 — Levar as respostas já preenchidas até o agendamento)
- champion: Karol e Márcio
- spec: 04_fase-atual/specs/spec-4-004-refinamento-formulario-fila-visao.md (seção REF-02)
- etapa: implementando
- autorizacao_implementacao: confirmada — Ricardo, 29/10/2026 ~15:45, mensagem literal "pode implementar" (após relatório de análise e RED reproduzido)
- teste_humano: pendente
- verificacao_automatica: pendente (RED confirmado pelo operador em 29/10 ~15:45: "Seus dados" chega vazio)
- aprendizado: pendente
- ultima_acao: autorização registrada; preparação da implementação (acesso de escrita ao Skip Builder)
- proxima_acao: implementar o recorte REF-02 e executar verificações automáticas
- atualizado_em: 2026-10-29T15:50:00-03:00

## REF-01 — Fila (ABERTA, não corrigida)

- Diagnóstico somente leitura 29/10: `/fila` abre no preview; gate da Fila aceita só `champion`/`consultor` (a Visão aceita também `gestao`/`supervisora`); nenhum link de navegação para `/fila` no app; produção 404; leitura de `lead_handoffs`/`lead_appointments` responde 200 sem autenticação, com 0 registros no teste (`agenda_slots` expôs 2 horários).
- Relato da cliente em 29/10 (literal): "abrir novamente a fila e abriu, anteriormente estava aparecendo um erro. agora funcionou normalmente".
- Status: ABERTA — erro não reproduzido; por especificação, diagnóstico inconclusivo e task não declarada corrigida. Se recorrer, coletar tela/link, papel, aparelho, passos e mensagem de erro, sem senha.

## Diagnóstico REF-02 — resumo sanitizado (29/10/2026)

- Triagem (Index.tsx, 7 etapas) salva `lead_submissions` + evento `TRIAGEM_CONCLUIDA` (telefone e e-mail no payload do evento) e oferece dois caminhos: WhatsApp externo e "Ver grade de horários" → `/agendar`.
- `/agendar` (Agendar.tsx) não lê a submissão da triagem: o bloco "Seus dados" (nome, canal de retorno, localidade, profissão, e-mail opcional) começa vazio e um NOVO `lead_submission_id` é gerado a cada visita (`useRef(crypto.randomUUID())`).
- Causa estrutural do relato I07: as duas páginas não compartilham estado nem identificador; o lead redigita no fim do agendamento o que já informou na triagem.
- Efeito colateral previsto em B3-03: o agendamento não vincula à submissão da triagem (cobertura incompleta da métrica norte).
- Reteste do operador (29/10 ~15:45): CONFIRMA o defeito — após triagem e escolha de horário, "Seus dados" chega vazio. RED reproduzido; diagnóstico validado.
- Ajuste de mecanismo autorizado no recorte: leitura da submissão por API é impossível sem autenticação (`lead_submissions` responde 403 a anônimo) e abrir essa leitura exigiria mudança de regra de acesso (fora do recorte). O transporte dos dados da triagem para o agendamento será pelo estado de navegação do roteador (mesma sessão de atendimento, sem dados na URL, sem armazenamento), preservando o mesmo `lead_submission_id`. Acesso direto sem triagem mantém o comportamento atual; falha mantém o formulário vazio sem sucesso falso.

- fase_5: planejada, liberar somente pelo ritual após F4
