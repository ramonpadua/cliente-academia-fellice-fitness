# AP-2026-10-29-1610 — Transporte de contexto entre páginas por estado do roteador

- Status: candidato
- Escopo: projeto do cliente (Thor/Fellice — Skip)
- Task/SPEC: REF-02 / SPEC-4-004 (CA-4-R02)
- Sinal: páginas React do mesmo atendimento não compartilham dados; leitura por API é negada a anônimo (403) e abrir leitura pública exigiria mudança de regra de acesso fora do recorte.
- Evidência: implementação v0.0.92 (commit db03c5f) — `navigate('/agendar', {state})` em Index.tsx e leitura validada por `useLocation()` em Agendar.tsx; GREEN 2× e teste negativo no preview; QA Skip OK.
- Regra reutilizável: para levar contexto entre páginas do mesmo atendimento, usar o estado de navegação do roteador (nada na URL, sem localStorage); validar tipos antes de usar; acesso direto sem contexto mantém o comportamento anterior; falha mantém o formulário vazio sem sucesso falso.
- Quando aplicar: fluxos multi-página do mesmo atendimento no Skip Builder quando a leitura por API não está disponível ao papel público.
- Quando não aplicar: persistência entre visitas/sessões (exige decisão de privacidade própria); dados que precisam sobreviver a refresh da página (estado do roteador se perde no recarregamento — documentar como limitação).
- Confiança: alta — provas executadas no ambiente autorizado em 29/10/2026.
- Privacidade: sem segredo, dado pessoal ou conteúdo bruto.
