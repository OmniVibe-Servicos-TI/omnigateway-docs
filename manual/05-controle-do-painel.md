---
title: Controle do painel
layout: default
parent: Manual do usuário
nav_order: 5
---

# Controle do painel

## 15. Perfis de acesso (painel)

Controla o que os **usuários do sistema** veem e alteram no `/admin`.

![Lista de perfis de acesso]({{ site.baseurl }}/assets/images/manual/05-perfis-lista.png)

![Formulário de perfil de acesso]({{ site.baseurl }}/assets/images/manual/05-perfis-formulario.png)

| Campo | Utilização |
|-------|------------|
| **Nome** | Nome do perfil (ex.: Operador, Administrador). |
| **Descrição** | Texto de apoio. |
| **Perfil ativo** | Perfis inativos não devem ser atribuídos. |
| **Permissões por tela** | Para cada tela: **Nenhuma**, **Leitura** ou **Gravação**. Há atalhos para aplicar o mesmo nível a todas ou por grupo. |

Telas típicas: Dashboard, Conexões, Queries, Definições de API, Mapeamento de Rota, Papéis da API, Usuários da API, Permissões por Papel, Rate Limit, Usuários do sistema, Perfis de acesso, Auditoria, Chamadas API, Billing, etc.

---

## 16. Usuários do sistema

Quem acessa o painel da organização (não são os consumidores da API).

### 16.1 Lista

![Usuários do sistema e convites]({{ site.baseurl }}/assets/images/manual/05-usuarios-sistema-lista.png)

- **Convites pendentes:** e-mail, perfil, estado, enviado em; ações de reenvio/cancelamento conforme disponível.
- **Membros:** nome, login, e-mail, perfil, status; ações como reenviar verificação de e-mail e remover da organização.

### 16.2 Convidar

![Convite de usuário do sistema]({{ site.baseurl }}/assets/images/manual/05-usuarios-sistema-convidar.png)

| Campo | Utilização |
|-------|------------|
| **E-mail** | Destinatário do convite. |
| **Perfil de acesso** | Perfil que a pessoa terá ao aceitar. |

### 16.3 Editar membro

![Edição de membro da organização]({{ site.baseurl }}/assets/images/manual/05-usuarios-sistema-editar.png)

| Campo | Utilização |
|-------|------------|
| **Nome / E-mail** | Somente leitura. |
| **Perfil de acesso** | Altera as telas permitidas. |
| **Ativo nesta organização** | Desativa o acesso à org (não se aplica a si mesmo em geral). |

---

*Interface sujeita a evolução; rótulos e campos seguem a versão atual do painel OmniGateway.*
