# AP-2026-11-06-1710 — Prioridade em toda coleção que a tela lê (e badge defensivo)

- Status: candidato
- Escopo: projeto do cliente (Thor/Fellice — Skip)
- Task/SPEC: REF-05 / SPEC-4-004 (CA-4-R05)
- Sinal: a Fila exibia tudo "Baixa · 0" e depois vazia/sem nota, embora o cálculo estivesse correto na triagem.
- Evidência: três falhas encadeadas provadas por logs e leitura autenticada da API — (1) gravação com spread (`...prioridade`, chaves nota/faixa/...) ignorada pelo PocketBase porque os campos reais se chamam prioridade_*; (2) a migração 0060 criou os campos em lead_submissions e lead_appointments mas não em lead_handoffs, a coleção que a Fila lê; (3) number vazio volta 0 e select vazio volta "", que o fallback `??` não pega — badge "Baixa · 0". Fix v0.0.96 (campos explícitos nos 4 pontos de gravação + `!p.faixa` no rótulo) e 0062 (campos em lead_handoffs); teste humano aprovado com "Alta · 9" na Fila e registro no banco (nota 9, faixa alta, matriz v1).
- Regra reutilizável: um campo novo existe em TODA coleção que alguma tela lê — mapear as coleções de leitura antes da migração, não só as de escrita; gravar sempre com os nomes reais dos campos (nunca spread de objeto com chaves abreviadas); tratar select vazio como "" e number vazio como 0 no fallback do rótulo (`!p.faixa`), porque o PocketBase não devolve null/undefined.
- Quando aplicar: qualquer REF que acrescente campo calculado exibido em mais de uma tela (Fila, Visão, Funil, Dashboard).
- Quando não aplicar: campo usado só na própria página que o calcula, sem persistência.
- Confiança: alta — causa demonstrada por logs (POST 200 com gravação ignorada) e leitura autenticada antes/depois do fix, 06/11/2026.
- Privacidade: sem segredo, dado pessoal ou conteúdo bruto.
