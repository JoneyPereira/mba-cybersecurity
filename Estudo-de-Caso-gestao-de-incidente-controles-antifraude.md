# Estudo de Caso: Gestão de Incidentes e Controles Antifraude
**Contexto:** MBA em Cibersegurança
**Cenário:** Tentativa de *Account Takeover* (Invasão de Conta) em uma Fintech.

---

## 🚨 1. Descrição do Incidente
* **Vítima:** Cliente com perfil de transações baixas via iOS.
* **Ataque:** O atacante obteve credenciais (usuário, senha e token) via Phishing.
* **Objetivo do Atacante:** Realizar uma transferência de alto valor (R$ 15.000,00) via PIX para uma conta laranja.

---

## 🛡️ 2. Aplicação de Controles Eficazes

Durante a tentativa de invasão, três camadas de defesa agiram de forma integrada:

| Controle | Função no Incidente | Impacto |
| :--- | :--- | :--- |
| **Device ID** | Identificou que o acesso partiu de um emulador Android e não do iPhone habitual. | Elevou o score de risco da sessão imediatamente. |
| **Biometria Comportamental** | Detectou padrões de digitação "mecânicos" e navegação inconsistente com o histórico da usuária. | Gerou um alerta silencioso de "usuário suspeito". |
| **Limites Dinâmicos** | O motor de risco bloqueou a transação de R$ 15k, pois o limite habitual da cliente é de R$ 500. | Impediu o prejuízo financeiro (perda de ativos). |

---

## 📋 3. Ciclo de Resposta a Incidentes (IR)

### Fase 1: Detecção e Análise
Os sistemas de monitoramento correlacionaram a falha de **Device ID** com a anomalia na **Biometria Comportamental**. O analista de segurança confirmou que o IP de origem pertencia a uma VPN comercial conhecida por atividades maliciosas.

### Fase 2: Contenção
O sistema de **Limites Transacionais Dinâmicos** agiu automaticamente como primeira barreira. Em seguida, o SOC (Security Operations Center) efetuou o logoff forçado de todas as sessões ativas da conta e bloqueou temporariamente o acesso.

### Fase 3: Erradicação e Recuperação
* **Erradicação:** Remoção dos tokens de acesso comprometidos.
* **Recuperação:** A cliente foi contatada por canal seguro. Após validação de identidade (prova de vida), foi orientada a trocar a senha e o dispositivo de confiança.

### Fase 4: Lições Aprendidas (Visão de Gestão)
* **Sucesso:** Os controles preventivos e detectivos funcionaram, evitando um prejuízo de R$ 15.000,00.
* **Melhoria:** Identificou-se a necessidade de implementar **FIDO2/Passkeys** para clientes de alto valor, reduzindo a dependência de senhas vulneráveis a Phishing.

---

## 💡 Conclusão para o MBA
A segurança moderna não se baseia em uma única barreira, mas no conceito de **Defesa em Profundidade**. A integração entre dados técnicos (Device ID) e dados comportamentais (Biometria) é o que permite uma resposta rápida e adaptativa em ambientes de alta criticidade.