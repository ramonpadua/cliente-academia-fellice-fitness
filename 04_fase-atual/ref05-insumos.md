# REF-05 — Análise e insumos (task 547994b2-a335-4fd9-878a-52b67b6c0b60)

## Análise REF-05 — resumo sanitizado (06/11/2026, somente leitura)

- Fonte das respostas: `lead_submissions.ocupacao` (select com as 7 opções aprovadas na REF-03 — migração 0059); respostas antigas anteriores à REF-03 têm valores de rótulo (texto puro) e não estão na lista nova.
- Recorte da SPEC: pesos aprovados pela cliente; cálculo determinístico e versionado, com valor e motivo rastreáveis; respostas ausentes/inválidas não geram nota favorável inventada; não ordenar/repriorizar histórico sem decisão própria; esta task NÃO decide quem pode agendar (elegibilidade é REF-06; score só entra lá se a cliente vincular formalmente).
- Superfícies de exibição candidatas: Fila (`/fila`, Queue.tsx — gate champion/consultor) e Visão (`/visao`, Visao.tsx — gate champion/consultor/gestao/supervisora); onde a equipe quer ver é insumo.
- Persistência candidata: campo(s) novo(s) em `lead_submissions` (valor + versão da matriz + motivo) via migração 0060 — decisões de estrutura só após insumos e autorização.
- Nada alterado nesta etapa; a SPEC proíbe inferir pesos de cargo/renda e criar mapa de calor não solicitado.

## Insumos REF-05 — recebidos do consultor (06/11/2026)

- **Insumo 1/3 — escala e pesos (respostas literais do formulário da task):** escala 0–10; Profissional CLT = 5; Autônomo = 6; Empresário = 7; Diretor ou alta gerência = 9; Estudante = 7; Aposentado = 7; Prefiro não informar = 5.
- Observação registrada: "Prefiro não informar" recebeu peso explícito 5 — decisão do consultor; é distinta do tratamento de resposta AUSENTE/inválida (a definir no insumo 2).
- Observação para o insumo 2 (não é decisão): com esses pesos, se as faixas forem Alta ≥8 / Média 5–7 / Baixa 0–4, nenhuma resposta da lista cai em Baixa — apenas resposta ausente com nota 0.
- **Insumo 2/3 — faixas, desempate e ausentes (respostas literais do formulário da task):** Alta = nota ≥ 7; Baixa = nota ≤ 5 (entre eles, Média); desempate = ordem de chegada (mais antigo primeiro); resposta ausente/inválida = nota 0, cai em Baixa e exibe "Sem pontuação".
- Efeito das faixas aprovadas sobre os pesos do insumo 1: Alta = Diretor ou alta gerência (9), Empresário (7), Estudante (7), Aposentado (7); Média = Autônomo (6); Baixa = CLT (5), Prefiro não informar (5) e resposta ausente (0).
- **Sub-insumo 2b — aberto pelo consultor (observação literal):** "as sub perguntas da triagem, dos itens clt, autonomo e o que mais tiver, precisa ter peso também" — cada profissão da pergunta secundária precisa de peso próprio; listas literais a extrair do código; coleta pendente.
- Listas literais extraídas do código (Index.tsx v1.1.1, working tree Skip, 06/11/2026): PROFISSOES_CLT = Assistente administrativo, Vendedor, Técnico de enfermagem, Médico, Engenheiro, Outros; PROFISSOES_AUTONOMO = Cabeleireiro, Eletricista, Advogado, Dentista, Médico, Outros. Somente CLT e Autônomo têm pergunta secundária; "Outros" abre texto livre (campo `profissao`).
- **Sub-insumo 2b — pesos por profissão (respostas literais do formulário da task):** regra de combinação = peso da profissão SUBSTITUI o da ocupação; CLT — Assistente administrativo 5, Vendedor 4, Técnico de enfermagem 5, Médico 8, Engenheiro 8, Outros 6; Autônomo — Cabeleireiro 5, Eletricista 4, Advogado 8, Dentista 7, Médico 8, Outros 6.
- Efeito com as faixas do insumo 2 (Alta ≥7, Baixa ≤5): Alta = CLT Médico (8), CLT Engenheiro (8), Autônomo Advogado (8), Autônomo Dentista (7), Autônomo Médico (8); Média = Outros de CLT e Autônomo (6); Baixa = CLT Assistente administrativo (5), CLT Vendedor (4), CLT Técnico de enfermagem (5), Autônomo Cabeleireiro (5), Autônomo Eletricista (4).
- **Insumo 3/3 — exibição (respostas literais do formulário da task):** prioridade aparece NA FILA E NA VISÃO; a Fila REORDENA por prioridade (Alta primeiro; empate = mais antigo primeiro); cada lead mostra FAIXA + NOTA (ex.: "Alta · 8").
