# AP-2026-11-06-1030 — Ressalva de teste vale como insumo antecipado da task seguinte

- Status: candidato
- Escopo: projeto do cliente
- Task/SPEC: REF-04 (`cf0687e4-1384-44ba-ae1b-6675124d27f0`), SPEC-4-004 seção REF-04 (CA-4-R04); relação com REF-06 (CA-4-R06)
- Sinal: no teste humano da REF-04, o operador aprovou ("o teste está ok") e registrou ressalva: "o prêmio está disponível para todos, independente da triagem, a triagem é feita para qualificar o perfil do nosso cliente" — exatamente o recorte que a REF-04 deixou para a REF-06 (elegibilidade por perfil), conforme a SPEC ("a oferta final respeita REF-06; não concluir antes da prova combinada").
- Evidência: mensagem do Ricardo em 06/11/2026 10:28 registrada no estado; recorte acordado nos insumos 2/3 (06/11 10:09) com NOTA de dependência da REF-06.
- Regra reutilizável: ressalva de teste que aponta recorte já acordado não reabre a task — registra-se como insumo antecipado da task seguinte, com a frase literal e data, antes de concluir a task atual.
- Quando aplicar: fechamento de task com teste aprovado e observação que pertence a outra task do mesmo plano.
- Quando não aplicar: se a ressalva indicar falha no que a task prometia (critério não atendido) — aí a task volta para debug, não é concluída.
- Confiança: alta — recorte documentado nos insumos da própria task e na SPEC antes da implementação.
- Privacidade: sem segredo, dado pessoal ou conteúdo bruto.
