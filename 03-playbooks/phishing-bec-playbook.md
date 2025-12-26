# Playbook — Phishing & BEC (Business Email Compromise)

Playbook híbrido (tático + executivo) para resposta a incidentes de **phishing** e **BEC**, cobrindo: triagem, contenção, erradicação, recuperação, comunicação e lições aprendidas.

> Escopo: contas corporativas (M365/Google Workspace), apps integrados, MFA, regras de caixa postal, forwarding, acessos suspeitos e tentativa de fraude.

---

## 1) Objetivo e princípios

**Objetivo:** reduzir impacto rápido (fraude / comprometimento), preservar evidências e restaurar confiança na conta/fluxo.  
**Princípios:**
- Agir rápido em contenção (fraude é tempo)
- Preservar evidências antes de “limpar tudo”
- Comunicação curta e clara (stakeholders e usuários)
- Foco em causa raiz (como entrou? por quê bypassou controles?)

---

## 2) Classificação de severidade (guia)

Considere elevar a severidade quando houver:
- **Fraude em andamento** (pagamento/alteração de dados bancários)
- **Conta privilegiada** comprometida (financeiro, RH, admin, executivos)
- **Forwarding/rules maliciosas** + sinais de persistência
- **Acesso anômalo confirmado** (login de país incomum, impossible travel)
- **Impacto amplo** (campanha interna enviada para muitos)

Sugestão:
- **SEV-1:** fraude/exfiltração confirmada, executivo/financeiro comprometido, grande alcance interno
- **SEV-2:** comprometimento provável/confirmado com impacto limitado
- **SEV-3:** tentativa/alerta com evidências limitadas, contido cedo
- **SEV-4:** spam/phishing sem clique, sem impacto

---

## 3) Entrada e triagem (0–30 min)

### 3.1 Sinais comuns (inputs)
- Usuário reporta e-mail suspeito + clique/credencial enviada
- Alertas de “impossible travel”, login suspeito, MFA fatigue
- Regras novas no mailbox (forward, delete, move)
- E-mails enviados em massa “do usuário” sem ele ter enviado
- Solicitação de pagamento/alteração de dados bancários (BEC)

### 3.2 Checklist de triagem (rápido)
- [ ] Quem reportou (usuário / SOC / TI)?
- [ ] Qual conta afetada? (email / UPN)
- [ ] Houve clique? download? credencial digitada?
- [ ] Houve MFA prompt estranho? “MFA fatigue”?
- [ ] Há indícios de login suspeito (localização/IP/device)?
- [ ] Há regras/forwarding/criação de inbox rules?
- [ ] Existe tentativa de fraude (pagamento, dados bancários)?
- [ ] Quantos usuários receberam? (alcance)

### 3.3 Evidências mínimas para coletar (antes de conter)
- Cabeçalhos do e-mail (headers) + subject + remetente
- URL(s) e domínio(s) envolvidos (sem clicar)
- Indicadores: IP de login, user-agent, device, app consentida
- Prints / logs de regras de mailbox e forwarding
- Alertas do SIEM/IdP (se houver)

> Artefatos: abra um ticket usando `02-templates/incident-ticket-template.md`.

---

## 4) Contenção (primeiras ações)

> Prioridade: impedir fraude e impedir persistência.

### 4.1 Ações imediatas (conta suspeita)
- [ ] **Reset de senha** da conta (forçar logout em sessões ativas)
- [ ] **Revogar sessões/tokens** (sign-out global)
- [ ] **Reforçar MFA** (re-registro / reset de MFA se necessário)
- [ ] Bloquear login de locais/condições suspeitas (quando possível)
- [ ] Se conta for privilegiada: revisar rapidamente permissões/grupos

### 4.2 Regras e persistência no mailbox
- [ ] Remover **forwarding** externo e regras suspeitas (delete/move/redirect)
- [ ] Checar delegações (“Send As”, “Send on behalf”) e revogar se indevido
- [ ] Verificar caixas compartilhadas/aliases envolvidos

### 4.3 E-mail malicioso e propagação
- [ ] Quarentenar/remover mensagem da organização (se ferramenta permitir)
- [ ] Bloquear remetente/domínio/URL (secure email gateway/defender/gmail)
- [ ] Identificar usuários que receberam e **notificar** (curto e direto)

