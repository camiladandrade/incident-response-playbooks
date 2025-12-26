# War Room Checklist — SEV-1 / SEV-2 (Incident Response)

Checklist rápido (10–20 min) para iniciar e conduzir um **War Room** em incidentes SEV-1/SEV-2 com clareza, rastreabilidade e boa comunicação.

> Objetivo: alinhar pessoas, decisões e evidências. Evitar caos, duplicidade e “ações sem dono”.

---

## 0) Abertura (primeiros 5 minutos)

### 0.1 Criar o registro do incidente
- [ ] Abrir ticket usando `02-templates/incident-ticket-template.md`
- [ ] Definir **Incident ID** e **SEV inicial** (1 ou 2)
- [ ] Definir **IR Lead (A)** e **Scribe/Timeline Owner (R)**

### 0.2 Estabelecer canais
- [ ] Canal de chat dedicado (War Room)
- [ ] Bridge/Call (se SEV-1)
- [ ] Pasta/drive para evidências (restrita)

### 0.3 Definir cadência de comunicação
- [ ] Próximo status update em: ___ min
- [ ] Quem recebe update executivo: ______________________

---

## 1) Alinhamento de situação (5–10 minutos)

### 1.1 “O que sabemos” (fatos)
- [ ] O que aconteceu (1–2 frases)?
- [ ] Quando começou? (timestamp mais antigo conhecido)
- [ ] Quais sistemas/usuários/serviços afetados?
- [ ] Impacto em C/I/A (Confidencialidade/Integridade/Disponibilidade)
- [ ] Há dados sensíveis/PII envolvidos? (potencial LGPD)

### 1.2 “O que não sabemos” (lacunas)
- [ ] Vetor de entrada?
- [ ] Extensão/escopo real?
- [ ] Exfiltração? fraude? persistência?
- [ ] Incidente ainda ativo?

> Regra: separar **fato** de **hipótese** no ticket.

---

## 2) Decisões críticas (primeiros 15 minutos)

### 2.1 Prioridade do momento (selecionar)
- [ ] Conter propagação
- [ ] Proteger dados/credenciais
- [ ] Restaurar serviço crítico
- [ ] Preservar evidências (antes de mudanças destrutivas)

### 2.2 Ações “permitidas” sem aprovação adicional
Defina o que pode ser feito imediatamente (exemplos):
- [ ] Isolar host/conta comprometida
- [ ] Revogar sessões/tokens
- [ ] Bloquear IOC/domínio/URL
- [ ] Reset de credenciais e MFA
- [ ] Desativar integrações suspeitas

### 2.3 Ações que exigem aprovação (Change / risco operacional)
- [ ] Derrubar serviço / bloquear tráfego amplo
- [ ] Alterações em produção com risco alto
- [ ] Restores/rollbacks em massa
- [ ] Comunicação externa

**Aprovador:** ______________________

---

## 3) Evidências (preservação mínima)

> Antes de “limpar”, preserve o suficiente para investigar.

- [ ] Registrar timestamps (início e principais marcos)
- [ ] Guardar logs-chave (IdP, e-mail, endpoint, firewall, SIEM)
- [ ] Salvar IOCs (IPs, domínios, hashes, usuários, processos)
- [ ] Capturar prints e outputs relevantes
- [ ] Se aplicável: snapshot/forense (conforme capacidade)

**Dono das evidências:** ______________________

---

## 4) Delegação e execução (RACI na prática)

### 4.1 Definir frentes de trabalho (com dono)
- [ ] **Containment Lead:** ______________________
- [ ] **Investigation Lead:** ______________________
- [ ] **Recovery Lead:** ______________________
- [ ] **Comms Lead (interno/executivo):** ______________________
- [ ] **Legal/Privacy Liaison (se necessário):** ______________________

### 4.2 Criar lista de ações (com prazos)
- [ ] Cada ação tem **owner + prazo + evidência**
- [ ] Atualizar no ticket (tabela de ações)

---

## 5) Comunicação (executivo e stakeholders)

### 5.1 Status update padrão (usar template)
- [ ] Preparar update usando `02-templates/status-update-template.md`
- [ ] Confirmar:
  - Situação atual (fato)
  - Impacto
  - Ações tomadas
  - Próximos passos
  - Bloqueios / decisões necessárias

### 5.2 Pontos de decisão executiva (se houver)
- [ ] Aceitar risco temporário para manter serviço?
- [ ] Congelar mudanças / ativar change freeze?
- [ ] Acionar fornecedor/terceiro?
- [ ] Acionar jurídico/privacidade?

---

## 6) Critérios de saída do War Room

Encerrar War Room quando:
- [ ] A ameaça está **contida** (sem atividade maliciosa em andamento)
- [ ] Há plano claro de erradicação/recuperação com owners
- [ ] Cadência de updates definida até “all clear”
- [ ] Evidências mínimas preservadas e registradas

---

## 7) Pós-incidente (garantir que vai acontecer)

- [ ] Agendar PIR (Post-Incident Review) em até ___ dias
- [ ] Abrir PIR usando `02-templates/post-incident-review-template.md`
- [ ] Criar backlog de melhorias (owners + prazos)

---
