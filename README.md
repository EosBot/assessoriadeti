
# 6 Sides Tech

## Projeto de Assessoria de TI com Softwares Open Source

### Visão Geral
Este projeto é uma solução de assessoria de TI que utiliza softwares open source para criar uma infraestrutura robusta e escalável em uma Virtual Private Server (VPS). Os softwares principais incluem Typebot, Chatwoot, n8n, Traefik e Portainer. Essa configuração oferece um conjunto abrangente de ferramentas para gerenciar comunicação, automação de fluxo de trabalho, gerenciamento de contêineres e monitoramento da infraestrutura.

### Softwares Utilizados
1. **Typebot**: Plataforma de chatbot open source que permite criar e gerenciar bots de conversação para diversos propósitos, incluindo suporte ao cliente e geração de leads.
2. **Chatwoot**: Plataforma de atendimento ao cliente de código aberto, que oferece recursos de chat ao vivo, automação de mensagens e gerenciamento centralizado de conversas de clientes.
3. **n8n**: Plataforma de automação de fluxo de trabalho que permite integrar serviços online, APIs e ferramentas de forma visual e fácil, sem a necessidade de escrever código.
4. **Traefik**: Roteador de borda open source e um balanceador de carga reverso que ajuda a implementar serviços de rede de forma eficiente e segura, com suporte a configuração dinâmica.
5. **Portainer**: Interface de usuário simples e intuitiva para gerenciar contêineres Docker em um ambiente Docker Swarm ou Kubernetes.
6. **pgvector**: Extensão para PostgreSQL para suporte a operações de vetor, especialmente útil em machine learning e similaridade de pesquisa.
7. **WoofedCRM**: Sistema de gerenciamento de relacionamento com o cliente customizado.
8. **Zabbix Proxy**: Proxy para Zabbix, uma plataforma de monitoramento open source.
9. **Sign**: Serviço para assinatura digital.
10. **NocoBase**: Plataforma de gerenciamento de dados sem código.
11. **pgAdmin**: Ferramenta de administração e desenvolvimento open source para PostgreSQL.
12. **Zammad**: Sistema de tickets open source para suporte técnico e helpdesk.
13. **PostgreSQL**: Sistema de gerenciamento de banco de dados objeto-relacional.
14. **MongoDB**: Banco de dados NoSQL orientado a documentos.
15. **Redis**: Armazenamento de estrutura de dados em memória, utilizado como banco de dados, cache e broker de mensagens.
16. **RabbitMQ**: Broker de mensagens open source.
17. **EvolutionAPI**: API customizada para integração do whatsapp.

## Estrutura do Projeto
O projeto está organizado em vários diretórios, cada um contendo um arquivo `docker-compose.yaml` para a configuração dos serviços Docker correspondentes. Aqui estão os principais diretórios e seus conteúdos:

- **1-traefik**
  - `docker-compose.yaml`: Configuração do Traefik.

- **10-pgvector**
  - `docker-compose.yaml`: Configuração do pgvector.
  - `regras.txt`: Regras específicas para o pgvector.

- **11-woofedcrm**
  - `docker-compose.yaml`: Configuração do WoofedCRM.

- **12-Zabbix-proxy**
  - `docker-compose.yaml`: Configuração do Zabbix Proxy.
  - `zabbix-message-whatsapp-evolution.yaml`: Configuração para mensagens WhatsApp no Zabbix.

- **13-sign**
  - `docker-compose.yaml`: Configuração do serviço Sign.

- **14-nocobase**
  - `docker-compose.yaml`: Configuração do Nocobase.

- **15-pgadmin**
  - `docker-compose.yaml`: Configuração do pgAdmin.

- **16-zammad**
  - `docker-compose.yaml`: Configuração do Zammad.
  - `backup.sh`: Script de backup para o Zammad.
  - `github.txt`: Instruções relacionadas ao GitHub para o Zammad.

- **2-portainer**
  - `docker-compose.yaml`: Configuração do Portainer.

- **3-postgres**
  - `docker-compose.yaml`: Configuração do PostgreSQL.

- **4-mongodb**
  - `docker-compose.yaml`: Configuração do MongoDB.

- **5-Typebot**
  - `docker-compose.yml`: Configuração do Typebot.

- **5-redis**
  - `docker-compose.yaml`: Configuração do Redis.

- **6-chatwoot**
  - `docker-compose.yaml`: Configuração do Chatwoot.

- **7-n8n**
  - `docker-compose.yaml`: Configuração do n8n.

- **8-rabbitmq**
  - `docker-compose.yml`: Configuração do RabbitMQ.
  - `command-monitor.txt`: Comandos de monitoramento.
  - `commmands-bash.txt`: Comandos Bash para RabbitMQ.
  - `create-user.txt`: Instruções para criar usuários no RabbitMQ.
  - `rabbitmq.conf`: Arquivo de configuração do RabbitMQ.

- **9-evolutionapi**
  - `.env`: Arquivo de configuração de ambiente para o Evolution API.
  - `docker-compose.yaml`: Configuração do Evolution API.

## Passos de Instalação

### Instalação do Docker
1. Atualize e instale o Docker:
   ```bash
   sudo apt-get update
   sudo apt-get install -y apparmor-utils
   curl -fsSL https://get.docker.com | bash
   ```
2. Inicialize o Docker Swarm:
   ```bash
   docker swarm init
   docker network create --driver=overlay traefik
   ```

### Instalação do Traefik
1. Crie um diretório para o Traefik e adicione o arquivo `docker-compose.yaml`.
2. Implante o stack do Traefik:
   ```bash
   docker stack deploy --prune --resolve-image always --detach=false -c docker-compose.yaml traefik
   ```

### Instalação do Portainer
1. Crie um diretório para o Portainer e adicione o arquivo `docker-compose.yaml`.
2. Implante o stack do Portainer:
   ```bash
   docker stack deploy --prune --resolve-image always --detach=false -c docker-compose.yaml portainer
   ```

### Criação de Bancos de Dados PostgreSQL
1. Crie os bancos de dados necessários dentro do PostgreSQL:
   ```sql
   create database n8n_queue;
   create database chatwoot;
   create database typebot;
   create database woofedcrm;
   ```

### Execução dos Contêineres
1. Em cada diretório correspondente ao serviço, execute:
   ```bash
   docker-compose up -d
   ```
