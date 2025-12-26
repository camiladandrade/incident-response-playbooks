# Incident Response Lifecycle — Ciclo de IR (end-to-end)

Este documento descreve o ciclo de Resposta a Incidentes (IR) e os entregáveis mínimos esperados em cada etapa.

## 1) Objetivos do IR
- Conter impacto rapidamente e preservar disponibilidade quando possível
- Reduzir risco de recorrência (erradicação real, não “apagar incêndio”)
- Garantir evidências e rastreabilidade (timeline, decisões, artefatos)
- Comunicação adequada (tático, executivo e stakeholders)

---

## 2) Etapas do ciclo

### 2.1 Preparação
**Entregáveis:** contatos, papéis, canais, checklists, playbooks, acesso a logs e ferramentas.

### 2.2 Detecção e triagem
**Meta:** confirmar se é incidente, classificar severidade e acionar times.  
**Entregáveis:** ticket do incidente, classificação inicial, hipóteses e próximos passos.

### 2.3 Contenção
**Meta:** interromper propagação e reduzir risco imediato.  
**Entregáveis:** ações de contenção registradas + impacto/risco + critérios de rollback.

### 2.4 Erradicação
**Meta:** remover causa raiz (malware, backdoor, credenciais comprometidas, configuração insegura).  
**Entregáveis:** ações definitivas + evidências + medidas para evitar reentrada.

### 2.5 Recuperação
**Meta:** restaurar operação com segurança e monitorar recaída.  
**Entregáveis:** validações pós-recovery, monitoração reforçada, critérios de “all clear”.

### 2.6 Pós-incidente (PIR / Lessons Learned)
**Meta:** consolidar timeline, impacto, falhas de controle e plano de ação.  
**Entregáveis:** PIR completo + plano de melhoria com owners e datas.

---

## 3) Artefatos obrigatórios
- Ticket do incidente + timeline
- Registro de decisões (por quê cada ação foi tomada)
- Evidências-chave (logs, hashes, alertas, prints)
- Status updates (executivo e técnico)
- PIR + plano de melhorias
