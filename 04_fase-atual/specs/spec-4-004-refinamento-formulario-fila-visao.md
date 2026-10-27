# SPEC-4-004 — Refinamento do formulário, Fila e Visão

## Emenda e autorização

**Emenda E-F4-REF-20261027**, aprovada por Ramon em 27/10/2026 às 17:25: “Aprovo a proposta. Atualize os documentos e publique as novas tasks, preservando as concluídas.” Fonte dos 16 pedidos: documento da cliente `pontos_de_melhoria.docx`, recebido em 27/10/2026; conteúdo operacional transcrito nos contratos abaixo. Proposta de 12 tasks aprovada. Aprovação da documentação não equivale a execução ou aceite de produto.

**Degrau da solução:** correções e incremento determinístico do sistema existente; nenhuma IA nova, CRM novo ou integração nova. Fase 4 atual recebe uma leva residual aditiva. As SPEC-4-001, SPEC-4-002 e SPEC-4-003 e seus oito cards mantêm contrato e bloqueios próprios; fases encerradas e seus aceites permanecem intactos. Esta SPEC é a unidade aditiva: nenhuma SPEC histórica é reescrita para acomodar o pedido.

## Contexto, superfícies e estado desejado

Hoje a cliente relata falha ao abrir Fila, repetição de dados no agendamento, oferta duplicada, conteúdo incorreto e necessidade de evoluir qualificação e operação da Visão. Sintomas não foram reproduzidos nesta emenda. Superfícies conhecidas: Index/formulário, Fila e Visão; o executor identifica o componente/rota real em leitura antes de alterar. Não presumir que a Fila relatada é a futura fila de reconciliação da integração.

Desejado: fluxo coerente com os 16 pedidos, sem quebra de agendamentos, histórico, privacidade ou métricas. O código atual e o banco autorizados no ambiente do cliente são a fonte técnica; esta SPEC não inventa nomes de arquivos, campos ou APIs.

## Atores, permissões e dados

- Champion/cliente: confirma conteúdo, listas de profissão, matriz de perfil, pesos, vídeos e regras de estados; testa cada incremento.
- Maestro do cliente: explica o resultado da task em linguagem simples, coleta os insumos da própria task, apresenta a decisão registrada e só então implementa o recorte.
- Consultor Ramon: aprova alterações que excedam este contrato e revisa o pacote final; não atribuir ao consultor anterior os novos cards.
- Operador e visitante: preservam os papéis já aprovados; esta emenda não amplia acesso. Dados pessoais e gravações de teste são sanitizados; nenhuma credencial em chat/repositório.
- Fonte de verdade: respostas do mesmo atendimento e regras versionadas aprovadas. Histórico anterior conserva versão; sem migração/reclassificação em massa por inferência.

## Regras transversais e execução

1. Novas tasks pendentes; uma implementação ativa por vez. Analisar, mostrar plano, executar provas e obter teste humano explícito antes de avançar. A primeira ação é REF-01 (diagnóstico), depois REF-02; cada dependência específica também se aplica.
2. Coletar insumos dentro da task, com uma pergunta por vez, sem exigir conhecimento de API/banco. Registro humano: decisão literal, autor, data e hora quando disponível; não inventar ausência. Sem insumo, manter aguardando resposta, não adivinhar.
3. Não liberar integração com Kommo, não acessar conta externa por esta emenda, não publicar produção, não alterar dados reais para testar e não alterar cards antigos. Nenhum ciclo/loop é ativado.
4. Score ordena prioridade; elegibilidade decide oferta/reserva. Sem matriz de perfil aprovada, não configurar gate. Profissão não prova renda e não autoriza perfil inferido.
5. Novas opções/regras têm versão e vigência; não recalcular histórico. Rótulos não mudam valores internos nem semântica histórica. Reagendar e Sem perfil têm contrato de transição próprio.
6. Antes de mudar arquitetura, schema, regra de acesso, serviço externo ou migrar dados: detalhar impacto e pedir autorização específica. Não baixar controles de acesso para fazer Fila abrir.
7. Pré-condição técnica desconhecida ou causa não reproduzida exige diagnóstico e ponto de parada; nunca declarar implementação com teste faltante.

## Fluxo de trabalho e rollback

