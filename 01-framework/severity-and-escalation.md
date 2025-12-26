# Severity & Escalation — Classificação e escalonamento

Este documento define severidade (SEV) e gatilhos de escalonamento para IR.

## 1) Dimensões usadas
- Impacto em **Disponibilidade** (down/instabilidade)
- Impacto em **Confidencialidade** (exfiltração/dados sensíveis)
- Impacto em **Integridade** (fraude/alteração indevida)
- **Escopo** (quantos sistemas/usuários)
- **Exposição** (internet-facing, tier-0)
- **Obrigação legal/compliance** (LGPD, contratos, regulatório)

---

## 2) Matriz simplificada

### SEV-1 (Crítico)
- Ransomware ativo, exfiltração confirmada, tier-0 comprometido, fraude em andamento, indisponibilidade ampla
- **Ação:** war room imediato + updates frequentes + sponsor/c-level informado

### SEV-2 (Alto)
- Comprometimento provável com impacto limitado, credenciais privilegiadas vazadas, incidente em sistema crítico sem evidência de exfiltração
- **Ação:** coordenação formal + contenção rápida + update regular

### SEV-3 (Médio)
- Incidente contido, impacto limitado, sem sinais de propagação
- **Ação:** resposta padrão + investigação e correções

### SEV-4 (Baixo)
- Evento/alerta com baixo impacto (ou quase-incidente)
- **Ação:** registrar, ajustar detecção e prevenir recorrência

---

## 3) Cadência de comunicação (sugestão)
- SEV-1: update a cada **30–60 min** (interno) + executivo a cada **2–4h**
- SEV-2: update a cada **2–4h**
- SEV-3: update diário (ou por marcos)
- SEV-4: update sob demanda

---

## 4) Escalonamento
Escalonar quando:
- Impacto aumenta (SEV sobe)
- Bloqueio operacional impede contenção
- Há risco legal/reputacional
- Há evidência de exfiltração/fraude
