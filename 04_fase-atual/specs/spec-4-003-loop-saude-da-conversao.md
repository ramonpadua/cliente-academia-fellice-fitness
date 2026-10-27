# SPEC-4-003 — Loop de saúde da conversão (loop adicional da Fase 4)

## Direção vigente — confirmação do consultor em 27/10/2026 17:43

Objetivo único das etapas restantes: refinar, validar e concluir a plataforma atual. Executar REF-01 a REF-12, depois os controles locais de qualidade/conversão previstos na fase 4, e finalizar com validação ponta a ponta e encerramento na fase 5. Novo mapeamento somente APÓS concluir a fase 5, em outro processo, sem entrega adicional presumida neste plano.

Não solicitar credenciais, desenhar integrações externas ou inserir escopo de outro sistema nas tasks atuais. Os quatro cards de integração/painel e a subtarefa ficam suspensos, não concluídos, somente para rastreabilidade. Não iniciar nem discutir novo escopo durante os refinamentos. Histórico de decisões não é orientação de execução.

Uma implementação por vez, insumos operacionais perguntados à cliente na própria task, prova técnica e teste humano explícito. Primeira ação: REF-01, diagnóstico da Fila. Prazos a combinar. Nada é marcado concluído por esta atualização documental.

**Status vigente: AJUSTADA para conversão LOCAL.** Esta seção substitui as dependências e fontes externas do texto histórico abaixo:

- Fonte: somente eventos locais autorizados das fases anteriores e novos refinamentos; não consumir estado de Kommo/Lovable ou fila/conector externo.
- Pré-condições: REF-01 a REF-12 aceitas, baseline B4-04 congelado por versão/fórmula/período/cobertura e alvo aprovado. Removida a dependência “integração configurada”. Não recalcular histórico ou misturar versões sem explicitar cobertura.
- Privacidade: manter base legal e papéis autorizados para dados locais; B4-01 na parte de autorização de escrita externa não é gate. Dado insuficiente ou sem autorização interrompe análise.
- CA-4-011/012/013 preservados. CA-4-014 vigente: falha da fonte/medição LOCAL interrompe recomendações e abre pendência com responsável. Nenhuma credencial ou teste de conector é solicitado.
- TDD local RED: ausência de registro de ciclo; GREEN: baseline e 2 ciclos sintéticos completos (cobertura, achado, veredito), sem ação externa; REGRESSÃO: fonte local indisponível ou cobertura insuficiente interrompe recomendações, alvo/veredito ausente não libera ação, escrita externa recusada. Prova humana mantém gate.
- Fechamento: CA-4-011 a CA-4-014 locais + CA-4-R01 a R12, sem cobrar CA-4-001 a CA-4-010 suspensos. Veredito do consultor em task de fechamento. Suspensão não é conclusão.

## Tasks vinculadas — projeção vigente

| Task | Critério | Pré-condição | Status |
|---|---|---|---|
| Congelar baseline e aprovar alvo | B4-04 + alvo | versão/fórmula/cobertura, decisão Champion/Gestão | Pendente |
| `31dae29a-884a-4ac6-a23a-2cfc5b0e56a8` Configurar loop local | CA-4-011 a 014 locais | baseline/alvo e REF-01 a REF-12 aceitas | Pendente |
| `12bf95df-e79a-4ef2-b4f1-214fc65c3cbb` Ciclo/recuperação local | CA-4-011/014 locais | loop aceito | Pendente |
| `c5ccd038-0cae-4e1d-9d72-52e2d3ef935d` Revisão final Ramon | CA locais + CA-4-R01 a R12 | refinamentos e ciclo local aceitos | Pendente |


## Contrato anterior — histórico, subordinado à vigência acima

**Fase:** 4
**Status:** SPEC aprovada pelo consultor em 30/09/2026 ("libero todas as specs, pode executar"); tasks geradas. O loop não é ativado em produção por esta SPEC.

**Dono:** Champion do cliente (decisor de B4-04 e do alvo); Gestão aprova o alvo junto com o Champion
**Origem:** Loop adicional "Saúde da conversão" da Fase 4 do escopo definitivo; EV-F3-02 (B4-04)
**Degrau:** ciclo de revisão semanal que produz diagnóstico e sugere experimento com veredito humano; nenhum assistente ou agente altera formulário, regra, campanha ou integração.

**Gate atual:** tasks de baseline/alvo, configuração do loop e ciclo de prova liberadas na Jornada da Fase 4; execução uma por vez com teste humano.

## Contexto e resultado

