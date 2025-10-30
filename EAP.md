# Autenticação EAP (Extensible Authentication Protocol) em Redes Corporativas

O EAP é um protocolo de *framework* que permite que diferentes métodos de autenticação (como EAP-TLS, PEAP, EAP-TTLS) sejam utilizados dentro de uma conexão. É o pilar da segurança WPA2/WPA3-Enterprise.

## 🛡️ EAP-TLS vs. PEAP: Detalhes e Diferenças

| Característica | EAP-TLS (Transport Layer Security) | PEAP (Protected EAP) |
| :--- | :--- | :--- |
| **Autenticação de Servidor** | **Obrigatória** (Certificado Digital) | **Obrigatória** (Certificado Digital) |
| **Autenticação de Cliente** | **Obrigatória** (Certificado Digital) | **Geralmente Credenciais** (Usuário/Senha) |
| **Mecanismo Central** | **Autenticação Mútua Baseada em Certificados.** O cliente e o servidor trocam certificados para verificar as identidades. | **Cria um Túnel TLS Criptografado** (o "túnel PEAP") para proteger a autenticação interna (mais comum: EAP-MSCHAPv2, que usa usuário e senha). |
| **Segurança** | **Mais seguro.** Elimina senhas e é resistente a ataques MitM (Man-in-the-Middle) e *phishing*. | **Mais fácil de gerenciar.** Oferece boa segurança, mas é vulnerável a ataques de credenciais (se o cliente não validar o certificado do servidor). |
| **Implementação no Cliente** | Mais complexa. Requer **três** certificados (CA Raiz, Cliente e Chave Privada). | Mais simples. Requer o certificado da **CA Raiz** e credenciais (usuário/senha). |

---

## 💻 Implementação PEAP no ESP32 (WPA2-Enterprise)

O método PEAP é a escolha mais comum para dispositivos IoT como o ESP32, pois permite o uso de credenciais (usuário e senha) para autenticação do cliente. A implementação utiliza as APIs de segurança Wi-Fi do ESP-IDF.

### Código de Exemplo (Framework Arduino/ESP-IDF)

Este código configura o ESP32 para se conectar a uma rede WPA2-Enterprise usando PEAP.

```cpp
#include <WiFi.h>
#include "esp_wpa2.h" // Necessário para funções WPA2 Enterprise
#include "esp_wifi.h" // Para acessar as funções de autenticação EAP

// --- 1. Configurações da Rede Enterprise ---
const char *ssid = "NOME_DA_SUA_REDE_WPA2_ENTERPRISE";
#define EAP_ID       "seu_usuario_eap"
#define EAP_USERNAME "seu_usuario_eap"
#define EAP_PASSWORD "sua_senha_segura"

// --- 2. Certificado da CA Raiz (Root CA) ---
// Cole o conteúdo do seu certificado da CA Raiz (formato PEM) aqui.
// Esta etapa é crucial para que o ESP32 confie no servidor RADIUS.
const char* ca_cert = \
"-----BEGIN CERTIFICATE-----\n"
"COLE AQUI O CONTEÚDO DO SEU CERTIFICADO RAIZ (ROOT CA)\n"
"-----END CERTIFICATE-----\n";

void setup() {
  Serial.begin(115500);
  delay(10);
  Serial.println("\nIniciando conexao WPA2 Enterprise (PEAP)...");

  // 1. Desconectar e configurar o modo STA
  WiFi.disconnect(true);
  WiFi.mode(WIFI_STA);

  // 2. Definir as credenciais e identidade
  esp_wifi_sta_wpa2_ent_set_identity((uint8_t *)EAP_ID, strlen(EAP_ID));
  esp_wifi_sta_wpa2_ent_set_username((uint8_t *)EAP_USERNAME, strlen(EAP_USERNAME));
  esp_wifi_sta_wpa2_ent_set_password((uint8_t *)EAP_PASSWORD, strlen(EAP_PASSWORD));

  // 3. Configurar Certificado da CA para validação do servidor
  if (strlen(ca_cert) > 0) {
    Serial.println("Configurando Certificado CA...");
    esp_wifi_sta_wpa2_ent_set_ca_cert((uint8_t *)ca_cert, strlen(ca_cert));
  } else {
    Serial.println("AVISO: Certificado CA nao fornecido. A seguranca pode ser comprometida.");
  }

  // 4. Habilitar o modo WPA2 Enterprise
  esp_wpa2_config_t config = WPA2_CONFIG_INIT_DEFAULT();
  esp_wifi_sta_wpa2_ent_enable(&config);

  // 5. Iniciar a conexão Wi-Fi
  WiFi.begin(ssid);

  // 6. Loop de Conexão
  int attempts = 0;
  while (WiFi.status() != WL_CONNECTED && attempts < 30) {
    delay(1000);
    Serial.print(".");
    attempts++;
  }

  // 7. Resultado da Conexão
  if (WiFi.status() == WL_CONNECTED) {
    Serial.println("\n\nConectado com Sucesso!");
    Serial.print("IP Address: ");
    Serial.println(WiFi.localIP());
  } else {
    Serial.println("\n\nFalha na Conexao Enterprise! Verifique credenciais e certificados.");
  }
}

void loop() {
  // Seu código principal...
}
