---
title: Acesso à API pública
layout: default
parent: Manual do usuário
nav_order: 4
---

# Acesso à API pública

## 11. Papéis da API

Papéis de autorização dos **consumidores** da API pública (não confundir com perfis do painel).

![Lista de papéis da API]({{ site.baseurl }}/assets/images/manual/04-papeis-lista.png)

![Formulário de papel da API]({{ site.baseurl }}/assets/images/manual/04-papeis-formulario.png)

| Campo | Utilização |
|-------|------------|
| **Nome** | Identificação do papel (ex.: `leitura`, `integracao-erp`). |
| **Papel ativo** | Papéis inativos não devem autorizar chamadas. |
| **Descrição** | Texto de apoio. |

Na lista: contagem de usuários e permissões; atalho para **gerenciar permissões**.

---

## 12. Usuários da API

Contas que sistemas externos usam para chamar o gateway.

### 12.1 Lista

![Lista de usuários da API]({{ site.baseurl }}/assets/images/manual/04-usuarios-api-lista.png)

| Coluna | Utilização |
|--------|------------|
| **Usuário** | Login/identificação do consumidor. |
| **Papel** | Papel RBAC associado. |
| **Tokens ativos** | Quantidade de tokens válidos. |
| **Webhook job** | Indica se há webhook de conclusão configurado. |
| **Status** | Ativo/inativo. |

### 12.2 Formulário

![Formulário de usuário da API]({{ site.baseurl }}/assets/images/manual/04-usuarios-api-formulario.png)

| Campo | Utilização |
|-------|------------|
| **Usuário** | Identificador do consumidor. |
| **Papel** | Define o conjunto de APIs permitidas (via permissões do papel). |
| **Usuário ativo** | Desative para bloquear todos os tokens desse usuário. |
| **Webhook de conclusão de job** | URL que receberá POST quando um job assíncrono terminar. |
| **Webhook ativo** | Liga/desliga o disparo do webhook. |

O webhook **não** liga o modo assíncrono; apenas notifica o fim do job. A async é controlada na **definição de API**.

### 12.3 Tokens (edição do usuário)

| Campo / coluna | Utilização |
|----------------|------------|
| **Identificação** | Rótulo do token (ex.: “produção”, “homolog”). |
| **Prefixo** | Trecho visível do token (o secret completo só aparece na criação). |
| **Criado em / Expira em** | Ciclo de vida. |
| **Estado (ativo)** | Desative sem apagar o token. |
| **Nome ou comentário** (novo) | Identificação opcional. |
| **Expira em** (novo) | Data/hora de validade opcional. |

Guarde o secret exibido **uma única vez** após a geração; ele não é mostrado de novo.

---

## 13. Permissões por papel

Define se um papel **pode invocar** cada definição de API.

### 13.1 Lista / item único

![Lista de permissões por papel]({{ site.baseurl }}/assets/images/manual/04-permissoes-lista.png)

| Campo | Utilização |
|-------|------------|
| **Papel** | Papel da API. |
| **API Path** | Definição de API alvo. |
| **Pode invocar** | Liga ou bloqueia a chamada para aquele papel. |

### 13.2 Gerenciar por papel

![Entrada para gerenciar permissões por papel]({{ site.baseurl }}/assets/images/manual/04-permissoes-formulario.png)

Tela em lote para um papel:

| Controle | Utilização |
|----------|------------|
| **Filtrar por método ou path** | Narrow nas APIs listadas. |
| **Marcar / Desmarcar filtradas** | Seleção em massa. |
| **Pode invocar** | Valor aplicado às marcadas. |
| **Salvar permissões** | Persiste a matriz. |

Sem permissão, a chamada autenticada com token desse papel tende a ser negada (acesso proibido), mesmo com a rota mapeada.

---

## 14. Rate limit

Controla quantas requisições a API aceita por janela de tempo.

### 14.1 Visão geral

![Rate limit global e aba Usuário]({{ site.baseurl }}/assets/images/manual/04-rate-limit.png)

| Informação | Utilização |
|------------|------------|
| **Máx. requisições (global)** | Limite padrão da organização. |
| **Janela (ms)** | Duração da janela do contador global. |

Abas **Usuário** e **Rota** abrem as exceções.

### 14.2 Exceção por rota

![Exceções de rate limit por rota]({{ site.baseurl }}/assets/images/manual/04-rate-limit-rota.png)

![Formulário de exceção por rota]({{ site.baseurl }}/assets/images/manual/04-rate-limit-rota-form.png)

| Campo | Utilização |
|-------|------------|
| **Definição de API** | Rota que terá limite próprio. |
| **Máx. requisições** | Teto na janela. |
| **Janela (ms)** | Duração da janela desta exceção. |
| **Override ativo** | Liga/desliga a exceção. |

### 14.3 Exceção por usuário

![Formulário de exceção por usuário]({{ site.baseurl }}/assets/images/manual/04-rate-limit-usuario-form.png)

| Campo | Utilização |
|-------|------------|
| **Usuário da API** | Consumidor alvo. |
| **Rota (opcional)** | Se vazio, aplica a todas as rotas desse usuário; se preenchido, só à rota escolhida. |
| **Máx. requisições / Janela (ms)** | Limite específico. |
| **Override ativo** | Liga/desliga. |

Quando o limite é excedido, a API pública responde com erro de rate limit; o log de chamadas pode mostrar o código correspondente.

---

*Interface sujeita a evolução; rótulos e campos seguem a versão atual do painel OmniGateway.*
