---
title: Acesso e perfil
layout: default
parent: Manual do usuário
nav_order: 2
---

# Acesso e perfil

## 4. Acesso à conta (login e segurança)

### 4.1 Login

![Formulário de login do painel]({{ site.baseurl }}/assets/images/manual/02-login.png)

| Campo / ação | Utilização |
|--------------|------------|
| **Usuário ou e-mail** | Identificação da conta do painel. |
| **Senha** | Senha do painel. |
| **Esqueci minha senha** | Abre o fluxo de recuperação por e-mail. |

Se a conta tiver MFA ativo, após a senha:

| Campo / ação | Utilização |
|--------------|------------|
| **Código do autenticador** | Código de 6 dígitos do app (Google Authenticator, Authy, etc.). |
| **Perdeu o autenticador?** | Vai para recuperação de MFA. |
| **Voltar para a senha** | Retorna ao passo de senha. |

### 4.2 Esqueci minha senha

![Recuperação de senha por e-mail]({{ site.baseurl }}/assets/images/manual/02-esqueci-senha.png)

| Campo | Utilização |
|-------|------------|
| **E-mail** | Se existir conta, o sistema envia link para redefinir a senha. |

### 4.3 Nova senha (link do e-mail)

| Campo | Utilização |
|-------|------------|
| **Nova senha** | Defina a nova senha (regras de força aplicadas na tela). |
| **Confirmar senha** | Deve ser idêntica à nova senha. |

### 4.4 Recuperar autenticador (MFA)

- **Sem token na URL:** informe o **E-mail** para receber o link de remoção do 2FA.

![Recuperar autenticador informando o e-mail]({{ site.baseurl }}/assets/images/manual/02-recuperar-mfa.png)
- **Com token:** confirme a remoção do 2FA e configure o autenticador de novo no **Perfil**.

### 4.5 Confirmar e-mail / Aceitar convite

- **Confirmar e-mail:** validação automática pelo link; depois faça login.
- **Aceitar convite:**
  - Conta nova: preencha **Nome completo**, **Usuário (login)**, **Senha** e **Confirmar senha**.
  - Conta já existente: use **Confirmar acesso**.

---

## 5. Perfil (`/profile`)

Dados da sua conta no painel.

![Perfil do usuário no painel]({{ site.baseurl }}/assets/images/manual/02-perfil.png)

### Dados do usuário

| Campo | Utilização |
|-------|------------|
| **Nome** | Nome exibido no painel. |
| **Login** | Identificador de login. |
| **E-mail** | Contato e recuperação de senha/MFA. |
| **Nova senha (opcional)** | Altera a senha; deixe vazio para manter. |
| **Confirmar nova senha** | Confirmação obrigatória se informar nova senha. |

### Autenticação em dois fatores

![Autenticação em dois fatores no perfil]({{ site.baseurl }}/assets/images/manual/02-perfil-2fa.png)

| Ação / campo | Utilização |
|--------------|------------|
| **Configurar autenticador (QR)** | Exibe QR para cadastrar no app TOTP. |
| **Código de confirmação** | Confirma a ativação do 2FA. |
| **Código do autenticador** | Valida código se o app já estiver configurado. |
| **Desativar** | Exige **Senha do painel** + **Código do autenticador**. |

---

*Interface sujeita a evolução; rótulos e campos seguem a versão atual do painel OmniGateway.*