### 4.4 Fraude (BEC) — contenção específica
Se houver tentativa de pagamento/alteração bancária:
- [ ] Acionar imediatamente Financeiro/Controladoria
- [ ] Congelar transações relacionadas
- [ ] Validar por canal fora do e-mail (telefone/teams) com fornecedor/cliente
- [ ] Preservar evidências para possível ação legal/forense

---

## 5) Investigação (30 min – 4h)

### 5.1 Perguntas que guiam a investigação
- Como a conta foi comprometida? (phish, password reuse, MFA fatigue, token)
- Quando começou o acesso indevido?
- Houve exfiltração (downloads, mailbox access, regras)?
- Quais dados/processos foram afetados?
- Há outras contas afetadas (mesmo padrão de login/URL)?

### 5.2 Pistas técnicas (alto nível, sem “como invadir”)
- Revisar logs de autenticação (sign-in logs)
- Mapear sessões e apps conectados (OAuth consents suspeitos)
- Verificar criação de regras de inbox e forwarding
- Verificar envios em massa e destinatários
- Verificar alterações em dados de recuperação (telefone, e-mail alternativo)

---

## 6) Erradicação

### 6.1 Medidas definitivas
- [ ] Garantir que credenciais foram trocadas e MFA revalidado
- [ ] Remover regras/persistência e revisar delegações
- [ ] Remover apps/consents suspeitos (quando aplicável)
- [ ] Ajustar políticas (Conditional Access / bloqueio legado / geofence)
- [ ] Treinamento e reforço do usuário afetado (orientação objetiva)

### 6.2 Hardening recomendado (programático)
- Desabilitar autenticação legada (onde aplicável)
- MFA resistente a phishing (quando possível) / reduzir MFA fatigue
- Alertas para criação de forwarding externo e regras suspeitas
- Proteção de domínio (SPF/DKIM/DMARC) e tuning de gateway
- Playbook de “vendor payment change” (processo anti-BEC)

---

## 7) Recuperação

- [ ] Confirmar acesso legítimo do usuário (device conhecido / local esperado)
- [ ] Revalidar apps e integrações (somente as necessárias)
- [ ] Monitorar por 7–14 dias (logins, regras, envios, reset attempts)
- [ ] Se houve fraude: acompanhar chargeback/contato bancário/fornecedor

**Critério de “all clear”:**
- Sem logins suspeitos
- Sem regras/forwarding reaparecendo
- Sem alertas de envio anômalo
- Usuário operando normalmente

---

## 8) Comunicação (executivo + usuários)

### 8.1 Status update (interno)
Use `02-templates/status-update-template.md`. Frequência:
- SEV-1: 30–60 min interno, executivo 2–4h
- SEV-2: 2–4h
- SEV-3: diário ou por marcos

### 8.2 Mensagem curta para usuários (modelo)
> Assunto: Alerta de Phishing  
> Identificamos um e-mail malicioso circulando. Se você clicou em links ou inseriu credenciais, informe imediatamente o time de TI/Segurança.  
> Não interaja com a mensagem e apague-a. Em caso de dúvida, encaminhe para <canal de reporte>.

### 8.3 Comunicação com liderança (modelo)
- O que aconteceu (1–2 linhas)
- Impacto (contas afetadas, fraude sim/não, alcance)
- Ações tomadas (contida? tokens revogados? regras removidas?)
- Próximos passos (investigação e hardening)
- Decisões necessárias (se houver)

---

## 9) Evidências e encerramento

### 9.1 Evidências mínimas para fechar
- Logs de autenticação (início/fim do acesso suspeito)
- Evidência de contenção (revogação de sessão, reset MFA, remoção de regras)
- Lista de destinatários/alcance e ações de comunicação
- Se fraude: evidências de transação e ações de contenção

### 9.2 Encerramento e PIR
- Abrir PIR usando `02-templates/post-incident-review-template.md`
- Registrar:
  - causa raiz
  - controles que falharam
  - plano de ação com owners e datas

---

## 10) Lições aprendidas (checklist)

- [ ] O reporte foi rápido? (usuário/canal funcionou?)
- [ ] Detecção pegou cedo? (alertas e-mail/IdP)
- [ ] MFA/Conditional Access estavam adequados?
- [ ] Processo anti-BEC (mudança de dados bancários) existe e foi seguido?
- [ ] Ações preventivas priorizadas com prazo e owner?

---
