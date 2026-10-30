# AP-2026-10-30-1640 — Lista aprovada pela cliente vale sobre exemplo citado na SPEC

- Status: candidato
- Escopo: projeto do cliente
- Task/SPEC: REF-03 (`d2aebe4c-2a02-48dc-a4fa-3ec1519b2ace`), SPEC-4-004 seção REF-03 (CA-4-R03)
- Sinal: a SPEC citava "nutricionista" como exemplo da lista de Autônomo, mas a lista literal aprovada pela cliente em 29/10/2026 não o incluía; a implementação seguiu a lista aprovada e o estado registrou a divergência com NOTA explícita antes da implementação.
- Evidência: `.adapta-cliente/estado-atual.md` (insumos 3/4 com NOTA sobre nutricionista) e `src/pages/Index.tsx` (PROFISSOES_AUTONOMO sem nutricionista), v0.0.93 commit 9ba9ab8.
- Regra reutilizável: quando a SPEC citar exemplo e a resposta literal da cliente divergir, a lista aprovada na task prevalece; registrar a divergência no estado antes de implementar, nunca resolver por inferência.
- Quando aplicar: coleta de insumos operacionais (listas, rótulos, textos) em qualquer REF/task com começo interativo.
- Quando não aplicar: quando a cliente revisar a própria lista depois do registro; aí vale a revisão mais recente, também registrada.
- Confiança: alta — divergência documentada em duas fontes do repositório e resolvida sem retrabalho.
- Privacidade: sem segredo, dado pessoal ou conteúdo bruto.