A Fase 3 entregou o dashboard e o critério de baseline, mas nenhum ciclo de revisão opera sobre eles. O resultado desejado é um ciclo semanal de saúde da conversão que registra baseline, cobertura, achado e veredito humano, melhorando com decisão humana a conversão de lead para agendamento sem reduzir a cobertura de atribuição.

## BLOQUEIOS executáveis

| Bloqueio | Dono | Evidência para liberar |
|---|---|---|
| B4-04 — baseline operacional congelado (proposta EV-F3-02 — validar) | Champion | Versão de baseline congelada com numerador, denominador, período, cobertura e versão, conforme critério B3-05 (o loop define "Baseline: valor congelado na fase 3") |
| Alvo quantitativo do ciclo | Champion + Gestão | Alvo numérico aprovado e registrado antes da ativação do loop; nenhum alvo é inferido |
| B4-01 — base legal/consentimento LGPD (proposta EV-F3-01 — validar) | Champion | Necessário antes de analisar dado real de lead |

## Limites, dados e permissões

Definição do loop (escopo definitivo, Fase 4):

| Elemento | Definição |
|---|---|
| Meta por ciclo | Melhorar, com decisão humana, a conversão de lead para agendamento sem reduzir a cobertura de atribuição. |
| Baseline | Valor congelado na fase 3 (B4-04 — ainda não congelado). |
| Alvo | Quantitativo aprovado pelo Champion e Gestão antes da ativação do loop. |
| Cadência e fonte | Revisão semanal com eventos da plataforma e estado da integração. |
| Assistente/agentes candidatos | Assistente de análise; agente de qualidade de dados somente se conector e permissões forem validados. |
| Autonomia | Produz diagnóstico e sugere experimento; não altera formulário, regra, campanha ou integração sem aprovação humana. |
| Recuperação | Falha de medição ou conector interrompe recomendações e abre pendência para o responsável. |

Ficam fora: publicação de formulário, mudança de campanha, alteração de integração, aprovação de resultado e qualquer escrita externa pelo loop ou agente.

## Fluxo de execução

1. Champion congela o baseline operacional (B4-04) e registra o alvo aprovado com Gestão (insumos embutidos na task de baseline/alvo).
2. Executor implementa o ciclo semanal sobre eventos da plataforma e estado da integração, com registro de baseline, cobertura, achado e campo de veredito humano.
3. Assistente de análise prepara diagnóstico e sugestão de experimento; nenhuma ação é executada sem veredito.
4. Teste humano do Champion; aceite formal em task separada; ativação somente após autorização explícita.

## Critérios de aceite

- **CA-4-011:** o ciclo semanal registra baseline, cobertura, achado e veredito humano; sem veredito, nenhuma recomendação vira ação.
- **CA-4-012:** o alvo quantitativo só é considerado ativo depois de aprovado por Champion e Gestão, com registro de data.
- **CA-4-013:** loop e assistente não alteram formulário, regra, campanha ou integração (prova negativa: nenhuma escrita externa).
- **CA-4-014:** falha de medição ou conector interrompe recomendações e abre pendência para o responsável.

## TDD da SPEC

- **RED:** hoje não existe ciclo de revisão; conversão é observada sem diagnóstico registrado, sem veredito e sem baseline congelado.
- **GREEN:** fixture com baseline congelado e 2 ciclos sintéticos produz registros completos (baseline, cobertura, achado, veredito) e sugestão de experimento sem efeito externo.
- **REGRESSÃO:** ausência de veredito bloqueia ação; falha de fonte interrompe recomendação e abre pendência; tentativa de escrita externa pelo assistente é recusada; alvo não aprovado mantém loop inativo.

Evidências: registro dos ciclos, aprovação do alvo, provas negativas de escrita e aceite humano.

## Tasks vinculadas

| ID | Task | Critério | Pré-condição |
|---|---|---|---|
| id pendente | Congelar o baseline e aprovar o alvo do loop | B4-04 + alvo | decisões Champion+Gestão |
| `31dae29a-884a-4ac6-a23a-2cfc5b0e56a8` | Configurar o loop de saúde da conversão | CA-4-011..014 | baseline congelado + alvo aprovado |
| `12bf95df-e79a-4ef2-b4f1-214fc65c3cbb` | Executar um ciclo e provar recuperação | CA-4-011/014 (regressão) | loop configurado |
| `c5ccd038-0cae-4e1d-9d72-52e2d3ef935d` | Revisar os ciclos e decidir o fechamento da Fase 4 | CA-4-001..014 | tasks anteriores concluídas |
