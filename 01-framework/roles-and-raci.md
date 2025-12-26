# Papéis & RACI — Resposta a Incidentes (IR)

Este documento define **papéis** e a matriz **RACI** para Resposta a Incidentes, garantindo clareza de responsabilidade, rapidez nas decisões e rastreabilidade.

> Objetivo: evitar “zona cinzenta” durante incidentes, acelerar contenção e reduzir retrabalho.

---

## 1) Papéis (definições)

### Líder de Resposta a Incidentes (Comandante do Incidente)
**Responsável final** pela condução do incidente. Define prioridades, coordena frentes, remove bloqueios e garante comunicação.  
**Entregas:** direção tática, decisões registradas, atualizações de status, encerramento e Relatório Pós-Incidente.

### Registrador / Responsável pela Linha do Tempo
**Responsável** por registrar a linha do tempo, decisões, ações e evidências no ticket.  
**Entregas:** linha do tempo “alta fidelidade”, registro de decisões, evidências linkadas.

### Analista de Detecção (SOC) *(quando aplicável)*
Responsável por alertas, correlação inicial, indicadores e apoio à investigação.  
**Entregas:** resumo da detecção, indicadores, hipóteses e recomendações.

### Líder de Investigação (Forense / Caça a Ameaças)
Coordena a investigação técnica e a confirmação do escopo.  
**Entregas:** escopo, hipótese de vetor, evidências técnicas e recomendações de erradicação.

### Líder de Contenção (Infraestrutura / SRE / Redes)
Coordena contenção e ações imediatas para interromper propagação/abuso.  
**Entregas:** isolamentos, bloqueios, revogações, mudanças emergenciais com evidência.

### Líder de Erradicação (Infra / AppSec / Endpoints)
Coordena a remoção da causa raiz e persistência.  
**Entregas:** correções definitivas (patch/hardening/reimagem), validações e evidências.

### Líder de Recuperação (Continuidade / DR / Operações)
Coordena recuperação, restabelecimento e monitoramento pós-recuperação.  
**Entregas:** plano de restauração, critérios de “liberação”, validações e monitoramento reforçado.

### Operações de TI / Plataforma / SRE
Execução de mudanças e operação de ambientes, automações, retorno (rollback).  
**Entregas:** execução de mudanças, restauração, acessos e suporte a logs/ferramentas.

### Dono do Serviço (Dono do Ativo/Aplicação)
Dono do impacto do serviço e da priorização do negócio. Apoia decisões de trade-off.  
**Entregas:** priorização de recuperação, validação funcional do serviço, apoio à comunicação.

### Responsável por Comunicação (Interna/Externa)
Prepara mensagens para usuários, liderança, clientes e terceiros sob direção do Comandante do Incidente e alinhamento com Jurídico/Privacidade.  
**Entregas:** rascunhos/aprovações, consistência do discurso e alinhamento de stakeholders.

### Jurídico / Privacidade (LGPD)
Avalia obrigações legais, risco regulatório e necessidade de notificação.  
**Entregas:** direcionamento legal, requisitos de preservação, suporte em notificações.

### Responsável por Fornecedores/Terceiros
Coordena contato com fornecedores (cloud, MSSP, EDR, e-mail) e terceiros afetados.  
**Entregas:** abertura de chamados, escalonamento, coleta de evidências externas.

### Patrocinador Executivo (CISO / Diretor / Head)
Patrocina decisões críticas (derrubar serviços, comunicação externa, recursos).  
**Entregas:** decisões executivas e remoção de bloqueios.

---

## 2) RACI (matriz)

Legenda:
- **R** = Responsável (executa)
- **A** = Aprovador / Responsável final (dono do resultado)
- **C** = Consultado
- **I** = Informado

| Atividade | Comandante do Incidente | Registrador (Linha do Tempo) | Detecção (SOC) | Investigação | Contenção | Erradicação | Recuperação | Operações TI/SRE | Dono do Serviço | Comunicação | Jurídico/Privacidade | Fornecedores/Terceiros | Patrocinador Executivo |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Classificar severidade e abrir incidente | A | R | C | C | C | I | I | I | C | I | I | I | I |
| Ativar sala de crise e cadência | A | R | I | I | I | I | I | I | I | I | I | I | I |
| Preservar evidências (mínimo) | A | R | C | R | C | C | I | C | I | I | C | C | I |
| Contenção imediata (parar propagação) | A | I | C | C | R | C | C | R | C | I | I | C | I |
| Investigação e definição de escopo | A | C | R | R | C | C | I | C | C | I | I | C | I |
| Decisões de trade-off (disponibilidade vs risco) | A | I | C | C | C | C | C | C | R/C | I | C | I | A/C |
| Erradicação (causa raiz) | A | I | C | R | C | R | C | R | C | I | I | C | I |
| Recuperação e validação do serviço | A | I | I | C | C | C | R | R | R/C | I | I | C | I |
| Comunicação interna (usuários/gestão) | A | I | I | I | I | I | I | I | C | R | C | I | I |
| Comunicação externa / notificação | A | I | I | I | I | I | I | I | C | R | A | C | A/C |
| Atualizações de status (tático e executivo) | A | R | C | C | C | C | C | I | I | C | C | I | I |
| Encerramento e “liberação” | A | R | C | C | C | C | C | C | C | I | C | I | I |
| Relatório Pós-Incidente e lições aprendidas | A | R | C | R | C | C | C | C | C | C | C | I | I |

> Nota: em times menores, alguns papéis podem ser acumulados (ex.: Comandante do Incidente + Investigação).

---

## 3) Regras práticas (para incidentes severos)

- Sempre existe **um Comandante do Incidente** e **um Registrador**.
- Ações de alto impacto (derrubar serviços amplos, comunicação externa) devem ter **decisão registrada**.
- Evidências mínimas devem ser coletadas **antes** de mudanças destrutivas (quando possível).
- Encerrar incidente apenas quando:
  - ameaça contida,
  - plano de erradicação/recuperação definido,
  - critérios de “liberação” estabelecidos,
  - Relatório Pós-Incidente agendado.

---
