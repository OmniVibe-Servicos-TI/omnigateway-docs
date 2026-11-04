---
title: Visão geral
layout: default
parent: Manual do usuário
nav_order: 1
---

# Visão geral

## 1. O que é o OmniGateway (visão operacional)

O OmniGateway é uma plataforma de **API Gateway configurável**. Pelo painel você:

1. Cadastra **conexões** com bases de dados.
2. Define **queries** (SQL ou operações MongoDB) com parâmetros.
3. Publica **definições de API** (método HTTP + caminho).
4. Liga API + query + conexão em **mapeamentos de rota**.
5. Controla quem chama a API com **papéis**, **usuários da API**, **tokens** e **permissões**.
6. Ajusta **limites de taxa (rate limit)** e acompanha **uso (billing)**, **auditoria** e **logs de chamadas**.

As chamadas dos sistemas clientes são feitas na **API pública** do gateway (fora do painel), autenticadas com o token do **usuário da API**. O painel serve para configurar e monitorar.

### Organização ativa

Tudo o que você cria ou edita pertence à **organização** selecionada. Se o seu login tiver acesso a mais de uma organização:

- Após o login (ou quando necessário), aparece o diálogo **Escolha a organização**.
- No menu lateral, use **Trocar organização** para mudar o contexto.

![Diálogo Escolha a organização]({{ site.baseurl }}/assets/images/guia/01-escolher-organizacao.png)

![Trocar organização no menu lateral]({{ site.baseurl }}/assets/images/guia/01-trocar-organizacao.png)

Listagens e formulários refletem sempre a organização ativa.

### Permissões do painel

Cada usuário do painel tem um **perfil de acesso**. Para cada tela o nível pode ser:

| Nível | Efeito |
|-------|--------|
| **Nenhuma** | A tela não aparece no menu. |
| **Leitura** | Consulta listas e detalhes; sem criar/editar/excluir. |
| **Gravação** | Permite criar, editar e excluir (onde a tela oferece essas ações). |

Se um item do menu não aparecer, peça ao administrador da organização a permissão adequada no perfil.

---

## 2. Resumo das funcionalidades

| Área | Funcionalidade | Para que serve |
|------|----------------|----------------|
| **Operação** | Dashboard | Visão rápida de volumes e atividade recente. |
| | Conexões | Cadastro dos bancos/backends usados pelas queries. |
| | Queries | Templates de consulta e esquema de parâmetros. |
| | Definições de API | Rotas HTTP públicas (método, path, timeout, async). |
| | Mapeamento de rota | Liga API ↔ query ↔ conexão (ordem, fallback, condição). |
| **Acesso e limites** | Papéis da API | Grupos de autorização dos consumidores da API. |
| | Usuários da API | Contas consumidoras, tokens e webhook de jobs. |
| | Permissões por papel | Quais APIs cada papel pode invocar. |
| | Rate limit | Limites globais e exceções por rota ou por usuário. |
| **Controle de acesso** | Perfis de acesso | Quem vê/edita cada tela do painel. |
| | Usuários do sistema | Quem entra no `/admin` da organização. |
| **Auditoria** | Auditoria | Histórico de alterações de configuração. |
| | Chamadas API | Log das invocações da API pública. |
| **Billing** | Billing | Custos, planos, saldos e consumo de tokens. |
| **Conta** | Perfil | Dados pessoais, senha e autenticação em dois fatores. |

---

## 3. Fluxo típico de operação

Ordem recomendada para publicar uma nova API:

```text
1. Conexão          → cadastre e teste o acesso ao banco
2. Query            → template + parâmetros; teste no painel
3. Definição de API → método, path, timeout; async se necessário
4. Mapeamento       → una API + query + conexão
5. Papel            → crie (ou reutilize) o papel da API
6. Permissão        → liberar a definição de API para o papel
7. Usuário da API   → vincule o papel; gere token; configure webhook se async
8. Validar          → chame a API com o token; confira “Chamadas API”
```

### Chamada síncrona vs assíncrona

- **Síncrona (padrão):** o gateway executa a query na mesma requisição e devolve o resultado no HTTP.
- **Assíncrona:** na definição de API, ative **Execução assíncrona**. A API responde **HTTP 202** com `jobId` e `statusUrl`; o processamento continua em segundo plano. O cliente consulta o status do job no **host da API pública** (não no painel `/admin`). Opcionalmente, configure **webhook** no usuário da API para receber o resultado ao concluir.

---

*Interface sujeita a evolução; rótulos e campos seguem a versão atual do painel OmniGateway.*
