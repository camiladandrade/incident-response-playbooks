# Playbook — Ransomware (Hybrid: Técnico + Executivo)

Playbook híbrido para resposta a incidentes de **ransomware**, cobrindo: triagem, contenção, erradicação, recuperação, comunicação e lições aprendidas.

> Objetivo: **conter propagação rápido**, preservar evidências, reduzir impacto operacional e restaurar serviços com segurança (sem reinfecção).

---

## 1) Sinais e gatilhos de ativação

### 1.1 Sinais comuns
- Arquivos criptografados / extensão alterada / ransom note
- Aumento anômalo de operações de escrita/renomeação
- Alertas EDR/XDR (mass encryption, suspicious PowerShell, lateral movement)
- Falhas de login em massa, uso de credenciais privilegiadas fora do padrão
- Serviços críticos indisponíveis (AD, file servers, VMs, backups)

### 1.2 Ativar como incidente de ransomware quando:
- Criptografia confirmada **ou**
- Evidência forte de tentativa em andamento (EDR bloqueando) **ou**
- Backups/infra de recuperação foram afetados

**Severidade sugerida:** normalmente **SEV-1** (ou SEV-2 se contido cedo e sem impacto).

---

## 2) Primeiros 15 minutos (ação decisiva)

> Prioridade: **parar a propagação** e proteger AD/credenciais/backups.

### 2.1 Setup rápido
- [ ] Abrir ticket `02-templates/incident-ticket-template.md`
- [ ] Definir IR Lead + Scribe/Timeline Owner
- [ ] Ativar War Room com `04-checklists/war-room-checklist.md`

### 2.2 Contenção imediata (sem esperar investigação completa)
- [ ] Isolar hosts comprometidos (rede) / quarentena EDR
- [ ] Desabilitar contas suspeitas / reset de credenciais privilegiadas
- [ ] Bloquear IOCs conhecidos (domínios/IPs/hashes) nos controles disponíveis
- [ ] Avaliar desligar compartilhamentos críticos (SMB) temporariamente, se necessário
- [ ] Suspender tarefas agendadas/serviços suspeitos identificados

> Nota: decisões que derrubam serviço amplo devem ser registradas com “por quê” no ticket.

---

## 3) Preservação de evidências (antes de “limpar”)

Coletar o mínimo viável:
- Logs do EDR/XDR (alertas, árvore de processos, host timeline)
- Identificação do(s) host(s) “patient zero” e hora mais antiga
- Amostras/artefatos: ransom note, extensão, nome do executável (sem executar)
- Logs de autenticação (AD/IdP): picos, privilégios, contas usadas
- Evidências de movimentação lateral (SMB/RDP/WMI/WinRM, conforme logs disponíveis)
- Estado de backup (último backup bom, integridade, alcance do impacto)

---

## 4) Triagem e escopo (30–90 min)

### 4.1 Confirmar escopo
- Quais hosts/servidores foram criptografados?
- Qual porcentagem/criticidade (Tier-0/Tier-1)?
- Sistemas de identidade (AD/IdP) foram comprometidos?
- Backups foram tocados? (apagados, criptografados, inacessíveis)

### 4.2 Identificar vetor provável (alto nível)
- Phishing/credenciais
- RDP exposto / password spraying
- Vulnerabilidade em serviço exposto
- Acesso de terceiro/fornecedor
- Ferramentas de administração remota abusadas

> Importante: não precisa saber “tudo” para conter; mas precisa saber o suficiente para evitar reinfecção na recuperação.

---

## 5) Contenção detalhada (objetivo: parar propagação)

### 5.1 Rede e segmentação
- [ ] Bloquear tráfego lateral suspeito (onde possível)
- [ ] Segmentar/isolamento de sub-redes afetadas (se necessário)
- [ ] Bloquear comunicações de C2 (domínios/IPs) conhecidos

### 5.2 Identidade e privilégios (prioridade alta)
- [ ] Reset de credenciais privilegiadas (admin, service accounts críticas)
- [ ] Invalidar sessões/tokens (IdP)
- [ ] Revisar contas recém-criadas, grupos alterados, delegações
- [ ] Suspender contas com comportamento anômalo

