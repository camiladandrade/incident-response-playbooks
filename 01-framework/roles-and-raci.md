# Roles & RACI — Incident Response (IR)

Este documento define **papéis** e a matriz **RACI** para Resposta a Incidentes, garantindo clareza de responsabilidade, rapidez nas decisões e rastreabilidade.

> Objetivo: evitar “zona cinzenta” durante incidentes, acelerar contenção e reduzir retrabalho.

---

## 1) Papéis (definições)

### IR Lead (Incident Commander)
**Accountable** pela condução do incidente. Decide prioridades, coordena frentes, remove bloqueios e garante comunicação.  
**Entregas:** direção tática, decisões registradas, status updates, encerramento e PIR.

### Scribe / Timeline Owner
**Responsible** por registrar timeline, decisões, ações e evidências no ticket.  
**Entregas:** timeline “alta fidelidade”, ata curta de decisões, evidências linkadas.

### SOC / Detection Analyst (quando aplicável)
Responsável por alertas, correlação inicial, IOCs e apoio à investigação.  
**Entregas:** resumo de detecção, indicadores, hipóteses e recomendações.

### Investigation Lead (Forense / Threat Hunting)
Coordena investigação técnica e confirmação de escopo.  
**Entregas:** escopo, hipótese de vetor, evidência técnica e recomendações de erradicação.

### Containment Lead (Infra/SRE/Network)
Coordena contenção e ações imediatas para interromper propagação/abuso.  
**Entregas:** isolamentos, bloqueios, revogações, mudanças emergenciais com evidência.

### Eradication Lead (Infra/AppSec/Endpoints)
Coordena remoção de causa raiz e persistência.  
**Entregas:** correções definitivas (patch/hardening/reimage), validações e evidências.

### Recovery Lead (BCP/DR / Operações)
Coordena recuperação, restabelecimento e monitoramento pós-recovery.  
**Entregas:** plano de restore, critérios de “all clear”, validações e monitoramento reforçado.

### IT Ops / Platform / SRE
Execução de mudanças e operação de ambientes, pipelines, rollback.  
**Entregas:** change execution, restore, acesso a logs e ferramentas.

### Application Owner / Service Owner (Dono do serviço)
Dono do impacto do serviço e priorização do negócio. Ajuda em decisões de trade-off.  
**Entregas:** priorização de recovery, validação funcional do serviço, apoio à comunicação.

### Comms Lead (Comunicação interna/externa)
Responsável por preparar mensagens (usuários, liderança, clientes, terceiros) sob direção do IR Lead e alinhamento com Legal/Privacy.  
**Entregas:** drafts e aprovações, consistência do messaging.

### Legal / Privacy (LGPD/GDPR)
Avalia obrigações legais, risco regulatório e necessidade de notificação.  
**Entregas:** direcionamento legal, requisitos de preservação, suporte em notificação.

### Vendor / Third-Party Liaison
Coordena contato com fornecedores (cloud, MSSP, EDR, e-mail) e terceiros afetados.  
**Entregas:** abertura de chamados, escalonamento, coleta de evidências externas.

### Executive Sponsor (CISO/Head/Dir)
Patrocina decisões críticas (down de serviços, comunicação externa, recursos).  
**Entregas:** decisões executivas e remoção de bloqueios.

---

## 2) RACI (matriz)

Legenda:
- **R** = Responsible (executa)
- **A** = Accountable (dono / responde pelo resultado)
- **C** = Consulted (consulta)
- **I** = Informed (informado)

| Atividade | IR Lead | Scribe | SOC/Detect | Invest Lead | Contain Lead | Eradicate Lead | Recovery Lead | IT Ops/SRE | Service Owner | Comms | Legal/Privacy | Vendor Liaison | Sponsor |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Classificar SEV e abrir incidente | A | R | C | C | C | I | I | I | C | I | I | I | I |
| Ativar War Room e cadência | A | R | I | I | I | I | I | I | I | I | I | I | I |
| Preservar evidências (mínimo) | A | R | C | R | C | C | I | C | I | I | C | C | I |
| Contenção imediata (stop the bleeding) | A | I | C | C | R | C | C | R | C | I | I | C | I |
| Investigação e definição de escopo | A | C | R | R | C | C | I | C | C | I | I | C | I |
| Decisões de trade-off (down vs risco) | A | I | C | C | C | C | C | C | R/C | I | C | I | A/C |
| Erradicação (causa raiz) | A | I | C | R | C | R | C | R | C | I | I | C | I |
| Recuperação e validação do serviço | A | I | I | C | C | C | R | R | R/C | I | I | C | I |
| Comunicação interna (usuários/gestão) | A | I | I | I | I | I | I | I | C | R | C | I | I |
| Comunicação externa / notificação | A | I | I | I | I | I | I | I | C | R | A | C | A/C |
| Status updates (tático e executivo) | A | R | C | C | C | C | C | I | I | C | C | I | I |
| Encerramento e “all clear” | A | R | C | C | C | C | C | C | C | I | C | I | I |
| PIR / lições aprendidas | A | R | C | R | C | C | C | C | C | C | C | I | I |

> Nota: em times menores, papéis podem acumular (ex.: IR Lead + Investigation Lead).

---

## 3) Regras práticas (para incidentes SEV-1/2)

- Sempre existe **um IR Lead** e **um Scribe** (sem isso, vira caos).
- Ações de alto impacto (derrubar serviços amplos, comunicação externa) devem ter **decisão registrada**.
- Evidências mínimas devem ser coletadas **antes** de mudanças destrutivas (quando possível).
- Encerrar incidente só com:
  - ameaça contida
  - plano de erradicação/recuperação completo
  - critérios de “all clear” definidos
  - PIR agendado

---
