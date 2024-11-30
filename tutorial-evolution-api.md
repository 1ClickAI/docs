---
icon: book-open
---

# Instalação da Evolution API

A Evolution API é usada para conectar agentes no WhatsApp e gerenciar automações. Este guia mostra como configurá-la utilizando o EasyPanel.

## Requisitos

* EasyPanel configurado no seu servidor.
* Conhecimento básico sobre Docker (gerenciado pelo EasyPanel).

## Passo a Passo

### 1. Configurar a Base de Dados

1. No EasyPanel, clique em **New Service** e selecione **PostgreSQL**:
   * Nomeie o serviço como `postgres`.
   * Salve as credenciais.
2. Crie outro serviço para o Redis:
   * Nomeie o serviço como `redis`.
   * Salve as credenciais.

### 2. Configurar a Evolution API

1. Adicione um novo serviço:
   * Clique em **New Service** e selecione **App**.
   * Nomeie o serviço como `evolution`.
2. Configure a imagem Docker:
   * Use a imagem oficial: `attend/evolution-api:v2.2.0`.
   * Salve as alterações.
3. Adicione as variáveis de ambiente:
   *   Preencha as variáveis conforme o modelo abaixo:

       ```env
       POSTGRES_URL=<URL do PostgreSQL>
       REDIS_URL=<URL do Redis>
       API_KEY=<Chave Gerada>
       DOMAIN_URL=<URL personalizada>
       ```
   * Substitua `<URL>` e `<Chave Gerada>` com suas credenciais.
4. Configure volumes:
   * Adicione um volume chamado `evolution-instances`.

### 3. Realizar o Deploy

1. No EasyPanel, clique em **Deploy** para iniciar a aplicação.
2. Verifique os logs para confirmar que a aplicação iniciou corretamente.

### 4. Acessar o Painel da Evolution API

1. No navegador, acesse: `http://<seu-dominio>/manager`.
2. Faça login usando a API Key configurada.

### 5. Conectar ao WhatsApp

1. No painel da Evolution API, crie uma nova instância.
2. Escaneie o QR Code com o WhatsApp para conectar.

Agora sua Evolution API está pronta para uso! Se precisar de mais ajuda, entre em contato com nossa [comunidade](tutorial-evolution-api.md).

{% embed url="https://doc.evolution-api.com/v2/pt/get-started/introduction" %}
