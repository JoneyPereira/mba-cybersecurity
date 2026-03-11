# 📋 Checklist de Pré-Auditoria: ISO/IEC 27001:2022

**Objetivo:** Avaliar a conformidade interna com os controlos da norma ISO/IEC 27001:2022 antes da auditoria oficial.
**Mantra do Auditor:** "Se não está documentado e evidenciado, não foi feito."

---

## 🏗️ 1. Controlos Organizacionais (Estratégico)
*Foco na governação, políticas e gestão de ativos.*

- [ ] **Políticas de Segurança:** Existem políticas documentadas, aprovadas pela gestão e comunicadas a todos?
- [ ] **Inventário de Ativos:** Existe uma lista atualizada de todos os ativos de informação (hardware, software, dados)?
- [ ] **Utilização Aceitável:** Todos os utilizadores assinaram um termo de responsabilidade sobre o uso dos recursos da empresa?
- [ ] **Gestão de Fornecedores:** Os contratos com terceiros (Cloud, SaaS) incluem cláusulas de segurança e privacidade?
- [ ] **Gestão de Incidentes:** Existe um processo claro para reportar e tratar incidentes de segurança?

---

## 👥 2. Controlos de Pessoas (Cultura e RH)
*Foco no ciclo de vida do colaborador na empresa.*

- [ ] **Triagem (Screening):** São realizadas verificações de antecedentes para cargos críticos antes da contratação?
- [ ] **Consciencialização e Formação:** Existem evidências (certificados/listas) de que os funcionários receberam formação em cibersegurança?
- [ ] **Processo de Desligamento (Offboarding):** Existe um fluxo para revogar acessos e recolher equipamentos no dia da saída do colaborador?
- [ ] **Trabalho Remoto:** Existem regras claras e controlos aplicados para quem trabalha em regime de Home Office?

---

## 🧱 3. Controlos Físicos (Infraestrutura)
*Foco na proteção do espaço físico e dispositivos móveis.*

- [ ] **Perímetros de Segurança:** As áreas sensíveis (Data Center, salas de rede) possuem controlo de acesso físico (cartões, biometria)?
- [ ] **Segurança de Dispositivos:** Equipamentos deixados em áreas comuns ou fora da empresa possuem proteção contra furto ou acesso indevido?
- [ ] **Eliminação Segura:** Existe um processo para destruir documentos em papel e limpar dados de discos rígidos antigos?
- [ ] **Monitorização Física:** Existem sistemas de vigilância ou registos de entrada/saída de visitantes?

---

## 💻 4. Controlos Tecnológicos (Operacional)
*Foco nas defesas técnicas e resiliência dos sistemas.*

- [ ] **Gestão de Identidades e Acessos (IAM):** É aplicado o Princípio do Privilégio Mínimo? O MFA está ativo para acessos externos e críticos?
- [ ] **Gestão de Vulnerabilidades:** São realizados scans periódicos e existe prova de que os patches de segurança são aplicados?
- [ ] **Backups:** Os backups são realizados conforme a política e, acima de tudo, são testados regularmente para garantir a restauração?
- [ ] **Criptografia:** Os dados sensíveis estão cifrados em repouso (disco/DB) e em trânsito (TLS/SSL)?
- [ ] **Registos (Logging):** Os logs de auditoria estão ativos e protegidos contra alteração?

---

## 📂 Guia de Evidências (O que apresentar ao Auditor)

| Item | Tipo de Evidência |
| :--- | :--- |
| **Políticas** | PDFs assinados digitalmente ou publicados na Intranet. |
| **Backups** | Relatório técnico da última restauração de teste bem-sucedida. |
| **IAM** | Print da consola de gestão (ex: AWS IAM ou Azure AD) mostrando MFA ativo. |
| **Formação** | Lista de presença de workshops ou relatórios de plataforma de e-learning. |
| **Vulnerabilidades** | Relatório de scan (ex: Nessus, OpenVAS) com o plano de ação de correção. |

---

## ⚖️ Avaliação de Risco (Cálculo para Gestão)

Para cada item "Não Conforme" encontrado neste checklist, aplica a fórmula:
**Risco = Probabilidade (1-5) x Impacto (1-5)**

* **Risco 15-25:** Crítico. Requer ação imediata antes da auditoria.
* **Risco 8-12:** Médio. Requer plano de mitigação a curto prazo.
* **Risco 1-6:** Baixo. Pode ser registado como oportunidade de melhoria.