# 🗄️ Backup Portainer — n8n Workflow

Workflow para automação de backup semanal de instâncias **Portainer**, com upload automático para o **OneDrive** e notificação por **e-mail**.

---

## 📋 O que esse workflow faz

1. **Disparo automático** toda sexta-feira às 19h
2. **Requisita o backup** de cada servidor Portainer via API
3. **Faz upload** do arquivo gerado para uma pasta no OneDrive
4. **Envia um e-mail** de confirmação com informações da execução

---

## 🔁 Fluxo

```
Schedule Trigger (Sexta 19h)
    ├── HTTP Server1 → Upload OneDrive → Send Email Server1
    └── HTTP Server2 → Upload OneDrive → Send Email Server2
```

---

## ⚙️ Configuração

Antes de importar o workflow no n8n, substitua os seguintes placeholders pelos valores reais do seu ambiente:

### Servidores

| Placeholder | Descrição |
|---|---|
| `{{SERVER1_IP}}` | IP do primeiro servidor Portainer |
| `{{SERVER2_IP}}` | IP do segundo servidor Portainer |
| `{{SERVER1_PORTAINER_API_KEY}}` | API Key do Portainer — Servidor 1 |
| `{{SERVER2_PORTAINER_API_KEY}}` | API Key do Portainer — Servidor 2 |
| `{{SERVER1_BACKUP_PASSWORD}}` | Senha de criptografia do backup — Servidor 1 |
| `{{SERVER2_BACKUP_PASSWORD}}` | Senha de criptografia do backup — Servidor 2 |

### E-mail

| Placeholder | Descrição |
|---|---|
| `{{SENDER_EMAIL}}` | E-mail remetente (ex: `noreply@seudominio.com`) |
| `{{RECIPIENT_EMAIL}}` | E-mail destinatário das notificações |

### OneDrive

| Placeholder | Descrição |
|---|---|
| `{{ONEDRIVE_FOLDER_ID}}` | ID da pasta de destino no OneDrive |
| `{{ONEDRIVE_CREDENTIAL_ID}}` | ID da credencial Microsoft OneDrive no n8n |
| `{{ONEDRIVE_CREDENTIAL_NAME}}` | Nome da credencial Microsoft OneDrive no n8n |

### SMTP

| Placeholder | Descrição |
|---|---|
| `{{SMTP_CREDENTIAL_ID}}` | ID da credencial SMTP no n8n |
| `{{SMTP_CREDENTIAL_NAME}}` | Nome da credencial SMTP no n8n |

### n8n

| Placeholder | Descrição |
|---|---|
| `{{N8N_INSTANCE_ID}}` | ID da instância do n8n (opcional) |

---

## 🔐 Como obter a API Key do Portainer

1. Acesse o painel do Portainer
2. Vá em **My Account** → **Access tokens**
3. Gere um novo token e copie o valor

---

## 📦 Como importar no n8n

1. Acesse seu n8n
2. Vá em **Workflows** → **Import from file**
3. Selecione o arquivo `backup-portainer-workflow.json`
4. Configure as credenciais necessárias (OneDrive e SMTP)
5. Substitua os placeholders pelos valores reais
6. Ative o workflow

---

## 🛠️ Requisitos

- n8n v1.0+
- Conta Microsoft com OneDrive configurado
- Acesso à API do Portainer (token de autenticação)
- Servidor SMTP ou serviço de e-mail (ex: Resend, SendGrid)

---

## 📁 Arquivos

```
.
├── backup-portainer-workflow.json   # Workflow do n8n (sem dados sensíveis)
└── README.md
```
