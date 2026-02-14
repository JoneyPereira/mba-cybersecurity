# 🔐 MBA em Cibersegurança — Notas de Estudo

Este repositório contém minhas **anotações, mapas mentais e resumos técnicos**
produzidos durante o **MBA em Cibersegurança**.

O objetivo é:
- Consolidar o aprendizado
- Facilitar revisões para provas
- Criar um material de referência profissional

---
## 📚 Conteúdo

- Fundamentos de Cibersegurança
- Redes de Computadores e Segurança
- Criptografia
- Segurança em Aplicações
- Governança, Risco e Compliance
- Ethical Hacking e Gestão de Vulnerabilidades

---

## 🧠 Metodologia de Estudo

- Resumos teóricos
- Mapas mentais (Mermaid)
- Questões comentadas
- Casos reais de incidentes
- Conexão com práticas de mercado

---

## ⚠️ Aviso

Este material é exclusivamente educacional e não deve ser utilizado
para fins ilegais ou não autorizados.

---

📌 *Repositório mantido como parte da evolução profissional em Cibersegurança.*

## Segmentação em VLANs e regras de acesso controladas

```mermaid
graph TD
    subgraph Rede_Externa["🌐 Rede Externa / Internet"]
        EXT[Usuários Externos]
    end

    subgraph Roteador["🧠 Roteador Principal (com ACLs)"]
        ACL1[ACL Entrada - VLAN Visitantes]
        ACL2[ACL Entrada - VLAN Pesquisa]
        ACL3[ACL Saída - VLAN Administração]
    end

    subgraph VLANs["🏫 Segmentos de Rede (VLANs)"]
        V1["VLAN 10 - Pesquisa e Desenvolvimento"]
        V2["VLAN 20 - Administracao"]
        V3["VLAN 30 - Academica (Alunos)"]
        V4["VLAN 40 - Visitantes"]
        V5["VLAN 50 - Servidores Confidenciais"]
    end

    EXT -->|"Acesso restrito"| ACL1
    ACL1 -->|"Permite apenas HTTP e HTTPS"| V4
    V4 -->|"Bloqueado acesso a Rede de Pesquisa"| V1
    V4 -->|"Bloqueado acesso a Servidores Confidenciais"| V5
    V1 -->|"Permitido SSH e FTP interno"| V5
    V2 -->|"Acesso administrativo controlado"| V5
    V3 -->|"Acesso limitado - apenas e-mail e web"| V5
    ACL3 -->|"Saida segura para Internet"| EXT

    style V1 fill:#ffd6a5,stroke:#333,stroke-width:1px
    style V2 fill:#bde0fe,stroke:#333,stroke-width:1px
    style V3 fill:#caffbf,stroke:#333,stroke-width:1px
    style V4 fill:#ffadad,stroke:#333,stroke-width:1px
    style V5 fill:#fdffb6,stroke:#333,stroke-width:1px
```
## Configuração de ACL Cisco (exemplo prático)

```bash
! ACL 100 - Controle de acesso para VLAN de Visitantes
ip access-list extended VISITANTES-ACL
  remark Bloqueia acesso a Pesquisa e Servidores
  deny ip 192.168.40.0 0.0.0.255 192.168.10.0 0.0.0.255
  deny ip 192.168.40.0 0.0.0.255 192.168.50.0 0.0.0.255
  remark Permite acesso à Internet (tráfego externo)
  permit ip 192.168.40.0 0.0.0.255 any
  remark Negar todo o resto por padrão
  deny ip any any log
exit

! Aplicando a ACL na interface VLAN dos Visitantes
interface GigabitEthernet0/4
 description Interface VLAN 40 - Visitantes
 ip address 192.168.40.1 255.255.255.0
 ip access-group VISITANTES-ACL in
 no shutdown
exit
```
## ESP32 implementado em uma rede Wi-Fi corporativa com autenticação EAP

