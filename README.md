# Chatwoot

## 1. Descrição

- **Objetivo:**  
  O Chatwoot é um microsserviço responsável por centralizar e gerenciar os atendimentos digitais do setor de aprovativos da Office Engenharia, oferecendo uma interface unificada para comunicação com clientes. Ele atua como a camada de atendimento e relacionamento, integrando canais de mensagens e permitindo operação multiusuário com controle de permissões.

- **Escopo:**  
  - Atendimento ao cliente via canais digitais (atualmente focado em WhatsApp)  
  - Gestão de usuários, times e caixas de entrada (inboxes)  
  - Histórico de conversas e mensagens  
  - Interface web para operadores e administradores  
  - Integração com serviços externos (APIs, SMTP e webhooks)

---

## 2. Portas e acessos

- **Portas internas (container):**
  - `9000/TCP` – Aplicação Chatwoot (Web + API)

- **Portas externas (host):**
  - `9090/TCP` – Acesso ao painel web (ambiente local/produção interna)

- **URLs relevantes:**
  - Painel Web / API:
    ```
    http://<IP_DA_VM>:9090
    ```
  - Healthcheck:
    ```
    /health
    ```

---

## 3. Dependências

- **Dependências internas:**
  - **PostgreSQL** – Banco de dados relacional  
  - **Redis** – Cache e filas de processamento (Sidekiq)

- **Dependências externas:**
  - **Servidor SMTP** – Envio de e-mails transacionais  
  - **API de WhatsApp (via conector externo)** – Canal principal de atendimento  
  - **Cloudflare Tunnel** – Exposição segura do serviço para acesso externo  
  - Webhooks e APIs de integração (quando aplicável)

---

## 4. Execução e operação

- **Build da aplicação (a partir do fork):**
  ```bash
  docker compose -f docker-compose.production.yaml build
