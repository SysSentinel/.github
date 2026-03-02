<img width="609" height="272" alt="Screenshot 2026-03-02 at 12-46-07 SysSentinel" src="https://github.com/user-attachments/assets/0f62a484-97c6-4f95-9c04-6b54b305aad7" />

# SysSentinel

SysSentinel é uma solução distribuída para monitoramento de máquinas em redes locais (LAN/VPN), composta por um servidor central e clientes leves instalados nos em sistemas monitorados.

O projeto foi desenvolvido com foco em:

* Monitoramento em tempo real
* Segurança baseada em autenticação JWT
* Baixo consumo de recursos no cliente

> [!NOTE]
> Links para acesso rapido:
> 
> Server ➜ [SysSentinel-Server](https://github.com/SysSentinel/SysSentinel-Server/)
> 
> Client ➜ [SysSentinel-Client](https://github.com/SysSentinel/SysSentinel-Client/)


---

## Índice

* [Arquitetura Geral](#arquitetura-geral)
  * [1. SysSentinel-Server](#1-syssentinel-server)
  * [2. SysSentinel-Client](#2-syssentinel-client)
* [Fluxo de Comunicação](#fluxo-de-comunicação)
* [Segurança](#segurança)
* [Estrutura da Organização](#estrutura-da-organização)
* [Objetivo do Projeto](#objetivo-do-projeto)
* [Galeria de fotos](#galeria-de-fotos)
* [Licença](#licença)

---

## Arquitetura Geral

O SysSentinel é dividido em múltiplos repositórios independentes:

### 1. SysSentinel-Server

Backend central responsável por:

* Autenticação de usuários (Spring Security + JWT)
* Recebimento de métricas das máquinas
* Armazenamento de dados
* Exposição de endpoints REST para consumo pelo frontend

Tecnologias:

* Java
* Spring Boot 3
* Spring Security
* JWT (HMAC HS256)
* H2 / Banco relacional
* Maven

Repositório:
[https://github.com/ribeiro-boll/SysSentinel-Server](https://github.com/ribeiro-boll/SysSentinel-Server)

---

### 2. SysSentinel-Client

Cliente leve instalado nas máquinas monitoradas.

Responsável por:

* Coleta de métricas do sistema (CPU, RAM, processos, rede, etc.)
* Envio periódico de informações ao servidor
* Execução controlada de comandos autorizados
* Comunicação autenticada via JWT

Tecnologias:

* Java
* OSHI (monitoramento de hardware/sistema)
* HTTP client

Repositório:
[https://github.com/ribeiro-boll/SysSentinel-Client](https://github.com/ribeiro-boll/SysSentinel-Client)

---

## Fluxo de Comunicação

1. Usuário realiza login no servidor.
2. O servidor gera um JWT assinado.
3. O cliente envia métricas autenticadas ao servidor.
4. O servidor valida o token e processa os dados.
5. O frontend consome os dados via API REST.

A aplicação é projetada para uso em ambientes controlados (LAN/VPN), não sendo destinada a exposição pública direta.

---

## Segurança

* Autenticação baseada em JWT
* Tokens assinados com HMAC SHA-256
* Validação de identidade por UUID da máquina
* Controle de autorização por usuário
* Senhas armazenadas com hash seguro (BCrypt)

---

## Estrutura da Organização

SysSentinel (Organization)

* SysSentinel-Server
* SysSentinel-Client
  
---

## Objetivo do Projeto

O objetivo do SysSentinel é servir como:

* Plataforma de monitoramento para redes privadas
* Base para estudos de segurança e autenticação
* Projeto completo de arquitetura cliente-servidor
* Fundamento para futuras expansões (dashboard web, alertas, automação)

---

## Galeria de Fotos

- Pagina de registro de Sistemas

> <img width="609" height="272"  alt="registerUUID" src="https://github.com/user-attachments/assets/f7ce96e0-92f3-40b9-8638-c13ebb101b8b" />

- Pagina da lista de Sistemas

> <img width="609" height="272"  alt="SystemsPage" src="https://github.com/user-attachments/assets/11593a85-2438-4ea1-9450-7e9bf75c17dc" />

- Pagina de detalhes do sistema (Parte 1)

> <img width="609" height="272" alt="details1" src="https://github.com/user-attachments/assets/5ebeb5bf-8352-41bb-9eb7-a15e5898c5a1" />

- Pagina de detalhes do sistema (Parte 2)
  
> <img width="609" height="272" alt="details2" src="https://github.com/user-attachments/assets/d9a2bebb-5ed0-4ea9-aa78-d98572d1bb60" />

---

## Licença

MIT

---
