
# SysSentinel

SysSentinel é uma solução distribuída para monitoramento de máquinas em redes locais (LAN/VPN), composta por um servidor central e clientes leves instalados nos hosts monitorados.

O projeto foi desenvolvido com foco em:

* Monitoramento em tempo real
* Segurança baseada em autenticação JWT
* Arquitetura modular
* Baixo consumo de recursos no cliente
* Facilidade de expansão

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

## Licença

MIT

---

Qual direção você quer seguir?