Diagnóstico somente leitura → pergunta operacional à cliente → registrar resposta e plano mínimo → reproduzir RED em teste autorizado → implementar recorte → GREEN e regressão → explicar o que observar → teste humano → evidência e atualização de uma única task.

Rollback: reverter somente alteração do incremento, conservar dados/histórico/reservas e restaurar a versão anterior do fluxo para novos atendimentos. Não apagar dados nem executar rollback de migração destrutiva. Se não houver reversão segura sem perda, parar e apresentar plano ao consultor. Em falha parcial de reagendamento, a reserva anterior não pode ser perdida; não informar sucesso falso.

## Contratos por task e critérios de aceite

Cada seção REF-NN abaixo é contrato obrigatório. CA-4-RNN identifica seu aceite; o recorte de prova é o bloco “Aceite/prova” da mesma seção. Decisões ausentes impedem implementação do recorte, não impedem começar a coleta de insumos.

### REF-01 — Entender e corrigir a abertura da Fila

**Critério CA-4-R01** · Dono: Champion com execução assistida pelo Maestro.

- **Fonte:** F01 — “A opção fila não está abrindo”.
- **Resultado simples:** o usuário autorizado consegue abrir a Fila, inclusive quando vazia, e recebe mensagem útil se houver falha.
- **Começo interativo:** pedir à cliente link/tela exata, login/papel afetado sem senha, aparelho/navegador, passos e mensagem/print do erro. Não confundir a Fila atual com futura fila de integração.
- **Execução:** reproduzir no ambiente autorizado, registrar hipótese e causa demonstrada, corrigir somente a causa. Não conceder acesso amplo para contornar erro.
- **Aceite/prova:** cenário relatado abre com usuário autorizado; estado vazio funciona; usuário sem permissão continua negado na tela e no acesso direto; erro de carregamento não vira tela vazia silenciosa. Cliente repete os passos e confirma.
- **Dependências/parada:** pode iniciar independente da integração e das decisões de pontuação. Sem reprodução, registrar diagnóstico inconclusivo e manter aberta; não declarar corrigida.

### REF-02 — Levar as respostas já preenchidas até o agendamento

**Critério CA-4-R02** · Dono: Champion com execução assistida pelo Maestro.

- **Fonte:** I07.
- **Resultado simples:** os dados já informados aparecem no fim do mesmo atendimento sem precisar digitá-los novamente.
- **Começo interativo:** confirmar com a cliente quais campos sumiram e se o problema ocorre ao avançar, voltar, atualizar página ou reabrir. Persistência entre visitas não está automaticamente incluída.
- **Execução:** diagnosticar o fluxo de dados e reaproveitar as respostas no mesmo atendimento; preservar identificadores/vínculos para não criar lead/agendamento duplicado. Não vazar respostas entre pessoas ou sessões.
- **Aceite/prova:** formulário sintético preenchido → agendamento com os mesmos valores; voltar e corrigir atualiza os valores; nova sessão não herda dados de outro lead; falha não informa gravação bem-sucedida. Teste humano do fluxo completo.
- **Dependências/parada:** prioritária antes de mudanças estruturais no formulário. Política de recarregamento e armazenamento além do atendimento exige confirmação e privacidade, não localStorage por conveniência.

### REF-03 — Atualizar as opções de rotina e a pergunta de profissão

**Critério CA-4-R03** · Dono: Champion com execução assistida pelo Maestro.

- **Fontes:** I01, I02, I03.
- **Resultado simples:** Autônomo e Empresário separados; categorias genéricas saúde/educação/plantonista retiradas do nível solicitado; Executivo ou Gestor exibido como Diretor ou alta gerência; CLT e Autônomo abrem pergunta secundária pertinente.
- **Começo interativo:** mostrar à cliente a lista resultante. Autônomo: advogado, dentista, médico, nutricionista e outros, conforme documento. Perguntar lista CLT e obrigatoriedade da pergunta secundária. Confirmar que retirar as categorias gerais não exclui as profissões explicitamente pedidas como Autônomo. Outros não implica coletar texto livre sem aprovação.
- **Aceite/prova:** cada caminho mostra somente sua pergunta aplicável; trocar a rotina limpa resposta secundária incompatível; categorias e rótulos conferem com a aprovação; versões antigas continuam legíveis. Cliente testa todos os caminhos.
- **Dependências/parada:** REF-02 aceita; lista CLT e regras de obrigatoriedade confirmadas antes da implementação desse recorte. Não inventar profissões.