```mermaid
graph TD

%% Nível de dispositivos
    subgraph IoT Devices
        ESP32["ESP32 (Supplicant)\nCliente Wi-Fi"]
    end

%% Nível de rede
    subgraph Wireless_Network["Rede Wi-Fi Corporativa"]
        AP["Access Point (Authenticator)\n802.1X / WPA2-Enterprise"]
    end

%% Nível de autenticação
    subgraph Auth_Layer["Camada de Autenticação"]
        RADIUS["Servidor RADIUS\n(Autenticador Real)"]
    end

%% Backend de controle de usuários
    subgraph Backend["Serviços de Identidade e Autorização"]
        LDAP["Servidor LDAP / Active Directory"]
        DB["Banco de Dados de Usuários"]
    end

%% Relações entre componentes
    ESP32 -- EAPOL (EAP over LAN) --> AP
    AP -- RADIUS Protocol (UDP/1812) --> RADIUS
    RADIUS -- Consulta de credenciais --> LDAP
    RADIUS -- Log e auditoria --> DB

%% Indicação de comunicação segura
    classDef secure fill:#d0f0d0,stroke:#2f7a2f,stroke-width:2px;
    class ESP32,AP secure;
    class RADIUS,LDAP,DB secure;

%% Legenda
    subgraph Legend["Legenda"]
        direction LR
        A["🟢 Comunicação segura (TLS/SSL)"]
        B["🔒 Autenticação baseada em EAP (802.1X)"]
    end
```
### 🔒 Fluxo resumido da autenticação

1-ESP32 envia solicitação de conexão à rede Wi-Fi Enterprise.

 - O Access Point solicita as credenciais via EAP.

 - As credenciais são repassadas ao Servidor RADIUS via protocolo RADIUS.

 - O RADIUS consulta o LDAP/AD para verificar a validade do usuário.

 - Se aprovado, o RADIUS envia mensagem de sucesso (EAP-Success).

 - O ESP32 estabelece uma sessão segura e criptografada (WPA2/WPA3-Enterprise).

### Arquitetura C4 – Autenticação EAP (802.1X) com ESP32

```mermaid
C4Container
title Arquitetura C4 – Autenticação EAP (802.1X) com ESP32

Person(usr, "Usuário", "Responsável pela configuração e uso do dispositivo ESP32 na rede corporativa.")

System_Boundary(iot_boundary, "Dispositivo IoT - ESP32") {
    Container(esp32_firmware, "Firmware ESP32", "C/C++ (ESP-IDF)", "Gerencia conexão Wi-Fi e autenticação EAP via esp_eap_client API.")
    Container(esp_wifi_module, "Módulo Wi-Fi", "Driver de rede", "Executa o protocolo 802.1X e criptografia WPA2/WPA3.")
}

System_Boundary(network_boundary, "Infraestrutura de Rede") {
    Container(ap, "Access Point", "Hardware/Software", "Controla o acesso e encaminha mensagens EAP para o servidor RADIUS.")
    Container(radius, "Servidor RADIUS", "FreeRADIUS / Microsoft NPS", "Realiza autenticação e autorização de clientes via protocolo RADIUS.")
}

System_Boundary(auth_backend, "Backend de Autenticação") {
    Container(ldap, "Servidor LDAP / Active Directory", "Serviço de Diretório", "Armazena credenciais e políticas de autenticação de usuários/dispositivos.")
    Container(db_logs, "Banco de Dados de Logs", "PostgreSQL / MySQL", "Registra logs de autenticação e tentativas de acesso.")
}

Rel(usr, esp32_firmware, "Configura SSID e credenciais de acesso")
Rel(esp32_firmware, esp_wifi_module, "Gerencia autenticação EAP (PEAP, TLS, TTLS)")
Rel(esp_wifi_module, ap, "Troca pacotes EAPOL (EAP over LAN)")
Rel(ap, radius, "Encaminha mensagens EAP via protocolo RADIUS (UDP 1812)")
Rel(radius, ldap, "Consulta credenciais do usuário/dispositivo")
Rel(radius, db_logs, "Armazena logs de autenticação e auditoria")
Rel(radius, ap, "Retorna resultado EAP-Success ou EAP-Failure")
Rel(ap, esp32_firmware, "Permite ou bloqueia acesso à rede")
```

### ⚙️ Fluxo de autenticação resumido

- O usuário configura o ESP32 com SSID e credenciais.

- O ESP32 Firmware inicia a conexão e executa o EAP Client.

- O Access Point recebe o pedido e envia o EAP-Request.

- O Servidor RADIUS valida as credenciais consultando o LDAP/AD.

- O resultado é logado e retornado ao ESP32, que ganha (ou não) acesso à rede.
