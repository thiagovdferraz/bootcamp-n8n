# ✅ Checklist para conectar APIs do Google no n8n

Se você quer usar **Google Drive, Gmail, Google Sheets, Docs, Calendar ou Slides** dentro do **n8n** (especialmente se está na trilha de automações da Jornada), precisa seguir esse passo a passo.

Dá um pouco de medo na primeira vez. O painel do Google Cloud parece um labirinto, mas aqui está tudo mastigado.

---

## 1. Acesse o Console da Google Cloud
- Vá para: [https://console.cloud.google.com](https://console.cloud.google.com)
- Faça login com a **conta do Gmail certa** (a que vai usar no n8n).

---

## 2. Configure o pagamento (mesmo sem pagar)
- Vai pedir um **cartão físico** (Visa/Mastercard).
- **Não pode ser** Nubank virtual ou cartão com bloqueio internacional.
- Você **NÃO será cobrado**. O Google só quer garantir que você é um ser humano válido. Inclusive, libera **US$300 em créditos** para novos usuários.

---

## 3. Crie um Projeto no GCP
- No topo, clique em **"Selecionar Projeto" > "Novo Projeto"**.
- Nomeie como quiser. Ex: `Projeto-n8n`
- Salve e ative o projeto recém-criado.

---

## 4. Ative as APIs necessárias

Você precisa ativar as APIs manualmente. No topo do GCP:

1. Pesquise: **Google Drive API** > Clique > Ativar  
2. Faça o mesmo com:
   - Gmail API  
   - Google Docs API  
   - Google Sheets API  
   - Google Calendar API  
   - Google Slides API  

*Sim, é repetitivo. Mas só precisa fazer uma vez.*

---

## 5. Configure a Tela de Consentimento OAuth

- Menu lateral (ícone de “hambúrguer”) > **APIs & Services > OAuth Consent Screen**
- Clique em **"Get started"**

Preencha:

- **Nome do App**: `n8n-bootcamp`
- **Usuário de suporte**: seu e-mail (ex: `seuemailo@gmail.com`)
- **Tipo de usuário**: Externo
- **E-mail de contato**: seu e-mail

Avance e salve.

---

## 6. Adicione usuários de teste

- Volte para **APIs & Services > OAuth Consent Screen > Audience**
- Vá em **"Test users"** > adicione seu e-mail > clique em **"Save"**
- Coloque seu e-mail e **publique o app**

---

## 7. Crie um Cliente OAuth

- Volte para **APIs & Services > Credenciais**
- Clique em **"Criar credenciais" > "OAuth Client ID"**
- Selecione: **Web Application**
- Nome: `n8n-bootcamp`
- Adicione o **URI de redirecionamento (Authorized redirect URIs)**

### Como encontrar o URI no n8n:

1. Crie um workflow  
2. Adicione um nó do Google Drive > Ação qualquer (ex: "Copy File")  
3. Vá em **Credenciais > Criar nova**  
4. Copie o campo **OAuth Redirect URL**

#### Exemplos:
- Cloud n8n:  
  `https://oauth.n8n.cloud/oauth2/callback`
- Self-hosted:  
  `https://n8n-host/rest/oauth2-credential/callback`

Cole esse valor no campo de URIs de redirecionamento autorizados.

> Clique em **Criar**

---

## 8. Copie o Client ID e o Secret

- Dentro de **Credenciais**, clique no lápis do cliente OAuth  
- Copie:

```text
Client ID:
asdfhausdfghuasdfgausgfausdgfausdgfuads.apps.googleusercontent.com

Client Secret:
9439324y9543y0543y005493y2ufwhbfdbjk