### REF-04 — Corrigir o endereço e eliminar a oferta duplicada de freepass

**Critério CA-4-R04** · Dono: Champion com execução assistida pelo Maestro.

- **Fontes:** I05, I06.
- **Resultado simples:** endereço correto nas superfícies afetadas e uma oferta coerente, sem repetir o prêmio/freepass indevidamente.
- **Começo interativo:** pedir endereço exato aprovado e em qual momento deve ficar a oferta; esclarecer texto do prêmio final e se é o mesmo benefício. Não escolher endereço por pesquisa pública nem criar nova promessa comercial.
- **Aceite/prova:** endereço conferido nas telas/componentes impactados; percurso completo não duplica a oferta; não remove recurso de acessibilidade ou CTA necessário por engano. Cliente confere texto e momento.
- **Dependências/parada:** definições humanas de conteúdo. Em caso de dependência com elegibilidade, a oferta final respeita REF-06; não concluir antes da prova combinada.

### REF-05 — Criar pontuação de ocupação para priorizar o atendimento

**Critério CA-4-R05** · Dono: Champion com execução assistida pelo Maestro.

- **Fonte:** I10.
- **Resultado simples:** respostas da rotina têm pesos aprovados e a equipe consegue identificar a prioridade resultante.
- **Começo interativo:** pedir pesos por opção, escala, faixas de prioridade, desempate e onde a equipe quer ver a informação. Não inferir pesos de cargo/renda nem criar mapa de calor não solicitado.
- **Execução:** cálculo determinístico e versionado, com valor e motivo rastreáveis; respostas ausentes/inválidas não geram nota favorável inventada. Não ordenar ou repriorizar histórico sem decisão própria.
- **Aceite/prova:** tabela de casos sintéticos com valores esperados aprovada; resultados iguais com mesmas respostas; mudança de resposta atualiza prioridade; ausência de dado sinalizada. Cliente compara os exemplos.
- **Dependências/parada:** REF-03 aceita e matriz de pesos aprovada. Esta task não decide quem pode agendar.

### REF-06 — Mostrar agendamento somente para quem atende às regras de perfil

**Critério CA-4-R06** · Dono: Champion com execução assistida pelo Maestro.

- **Fonte:** I04; relação com I06.
- **Resultado simples:** oferta de aula/agendamento aparece somente aos perfis aprovados pela cliente.
- **Começo interativo:** pedir matriz explícita de respostas que qualifica/desqualifica, tratamento de informações ausentes, exceções e próximo passo de quem não se qualifica. Confirmar se há relação com score e qual seria ela; não presumir um limiar.
- **Execução:** aplicar a regra aprovada nos CTAs e no fluxo/servidor que efetiva nova reserva; apenas esconder botão não comprova bloqueio. Preservar reservas antigas e disponibilidade legítima. Não converter automaticamente todo não qualificado em “Sem perfil” sem regra autorizada.
- **Aceite/prova:** casos qualificado/não qualificado/incompleto; acesso direto à rota e tentativa de gravação não burlam a regra; qualificado ainda consegue concluir normalmente; contadores e capacidade não se alteram com tentativa negada. Teste humano.
- **Dependências/parada:** REF-02/03 aceitas; regra de perfil aprovada. REF-05 só é dependência se a cliente vincular formalmente elegibilidade ao score. Sem regra ou sem acesso ao ponto real de reserva, não declarar gate concluído.

### REF-07 — Inserir os vídeos nas etapas indicadas

**Critério CA-4-R07** · Dono: Champion com execução assistida pelo Maestro.

- **Fontes:** I08, I09.
- **Resultado simples:** vídeo correspondente ao objetivo logo após a pergunta de objetivo; vídeo de diferenciais após a pergunta de rotina.
- **Começo interativo:** pedir links/arquivos autorizados de cada vídeo e associação objetivo→vídeo; confirmar texto de diferenciais e a validade das afirmações “a única”. Confirmar pular/continuar, reprodução e tratamento de objetivo sem vídeo. Não produzir/uploadar vídeos em outro serviço por iniciativa própria.
- **Aceite/prova:** cada objetivo mostra mídia correta; posição após a etapa de rotina validada com a pergunta secundária; móvel/desktop; falha de mídia não perde respostas nem trava o atendimento; nenhum tracking/serviço novo ativado sem aprovação. Cliente percorre os caminhos.
- **Dependências/parada:** REF-02/03 aceitas e mídias/regras confirmadas.

