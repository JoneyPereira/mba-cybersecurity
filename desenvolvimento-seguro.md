# 🛡️ Desenvolvimento Seguro — Mapa Mental

## 🔐 Desenvolvimento Seguro
Práticas e processos para projetar, desenvolver e manter sistemas protegidos contra ameaças e vulnerabilidades.

---

## 1️⃣ Vulnerabilidades Comuns em Aplicações Web

### 🌐 Conceito
Falhas de segurança em aplicações web que podem ser exploradas por atacantes para:
- Acesso não autorizado
- Vazamento de dados
- Comprometimento do sistema

📌 Referência principal: **OWASP Top 10**

---

### 💉 SQL Injection
- Injeção de comandos SQL maliciosos
- Explora falhas na validação de entradas

**Impactos**
- Vazamento de dados
- Alteração/exclusão de registros
- Escalada de privilégios

**Mitigações**
- Prepared Statements
- ORM
- Validação e sanitização de entradas
- Princípio do menor privilégio

---

### 🧨 XSS (Cross-Site Scripting)
- Execução de scripts maliciosos no navegador da vítima

**Tipos**
- Stored
- Reflected
- DOM-based

**Impactos**
- Roubo de sessão
- Phishing
- Manipulação de páginas

**Mitigações**
- Escape de saída
- Content Security Policy (CSP)
- Validação de entradas

---

### 🔄 CSRF (Cross-Site Request Forgery)
- Força o usuário autenticado a executar ações indesejadas

**Impactos**
- Transferências indevidas
- Alteração de dados

**Mitigações**
- CSRF Tokens
- SameSite Cookies
- Verificação de origem (Origin/Referer)

---

### 🔎 Avaliação de Segurança
- SAST (Análise Estática)
- DAST (Análise Dinâmica)
- Pentest
- Code Review
- Análise baseada no OWASP

---

## 2️⃣ Metodologias e Frameworks de Segurança

### 🧪 PTES
- Metodologia de Pentest
- Fases bem definidas:
  - Planejamento
  - Coleta de informações
  - Análise de vulnerabilidades
  - Exploração
  - Pós-exploração
  - Relatório

📌 Foco: **Testes de intrusão**

---

### 📘 NIST 800-155
- Guia para segurança de firmware
- Aplicado a:
  - Hardware
  - Sistemas embarcados
  - Cadeia de suprimentos

📌 Foco: **Integridade e confiança do firmware**

---

### 🧭 OSSTMM
- Metodologia científica de testes de segurança
- Avalia:
  - Pessoas
  - Processos
  - Tecnologia
  - Canais físicos e lógicos

📌 Foco: **Mensuração objetiva da segurança**

---

### 📊 CVSS
- Sistema de pontuação de vulnerabilidades
- Escala: 0.0 a 10.0

**Classificação**
- Baixa
- Média
- Alta
- Crítica

📌 Foco: **Priorização de correções**

---

### 🛠️ ISSAF
- Framework prático de segurança
- Baseado em procedimentos e checklists

📌 Foco: **Execução operacional de testes**

---

### 🕸️ OWASP
- Comunidade e framework de segurança
- Destaque:
  - OWASP Top 10
  - ASVS
  - OWASP Testing Guide

📌 Foco: **Segurança de aplicações web e APIs**

---

## 3️⃣ Estratégia Antifraude em Cibersegurança

### 🚨 Conceito
Conjunto de práticas para prevenir, detectar e responder a fraudes digitais.

---

### 🔍 Técnicas de Detecção e Prevenção
- Regras de negócio
- Análise comportamental
- Geolocalização
- Fingerprint de dispositivos
- Monitoramento em tempo real

---

### 🤖 Uso de IA e Machine Learning
- Detecção de padrões anômalos
- Score de risco
- Modelos preditivos

📌 Aplicação comum:
- Fintechs
- Bancos
- E-commerce

---

### 🛡️ Controles de Segurança
- MFA
- Limites de transação
- Alertas automáticos
- Logs e auditoria
- Bloqueio adaptativo

---

### 📈 Avaliação da Eficiência
- Taxa de falsos positivos
- Redução de perdas financeiras
- Tempo de resposta
- Impacto na experiência do usuário

---

## 4️⃣ Plano de Gestão de Incidentes

### 🚑 Importância
- Redução de impactos
- Resposta rápida e organizada
- Conformidade legal (ex: LGPD)

---

### 🧱 Etapas do Plano (Modelo NIST)

1. **Preparação**
2. **Identificação**
3. **Contenção**
4. **Erradicação**
5. **Recuperação**
6. **Lições Aprendidas**

---

### 🛠️ Resposta e Mitigação
- Isolamento de sistemas
- Revogação de acessos
- Aplicação de patches
- Comunicação interna e externa
- Preservação de evidências

---

### 🔁 Melhoria Contínua
- Simulações de incidentes
- Revisão de processos
- Atualização de playbooks
- Treinamento das equipes

---

📌 **Resumo Final**
- Desenvolvimento Seguro = Tecnologia + Processos + Pessoas
- Prevenção é mais barata que resposta
- Segurança deve estar integrada ao ciclo de desenvolvimento (SDLC)
