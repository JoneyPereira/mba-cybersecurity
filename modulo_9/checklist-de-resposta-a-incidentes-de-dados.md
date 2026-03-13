# 🚨 Checklist de Resposta a Incidentes de Dados (Foco LGPD)

**Objetivo:** Sistematizar a reação da organização diante de um incidente com dados pessoais para cumprir as obrigações legais perante a ANPD e os titulares.

---

## 🕒 Fase 1: Identificação e Triagem (Primeiras 24h)
- [ ] **Confirmar o Incidente:** Trata-se de uma violação de dados pessoais (acesso não autorizado, destruição, perda, alteração ou comunicação indevida)?
- [ ] **Acionar o Comitê de Crise:** Notificar o DPO (Encarregado), CISO, Jurídico e Comunicação.
- [ ] **Registro Interno:** Iniciar o log de cronologia do incidente (o que foi descoberto, por quem e a que horas).
- [ ] **Identificar o Tipo de Dado:** São dados comuns ou **Dados Sensíveis** (origem racial, saúde, biometria, convicção religiosa, etc.)?

---

## 🛠️ Fase 2: Contenção e Erradicação
- [ ] **Bloqueio de Acessos:** Revogar credenciais comprometidas ou isolar servidores afetados.
- [ ] **Preservação de Provas:** Garantir que logs e evidências forenses não sejam apagados durante a recuperação.
- [ ] **Análise de Causa Raiz:** Identificar como o dado vazou (falha técnica, erro humano ou ataque externo).

---

## 📊 Fase 3: Avaliação de Risco (Análise de Impacto)
- [ ] **Volume de Dados:** Quantos titulares foram afetados?
- [ ] **Gravidade:** Há risco de danos morais ou materiais (fraudes financeiras, roubo de identidade, discriminação)?
- [ ] **Critério de Notificação:** O incidente pode acarretar **risco ou dano relevante** aos titulares? 
    * *Nota: Se sim, a notificação à ANPD torna-se obrigatória.*

---

## 📢 Fase 4: Notificação (Prazo sugerido pela ANPD: 2 dias úteis)
### Comunicação à ANPD:
- [ ] Descrição da natureza dos dados pessoais afetados.
- [ ] Informações sobre os titulares envolvidos.
- [ ] Medidas técnicas e de segurança utilizadas para a proteção (ex: estavam criptografados?).
- [ ] Riscos relacionados ao incidente.
- [ ] Medidas que foram ou serão adotadas para reverter ou mitigar os efeitos.

### Comunicação aos Titulares (Linguagem Simples):
- [ ] Informar o que aconteceu de forma clara.
- [ ] Orientar o titular sobre como ele pode se proteger (ex: trocar senhas, monitorar extratos).
- [ ] Fornecer o contato do DPO para dúvidas.

---

## 📉 Fase 5: Pós-Incidente (Lições Aprendidas)
- [ ] **Atualizar o Inventário de Dados:** O fluxo de dados mudou após a correção?
- [ ] **Revisar o RIPD:** O Relatório de Impacto à Proteção de Dados precisa ser atualizado com as novas medidas de mitigação?
- [ ] **Relatório Final:** Documentar todas as ações tomadas para fins de auditoria futura e demonstração de boa-fé.

---

## 💡 Notas de Gestão (MBA Insights)
* **Diferença de Papéis:** Se a sua empresa é a **Operadora** (trata dados em nome de outra), você deve notificar o **Controlador** imediatamente. A obrigação de falar com a ANPD é, primariamente, do Controlador.
* **Segurança como Mitigante:** Se os dados vazados estavam anonimizados ou criptografados com algoritmos fortes, o "dano relevante" pode ser inexistente, o que desobriga a notificação pública e reduz multas.