### REF-08 — Usar os novos nomes na Visão sem reescrever o histórico

**Critério CA-4-R08** · Dono: Champion com execução assistida pelo Maestro.

- **Fontes:** V01, V02, V04.
- **Resultado simples:** Tentativas → Em andamento; Concluído → Agendado; Desistência → Sem interesse, nos contextos aprovados.
- **Começo interativo:** mostrar correspondência entre cada rótulo atual e o novo para confirmar o significado, principalmente se “Tentativas” também for título/contador geral.
- **Aceite/prova:** listagem, filtros e contadores coerentes; nenhum valor interno/histórico alterado só por tradução; métricas existentes conservadas. Se semântica de desistência não corresponder a falta de interesse, parar para decisão em vez de trocar nome silenciosamente. Cliente confere.
- **Dependências/parada:** diagnóstico da Visão e mapeamento aprovado; não renomear estados no banco nesta task.

### REF-09 — Acrescentar a ação de reagendar com preservação de vaga e histórico

**Critério CA-4-R09** · Dono: Champion com execução assistida pelo Maestro.

- **Fonte:** V03.
- **Resultado simples:** operador autorizado pode remarcar sem duplicar reservas ou perder o histórico anterior.
- **Começo interativo:** confirmar se Reagendar é botão, estado ou ambos; quem usa, quais estados permitem, prazos, capacidade, liberação da vaga antiga, falha/conflito e tratamento de notificações. Notificação externa não está autorizada por este documento.
- **Aceite/prova:** remarcação válida preserva vínculo e histórico; horário cheio negado; duplo clique não duplica; falha não perde a reserva anterior nem libera/confirma vaga indevidamente; papéis não autorizados negados; métricas diferenciadas sem dupla contagem. Cliente testa.
- **Dependências/parada:** regras humanas e contrato da agenda existente verificados; REF-02 aceita. Se exigir migração de dados/regras, demonstrar plano e pedir autorização específica.

### REF-10 — Acrescentar a classificação Sem perfil

**Critério CA-4-R10** · Dono: Champion com execução assistida pelo Maestro.

- **Fonte:** V05.
- **Resultado simples:** a Visão permite distinguir atendimento sem aderência ao perfil, sem apagar a pessoa ou o histórico.
- **Começo interativo:** confirmar quem classifica, motivo obrigatório ou não, manual/automático, reversibilidade, efeito em fila/agendamento e contabilização. Sem perfil não significa Sem interesse.
- **Aceite/prova:** estados/classificações coexistem com distinção explícita; papéis e transições aprovados; histórico preservado; filtro/contador coerente; reservas existentes não canceladas silenciosamente. Reclassificação demonstrada caso autorizada. Cliente testa.
- **Dependências/parada:** regra de perfil e transições aprovadas; REF-06 se houver classificação automática. Proibido classificar retroativamente todos os leads sem decisão própria.

### REF-11 — Validar o funil completo e a leitura dos indicadores

**Critério CA-4-R11** · Dono: Champion com execução assistida pelo Maestro.

- **Fonte:** regressão decorrente dos 16 pedidos, não nova funcionalidade.
- **Resultado simples:** formulário, vídeos, prioridade, elegibilidade, fila, visão e agenda funcionam juntos sem quebrar entregas anteriores.
- **Aceite/prova:** percursos qualificado/não qualificado/incompleto; mudanças de resposta e retorno entre etapas; sem dados cruzados; sem reservas duplicadas; reagendamento com conflito; Sem perfil distinto de Sem interesse; funil/contadores por versão não reinterpretam histórico; falhas não indicam sucesso falso; testes de acesso negativo.
- **Dependências/parada:** tasks aplicáveis aceitas. Registrar limitações e falhas com dono; não fechar fase automaticamente nem corrigir escopo extra durante a regressão.

### REF-12 — Conferir os refinamentos com a cliente e registrar o aceite

**Critério CA-4-R12** · Dono: Champion com execução assistida pelo Maestro.

