## Direção vigente — confirmação do consultor em 27/10/2026 17:43

Objetivo único das etapas restantes: refinar, validar e concluir a plataforma atual. Executar REF-01 a REF-12, depois os controles locais de qualidade/conversão previstos na fase 4, e finalizar com validação ponta a ponta e encerramento na fase 5. Novo mapeamento somente APÓS concluir a fase 5, em outro processo, sem entrega adicional presumida neste plano.

Não solicitar credenciais, desenhar integrações externas ou inserir escopo de outro sistema nas tasks atuais. Os quatro cards de integração/painel e a subtarefa ficam suspensos, não concluídos, somente para rastreabilidade. Não iniciar nem discutir novo escopo durante os refinamentos. Histórico de decisões não é orientação de execução.

Uma implementação por vez, insumos operacionais perguntados à cliente na própria task, prova técnica e teste humano explícito. Primeira ação: REF-01, diagnóstico da Fila. Prazos a combinar. Nada é marcado concluído por esta atualização documental.

## Registro histórico da análise da call — não é roteiro ativo

# E-F4-KOMMO-20261027 — recorte atual sem integração Kommo

## Decisão vigente

Ramon orientou em 27/10/2026 às 17:38 analisar a 4ª call alinhamento e ajustar as tasks: “a princípio eles não irão conectar o Kommo mais no sistema deles”. Esta emenda substitui a prioridade anterior de cobrar credenciais/conexão. **Integração suspensa neste recorte, não entregue nem concluída.** Não desconectar contas, apagar dados ou remover histórico.

## Evidência da 4ª call de alinhamento (23/10/2026)

Fonte: https://drive.google.com/file/d/18CygJZRK9T-K-fhkanhPyR_RokXwuIzc/view (consulta 27/10/2026).

- 09:00–09:22: Karol explica a pausa para decidir se usariam Kommo e a intenção de CRM próprio.
- 09:33–13:18: Ramon apresenta alternativas, incluindo adaptar fases para CRM, condicionadas a alinhamento com Isabel e prazo; não é liberação incondicional de construção/migração.
- 18:03–20:29: encaminhamento final: terminar o projeto atual com refinamentos; CRM exige novo detalhamento e conversa com Isabel, possivelmente projeto/adição posterior.
- 21:26–21:31: cliente enviará a lista detalhada de refinamentos, agora recebida e coberta pela SPEC-4-004.

**Interpretação conservadora:** executar os refinamentos e validar o sistema local; suspender conexão externa e suas dependências. Não substituir integração por CRM novo automaticamente. Recorte, prazo e autorização do CRM próprio continuam pendentes do consultor/Isabel. Não há decisão de excluir o Kommo nem migrar seu histórico nesta emenda.

## Impacto no plano

- Suspender quatro cards de contrato/conector e painel da integração, mais a subtarefa de prova do conector. Preservar IDs, não marcar [x], não apagar.
- SPEC-4-001 e SPEC-4-002: contrato histórico preservado, mas sem autorização de execução enquanto esta emenda vigorar. CA-4-001 a CA-4-010 não são aceites satisfeitos: ficam suspensos/fora da cobrança de entrega deste recorte por decisão do consultor. Só nova decisão pode reativá-los.
- SPEC-4-003: manter baseline, alvo e ciclo de conversão, somente com eventos locais da plataforma. Nenhuma credencial, conector, fila externa ou comparação Kommo é pré-condição. Seguem privacidade, acesso autorizado, minimização, cobertura, veredito humano e ausência de escrita externa.
- SPEC-4-004 e 12 tasks de refinamento preservadas. Primeira elegível REF-01. Não cobrar Kommo dentro das novas tasks.
- Fechamento F4: 12 refinamentos + baseline/alvo + loop local + ciclo/recuperação + revisão final. Quatro cards suspensos não contam como realizados. Total 20 cards preservados, 16 elegíveis no recorte vigente, 4 suspensos (subtarefa suspensa fora do denominador). Nenhum concluído pela emenda.
- F5 permanece planejada; na sua liberação, validar o conjunto local e os refinamentos, sem exigir conector suspenso. Não liberar a F5 ou encerrar projeto automaticamente.

## Retomada e segurança

Próxima ação: REF-01, diagnóstico da Fila. Uma implementação por vez; insumos coletados na própria task; prova técnica e teste humano antes de avançar. Só depois dos refinamentos aceitos configurar o loop local, com baseline e alvo aprovados. Publicação de produção continua separada. Se for impossível medir com fontes locais já disponíveis, registrar lacuna e perguntar ao consultor; não inventar dados nem criar CRM para preencher lacuna.
