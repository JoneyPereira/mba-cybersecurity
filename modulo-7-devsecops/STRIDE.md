# 📑 Ficha de Consulta Rápida: Metodologia STRIDE

**Conceito:** O STRIDE é uma técnica de modelagem de ameaças que ajuda a identificar o que pode correr mal num sistema, categorizando os riscos com base nas propriedades de segurança que violam.

---

## 🔍 Tabela de Referência STRIDE

| Letra | Ameaça | Propriedade Violada | Definição | Exemplo de Mitigação |
| :--- | :--- | :--- | :--- | :--- |
| **S** | **Spoofing** (Falsificação) | **Autenticidade** | Fingir ser algo ou alguém que não é (usuário, processo, host). | Autenticação Multifator (MFA), Certificados Digitais, Protocolos Seguros (SSH, TLS). |
| **T** | **Tampering** (Adulteração) | **Integridade** | Modificar dados ou código sem autorização em trânsito ou repouso. | Hashing, Assinaturas Digitais, Permissões de Ficheiros, TLS para tráfego. |
| **R** | **Repudiation** (Repúdio) | **Não-repúdio** | Negar a autoria de uma ação por falta de provas técnicas. | Logs de Auditoria protegidos, Assinaturas Digitais, Carimbo de Tempo (Timestamping). |
| **I** | **Information Disclosure** | **Confidencialidade** | Exposição de dados sensíveis a quem não tem permissão. | Criptografia (AES/RSA), Mascaramento de dados, ACLs (Listas de Controlo de Acesso). |
| **D** | **Denial of Service** (DoS) | **Disponibilidade** | Impedir ou degradar o acesso de utilizadores legítimos ao serviço. | Rate Limiting, Firewalls/WAF, Balanceadores de Carga, Redundância de Infraestrutura. |
| **E** | **Elevation of Privilege** | **Autorização** | Obter permissões superiores às que foram originalmente concedidas. | Princípio do Privilégio Mínimo (PoLP), RBAC (Controlo baseado em funções), Sandboxing. |

---

## 🛠️ Como Aplicar no Ciclo DevSecOps (Shift Left)

1. **Decomposição:** Desenha o fluxo de dados do sistema (DFD).
2. **Brainstorming:** Para cada componente (base de dados, API, interface), pergunta: *"Como é que este componente pode sofrer um [Letra do STRIDE]?"*
3. **Priorização:** Usa o risco (Impacto x Probabilidade) para decidir o que corrigir primeiro.
4. **Validação:** Após implementar as mitigações, verifica se a ameaça foi eliminada ou reduzida a um nível aceitável.

---

## 💡 Notas para o MBA: A "Regra de Ouro"

Ao apresentar uma modelagem STRIDE para a administração ou em exames, foca-te sempre no **Impacto de Negócio**:
* **Spoofing/Elevation** -> Roubo de Identidade e Fraude Financeira.
* **Tampering/Repudiation** -> Perda de Confiança e Multas Regulatórias (ex: RGPD/LGPD).
* **Information Disclosure** -> Danos à Reputação e Espionagem Industrial.
* **Denial of Service** -> Perda de Receita e Interrupção Crítica de Operações.