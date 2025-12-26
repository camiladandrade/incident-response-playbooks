# Cadência & Reuniões — Resposta a Incidentes (IR)

Este documento define a **cadência de comunicação**, rituais e reuniões do processo de Resposta a Incidentes (IR), para manter previsibilidade, alinhamento e tomada de decisão rápida.

> Objetivo: garantir coordenação eficiente durante incidentes e disciplina no pós-incidente (PIR).

---

## 1) Visão geral da cadência

- **Durante incidente:** cadência varia conforme severidade (SEV-1 a SEV-4)
- **Após incidente:** PIR (Relatório Pós-Incidente) + plano de ação
- **Rotina preventiva:** exercícios (tabletop) e revisão de playbooks

---

## 2) Cadência durante incidentes (por severidade)

> A cadência abaixo é recomendada. Ajuste conforme impacto, velocidade do evento e necessidade de decisão.

### SEV-1 (Crítico)
**Objetivo:** conter rápido e suportar decisões executivas.
- **Sala de Crise (call):** contínua ou check-ins a cada 30–60 min
- **Atualização tática (time técnico):** a cada **30–60 min**
- **Atualização executiva:** a cada **2–4 horas** (ou por marcos críticos)
- **Revisão de escopo/impacto:** a cada **2–4 horas**

**Gatilhos para aumentar cadência:**
- expansão de escopo
- evidência de exfiltração/fraude
- instabilidade operacional significativa

---

### SEV-2 (Alto)
**Objetivo:** coordenação formal e contenção rápida.
- **Check-in técnico:** a cada **2–4 horas**
- **Atualização executiva:** 1–2 vezes ao dia (ou por marcos)
- **Revisão de bloqueios/decisões:** a cada **4 horas**

---

### SEV-3 (Médio)
**Objetivo:** resolver com disciplina sem “gastar” a organização.
- **Check-in técnico:** diário (ou por marcos)
- **Atualização executiva:** sob demanda ou no encerramento
- **Ponto de controle:** verificar se SEV precisa subir

---

### SEV-4 (Baixo / Evento)
**Objetivo:** registrar, ajustar controles e prevenir recorrência.
- Sem sala de crise
- Atualização sob demanda
- Encerramento com registro simples (e ação preventiva se necessário)

---

## 3) Estrutura da reunião (roteiro padrão)

Para incidentes SEV-1/SEV-2, use esta agenda curta (15–20 min):

1. **Situação atual (fatos)**
2. **Impacto** (C/I/A, serviços, usuários)
3. **Ações desde o último checkpoint**
4. **Próximos passos** (até a próxima atualização)
5. **Bloqueios e decisões necessárias**
6. **Riscos** (reinfecção, exfiltração, fraude, compliance)

> Use o template `02-templates/status-update-template.md` para padronizar.

---

## 4) PIR (Relatório Pós-Incidente) — prazos e ritos

### 4.1 Quando fazer PIR
- **SEV-1:** em até **5 dias úteis**
- **SEV-2:** em até **10 dias úteis**
- **SEV-3:** em até **15 dias úteis** (ou consolidado mensalmente)
- **SEV-4:** opcional (registro simples)

### 4.2 Participantes mínimos
- Comandante do Incidente
- Registrador (linha do tempo)
- Dono do serviço/área afetada
- Representantes técnicos envolvidos (contenção/erradicação/recuperação)
- Jurídico/Privacidade (se aplicável)
- Comunicação (se aplicável)

### 4.3 Saídas obrigatórias do PIR
- Linha do tempo consolidada
- Causa raiz e fatores contribuintes
- O que funcionou / o que não funcionou
- Plano de ação com **owner + prazo + prioridade**
- Melhorias em detecção, prevenção e resposta

> Template recomendado: `02-templates/post-incident-review-template.md`

---

## 5) Rotina preventiva (maturidade do programa)

### 5.1 Exercícios (Tabletop)
- **Trimestral:** 1 tabletop (ex.: ransomware, BEC, vazamento)
- **Semestral:** simulação mais completa (incluindo comunicação e decisão executiva)

**Saídas:**
- gaps identificados
- plano de melhoria
- atualização de playbooks e contatos

### 5.2 Revisão de playbooks e templates
- Revisão **trimestral** dos playbooks críticos
- Revisão **mensal** (rápida) do diretório de contatos, ferramentas e acessos
- Atualização de checklists com base em incidentes reais

---

## 6) Regras de comunicação (boas práticas)

- Evitar especulação: separar **fato** de **hipótese**
- Registrar decisões e justificativas (principalmente em SEV-1)
- Definir um responsável por comunicação (para consistência)
- Preservar evidências antes de mudanças destrutivas (quando possível)

---
