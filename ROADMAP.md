# 🗺️ ROADMAP — Incident Response Playbooks (IR)

Este roadmap organiza as entregas do repositório em **milestones** para construir um conjunto de artefatos de **Resposta a Incidentes** com foco em **liderança**, **governança operável**, **evidências** e **decisão executiva**.

📌 Objetivo do repositório:
Demonstrar como estruturar e operar IR ponta a ponta:
**detecção/análise → contenção → erradicação → recuperação → lições aprendidas**, com templates e playbooks reutilizáveis e prontos para auditoria.

---

## ✅ Definição de pronto (Definition of Done)

Uma entrega está “pronta” quando:
- Está em **PT-BR**, clara e aplicável em ambiente corporativo.
- Tem **objetivo + quando usar + inputs/outputs** no topo.
- Inclui **papéis/owners** quando aplicável.
- Contém **exemplo fictício** (mínimo: modelo preenchido OU evidência simulada).
- Evita instruções ofensivas (foco em defesa, coordenação e resposta).
- Está **linkada** no README raiz e no README da pasta correspondente.

---

## 🧱 M0 — Repo Product Ready (higiene + navegação)
**Objetivo:** repo com cara de produto (navegável e rastreável).

### Entregas
- [x] `ROADMAP.md` (este arquivo)
- [x] `CHANGELOG.md`
- [x] `LICENSE` (MIT ou CC BY 4.0)
- [x] `DISCLAIMERS.md`
- [x] README raiz com Quick Start + links válidos
- [ ] Padronizar READMEs por pasta (01–05)

### Pacote de commits sugerido
- `chore: add roadmap, changelog, license and disclaimers`
- `docs: update root README quickstart + repo map`
- `docs: standardize folder readmes`

---

## 🧭 M1 — Operating Model de IR (governança real + severidade + evidências)
**Objetivo:** provar liderança e auditabilidade.

### Entregas (01-framework/)
- [ ] Revisar e fortalecer:
  - [ ] `ir-lifecycle.md`
  - [ ] `severity-and-escalation.md`
  - [ ] `roles-and-raci.md`
  - [ ] `cadence-and-meetings.md`
- [ ] Adicionar:
  - [ ] `incident-classification-and-triage.md`
  - [ ] `evidence-handling-and-chain-of-custody.md`
  - [ ] `communications-governance.md`

### Pacote de commits sugerido
- `docs: harden IR lifecycle, severity and RACI for auditability`
- `docs: add incident triage/classification guide`
- `docs: add evidence handling + communications governance`

---

## 🧩 M2 — Templates ponta a ponta (coordenação + executivo + PIR)
**Objetivo:** execução repetível, comunicação e melhoria contínua.

### Entregas (02-templates/)
- [ ] Revisar:
  - [ ] `incident-ticket-template.md`
  - [ ] `status-update-template.md`
  - [ ] `post-incident-review-template.md`
- [ ] Adicionar:
  - [ ] `incident-timeline-template.md`
  - [ ] `executive-brief-1pager-template.md`
  - [ ] `stakeholder-communication-template.md`
  - [ ] `legal-hold-and-notification-checklist.md` (alto nível)
  - [ ] `lessons-learned-backlog-template.md`

### Pacote de commits sugerido
- `templates: upgrade incident ticket + status update + PIR templates`
- `templates: add timeline + executive brief + stakeholder comms`
- `templates: add lessons learned backlog + legal hold checklist (high-level)`

---

## ⚡ M3 — Checklists de execução (war room + primeira hora + decisões)
**Objetivo:** reduzir caos e acelerar decisões.

### Entregas (04-checklists/)
- [ ] Revisar:
  - [ ] `war-room-checklist.md`
- [ ] Adicionar:
  - [ ] `first-60-minutes-checklist.md`
  - [ ] `containment-decision-checklist.md`
  - [ ] `executive-update-checklist.md`
  - [ ] `evidence-minimum-checklist.md`

### Pacote de commits sugerido
- `checklists: refine war room checklist + add first 60 minutes checklist`
- `checklists: add containment decision + exec update + evidence minimum`

---

## 🧯 M4 — Playbooks por cenário (core + suportes)
**Objetivo:** cobertura dos incidentes mais prováveis.

### Entregas (03-playbooks/)
- [ ] Padronizar estrutura dos playbooks existentes
- [ ] Adicionar playbooks:
  - [ ] `credential-compromise-playbook.md`
  - [ ] `data-leak-suspected-playbook.md`
  - [ ] `malware-endpoint-playbook.md`
  - [ ] `saas-incident-playbook.md`
  - [ ] `ddos-availability-playbook.md`
  - [ ] `third-party-incident-playbook.md`

### Pacote de commits sugerido
- `playbooks: standardize playbook structure (phases, evidence, comms)`
- `playbooks: add credential compromise + data leak suspected`
- `playbooks: add malware endpoint + saas incident`
- `playbooks: add ddos + third-party incident`

---

## 🧾 M5 — Evidence Pack de IR (audit readiness)
**Objetivo:** responder e provar (evidências organizadas).

### Entregas (criar 06-evidence-pack/)
- [ ] `06-evidence-pack/README.md`
- [ ] `06-evidence-pack/evidence-pack-structure.md`
- [ ] `06-evidence-pack/evidence-tracker.csv`
- [ ] `06-evidence-pack/sample-evidence/`
  - [ ] `sample-incident-timeline.md`
  - [ ] `sample-exec-brief.md`
  - [ ] `sample-status-updates.md`
  - [ ] `sample-closure-report.md`

### Pacote de commits sugerido
- `docs: add IR evidence pack structure + tracker`
- `docs: add fictional sample evidence artifacts`

---

## 📊 M6 — Métricas de IR + reporting executivo
**Objetivo:** linguagem de liderança (tendência, impacto, tempos, reincidência).

### Entregas (criar 07-metrics/)
- [ ] `07-metrics/ir-kpi-kri-catalog.md`
- [ ] `07-metrics/ir-thresholds-and-triggers.md`
- [ ] `07-metrics/monthly-ir-exec-report-template.md`
- [ ] `07-metrics/monthly-ir-exec-report-example-filled.md` (fictício)
- [ ] `07-metrics/metrics-governance.md`

### Pacote de commits sugerido
- `docs: add IR KPI/KRI catalog + thresholds`
- `templates: add monthly IR exec report template + filled example`
- `docs: add IR metrics governance`

---

## 🗂️ M7 — Case Studies (3 casos fictícios “pasta de entrevista”)
**Objetivo:** prova final com decisões, evidências, comunicação e PIR.

### Entregas (05-case-studies/)
- [ ] `05-case-studies/README.md` (template padrão)
- [ ] `case-01-phishing-bec/`
- [ ] `case-02-ransomware/`
- [ ] `case-03-credential-compromise-saas/`

**Formato padrão**
- `contexto.md`
- `deteccao-e-triagem.md`
- `linha-do-tempo.md`
- `decisoes-e-trade-offs.md`
- `comunicacao.md`
- `evidencias.md`
- `pos-incidente-pir.md`
- `resultado-e-metricas.md`

### Pacote de commits sugerido
- `cases: add case study template structure`
- `cases: add case 01 (phishing/BEC) with evidence artifacts`
- `cases: add case 02 (ransomware) with comms + recovery`
- `cases: add case 03 (credential compromise + SaaS) with PIR`