### 5.3 Backups e recuperação
- [ ] Isolar infraestrutura de backup (evitar contaminação)
- [ ] Confirmar existência de backup “limpo” (ponto no tempo)
- [ ] Proteger repositórios (imutabilidade quando aplicável)
- [ ] Registrar estado e risco de restauração

---

## 6) Erradicação (remover causa raiz)

### 6.1 Objetivos
- Remover persistência
- Eliminar ferramenta inicial (malware, backdoor, conta comprometida)
- Corrigir controle/porta/vulnerabilidade que permitiu entrada
- Garantir que o ambiente recuperado não reinfecte

### 6.2 Ações típicas (sem detalhar exploração)
- [ ] Remover artefatos maliciosos (via EDR/forense, conforme capacidade)
- [ ] Reimage/rebuild de hosts comprometidos quando necessário
- [ ] Patching/hardening de serviços expostos/credenciais fracas
- [ ] Revisar GPOs e políticas alteradas (ambiente Windows)
- [ ] Remover ferramentas de administração indevidas/“living off the land” abusadas (quando identificado)

---

## 7) Recuperação (restaurar com segurança)

### 7.1 Estratégia de recuperação (priorização)
Defina ordem por criticidade:
1. **Identidade** (AD/IdP, MFA, DNS)
2. **Rede e acesso**
3. **Serviços Tier-0/Tier-1**
4. **Dados e file shares**
5. **Sistemas auxiliares**

### 7.2 Regras para restaurar
- Restaurar **somente** após confirmar contenção e erradicação suficientes
- Validar integridade do backup (anti-malware/EDR scan em restaurados)
- Reintroduzir sistemas por fases (monitorar sinais de reinfecção)
- Documentar cada restore: origem, horário, validação

### 7.3 Critérios de “all clear”
- Sem detecções ativas no EDR/XDR
- Sem logins suspeitos e sem alterações anômalas em AD/IdP
- Sistemas restaurados operando e monitorados por 7–14 dias
- Controles reforçados aplicados (hardening e privilégios)

---

## 8) Comunicação (executivo, áreas, jurídico)

### 8.1 Status updates
Usar `02-templates/status-update-template.md`.

Cadência sugerida:
- **SEV-1:** interno 30–60 min; executivo a cada 2–4h
- **SEV-2:** 2–4h

### 8.2 Conteúdo mínimo para liderança
- O que aconteceu (fato)
- Impacto (quais serviços/dados, indisponibilidade)
- Status (contido? em erradicação? recuperação?)
- Riscos (reinfecção, backups, identidade)
- Decisões necessárias (prioridade de restauração, recursos, comunicação externa)

### 8.3 Jurídico/Privacidade/Compliance
Acionar quando:
- evidência/forte suspeita de exfiltração
- dados pessoais/sensíveis afetados
- obrigação contratual/regulatória de notificação

---

## 9) Pagamento de resgate (posicionamento e governança)

Este playbook **não recomenda** pagamento como ação padrão.
Caso a organização considere essa possibilidade:
- a decisão deve ser **executiva**, documentada, com jurídico/risco envolvidos
- preservar evidências e manter trilha de decisão (por quê, alternativas, impactos)

> O foco aqui é resposta e recuperação com segurança.

---

## 10) Evidências mínimas para encerramento

- Timeline completa no ticket
- Lista de sistemas afetados e restaurados
- Evidências de contenção (isolamentos, bloqueios, resets)
- Evidências de erradicação (rebuild, remoção, hardening)
- Relatório de recuperação (o que voltou, quando e como validou)
- PIR completo com plano de ação (`02-templates/post-incident-review-template.md`)

---

## 11) Pós-incidente (PIR) — lições e melhorias

Checklist de melhorias comuns:
- MFA e políticas de acesso (Conditional Access / Zero Trust)
- Privilégios mínimos e revisão de contas privilegiadas
- Segmentação de rede e restrições laterais
- Observabilidade (logs e alertas úteis)
- Resiliência de backup (imutabilidade, testes de restore)
- Exercícios tabletop e runbooks atualizados

---
