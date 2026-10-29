# Estado atual — refinamentos

## Direção vigente — confirmação do consultor em 27/10/2026 17:43

Objetivo único das etapas restantes: refinar, validar e concluir a plataforma atual. Executar REF-01 a REF-12, depois os controles locais de qualidade/conversão previstos na fase 4, e finalizar com validação ponta a ponta e encerramento na fase 5. Novo mapeamento somente APÓS concluir a fase 5, em outro processo, sem entrega adicional presumida neste plano.

Não solicitar credenciais, desenhar integrações externas ou inserir escopo de outro sistema nas tasks atuais. Os quatro cards de integração/painel e a subtarefa ficam suspensos, não concluídos, somente para rastreabilidade. Não iniciar nem discutir novo escopo durante os refinamentos. Histórico de decisões não é orientação de execução.

Uma implementação por vez, insumos operacionais perguntados à cliente na própria task, prova técnica e teste humano explícito. Primeira ação: REF-01, diagnóstico da Fila. Prazos a combinar. Nada é marcado concluído por esta atualização documental.

## Controle do orquestrador

- task_id: ce389a55-5a06-4dbe-b3d6-4516d17a0968 (REF-02 — Levar as respostas já preenchidas até o agendamento)
- champion: Karol e Márcio
- spec: 04_fase-atual/specs/spec-4-004-refinamento-formulario-fila-visao.md (seção REF-02)
- etapa: aguardando_autorizacao
- autorizacao_implementacao: ausente
- teste_humano: pendente — reteste de 29/10 REPRODUZIU o defeito (RED confirmado pelo operador): "Seus dados" chega vazio após escolher horário
- verificacao_automatica: passou (diagnóstico 29/10 15:00 + revalidação 15:40; bundle byte-conferido; código publicado mantém formulário vazio e novo lead_submission_id)
- aprendizado: pendente
- ultima_acao: reteste do operador confirmou o defeito I07; diagnóstico REF-02 validado
- proxima_acao: aguardar autorização para implementar o recorte REF-02 (plano já apresentado)
- atualizado_em: 2026-10-29T15:45:00-03:00

## REF-01 — Fila (ABERTA, não corrigida)

- Diagnóstico somente leitura 29/10: `/fila` abre no preview; gate da Fila aceita só `champion`/`consultor` (a Visão aceita também `gestao`/`supervisora`); nenhum link de navegação para `/fila` no app; produção 404; leitura de `lead_handoffs`/`lead_appointments` responde 200 sem autenticação, com 0 registros no teste (`agenda_slots` expôs 2 horários).
- Relato da cliente em 29/10 (literal): "abrir novamente a fila e abriu, anteriormente estava aparecendo um erro. agora funcionou normalmente".
- Status: ABERTA — erro não reproduzido; por especificação, diagnóstico inconclusivo e task não declarada corrigida. Se recorrer, coletar tela/link, papel, aparelho, passos e mensagem de erro, sem senha.

## Diagnóstico REF-02 — resumo sanitizado (29/10/2026)

- Triagem (Index.tsx, 7 etapas) salva `lead_submissions` + evento `TRIAGEM_CONCLUIDA` (telefone e e-mail no payload do evento) e oferece dois caminhos: WhatsApp externo e "Ver grade de horários" → `/agendar`.
- `/agendar` (Agendar.tsx) não lê a submissão da triagem: o bloco "Seus dados" (nome, canal de retorno, localidade, profissão, e-mail opcional) começa vazio e um NOVO `lead_submission_id` é gerado a cada visita (`useRef(crypto.randomUUID())`).
- Causa estrutural do relato I07: as duas páginas não compartilham estado nem identificador; o lead redigita no fim do agendamento o que já informou na triagem.
- Efeito colateral previsto em B3-03: o agendamento não vincula à submissão da triagem (cobertura incompleta da métrica norte).
- Plano mínimo proposto: o link da triagem para `/agendar` carrega o `lead_submission_id`; `/agendar` lê a submissão correspondente, pré-preenche nome/canal/localidade/profissão (e-mail quando disponível) e REUSA o mesmo `lead_submission_id`; sem localStorage; acesso direto sem triagem mantém o comportamento atual; falha de leitura mantém o formulário vazio sem indicar sucesso falso.
- Reteste do operador (29/10 ~15:45): CONFIRMA o defeito — após triagem e escolha de horário, "Seus dados" chega vazio (nome, canal, localidade, profissão, e-mail com placeholder). RED reproduzido; diagnóstico validado. Observação de ambiente: a grade exibe datas de setembro (fixtures), sem efeito neste teste. Persistência entre visitas segue fora do recorte.

- fase_5: planejada, liberar somente pelo ritual após F4
