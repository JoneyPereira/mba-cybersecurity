# mba-cybersecurity
Notas de aulas de projetos desenvolvidos.

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