- **Fonte:** gate humano da emenda.
- **Resultado simples:** a cliente confirma item a item o que foi entregue e o que permanece pendente.
- **Aceite/prova:** roteiro de 16 pedidos com resultado, evidência sanitizada, versão testada, data e confirmação humana; nenhum item considerado aceito por ausência de reclamação. Publicação permanece autorização separada.
- **Dependências/parada:** REF-11 concluída e revisão do consultor. Esta task não fecha por si só os critérios de integração/loop da F4.

## TDD da SPEC

- **RED:** em ambiente autorizado com dados sintéticos, reproduzir o relato/contrato específico de cada REF-01 a REF-10. Guardar resultado anterior sanitizado; sem reprodução, diagnóstico inconclusivo, sem causa inventada. REF-11/12 verificam integração e aceite, não são correção disfarçada.
- **GREEN:** executar os cenários do bloco “Aceite/prova” de cada REF; registrar entrada, saída esperada, saída obtida, versão e evidência. CA-4-R01 a R12 só passam com prova correspondente e teste humano aplicável. Usar o pipeline de lint/build/test existente no app, identificado por leitura do projeto; não inventar comandos que não existem.
- **REFACTOR/REGRESSÃO:** depois de cada incremento, repetir cenário principal e negativo de acesso/vazamento; ao final executar REF-11, incluindo conflito/idempotência de agenda, navegação direta sem elegibilidade, isolamento de sessão, versão histórica e contagem por etapa.
- **FALHA:** manter task aberta, registrar diagnóstico e repetir o mesmo aceite após reparo. Regressão descoberta fora do recorte precisa decisão própria; não reescrever task concluída.
- **Manual:** cliente percorre cada passo descrito, vê o resultado simples e confirma explicitamente. Silêncio não é aprovação.

## Checklist operacional

- [ ] Conteúdo e decisões da task confirmados sem valores inventados.
- [ ] RED, GREEN e regressão pertinentes executados com evidência sanitizada.
- [ ] Nenhuma ampliação de acesso, exclusão de dados ou publicação indevida.
- [ ] Histórico, reservas, versões e cards antigos preservados.
- [ ] Teste humano explícito antes de marcar a task e avançar.


## Tasks vinculadas

| ID / Referência | Task | Critério | Status |
|---|---|---|---|
| `3c9a7ea2-63fd-4aa5-a370-cdc04e796456` / REF-01 | Entender e corrigir a abertura da Fila | CA-4-R01 | Pendente |
| `ce389a55-5a06-4dbe-b3d6-4516d17a0968` / REF-02 | Levar as respostas já preenchidas até o agendamento | CA-4-R02 | Pendente |
| `d2aebe4c-2a02-48dc-a4fa-3ec1519b2ace` / REF-03 | Atualizar as opções de rotina e a pergunta de profissão | CA-4-R03 | Pendente |
| `cf0687e4-1384-44ba-ae1b-6675124d27f0` / REF-04 | Corrigir o endereço e eliminar a oferta duplicada de freepass | CA-4-R04 | Pendente |
| `547994b2-a335-4fd9-878a-52b67b6c0b60` / REF-05 | Criar pontuação de ocupação para priorizar o atendimento | CA-4-R05 | Pendente |
| `cbd0b8db-f55b-4f4c-93b8-c4bd9fd10e81` / REF-06 | Mostrar agendamento somente para quem atende às regras de perfil | CA-4-R06 | Pendente |
| `0164a633-4026-4270-9b3f-03c09c8fe517` / REF-07 | Inserir os vídeos nas etapas indicadas | CA-4-R07 | Pendente |
| `66178c29-3419-404b-bd88-7801545c751c` / REF-08 | Usar os novos nomes na Visão sem reescrever o histórico | CA-4-R08 | Pendente |
| `ae637215-75a1-44a9-ae07-db0a39745237` / REF-09 | Acrescentar a ação de reagendar com preservação de vaga e histórico | CA-4-R09 | Pendente |
| `25e13c7c-5c61-4503-a2b4-5edc6e4c1c0f` / REF-10 | Acrescentar a classificação Sem perfil | CA-4-R10 | Pendente |
| `f58973d8-dbac-4a9f-8875-21ba4f90384d` / REF-11 | Validar o funil completo e a leitura dos indicadores | CA-4-R11 | Pendente |
| `28a0f522-8e5c-4873-ba85-5c61dcb8ce85` / REF-12 | Conferir os refinamentos com a cliente e registrar o aceite | CA-4-R12 | Pendente |
