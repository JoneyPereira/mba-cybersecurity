# 🔑 Hash, MAC e HMAC
Mapa mental de estudos — MBA em Cibersegurança

```mermaid
mindmap
  root((Hash<br/>MAC<br/>HMAC))

    Hash
      Conceito
        Funcao_Unidirecional
        Nao_Reversivel
      Objetivos
        Integridade
        Verificacao_de_Dados
      Algoritmos
        MD5_Inseguro
        SHA_1_Inseguro
        SHA_256
        SHA_512
      Caracteristicas
        Tamanho_Fixo
        Pequena_Mudanca_Grande_Efeito
      Aplicacoes
        Verificacao_de_Arquivos
        Armazenamento_de_Senhas
        Assinaturas_Digitais

    MAC
      Conceito
        Message_Authentication_Code
        Hash_com_Chave
      Objetivos
        Integridade
        Autenticacao
      Caracteristicas
        Chave_Compartilhada
        Simetrico
      Algoritmos
        CBC_MAC
        CMAC
      Aplicacoes
        Comunicacao_Segura
        APIs
        Protocolos_de_Rede

    HMAC
      Conceito
        Hash_Based_MAC
        Hash_com_Chave_Secreta
      Algoritmos
        HMAC_SHA256
        HMAC_SHA512
      Vantagens
        Mais_Seguro_que_MAC_Simples
        Resistente_a_Colisoes
      Aplicacoes
        TLS
        APIs_REST
        Assinatura_de_Mensagens

    Comparacao
      Hash
        Sem_Chave
        Integridade
      MAC
        Com_Chave
        Integridade_e_Autenticacao
      HMAC
        Hash_e_Chave
        Alta_Seguranca
