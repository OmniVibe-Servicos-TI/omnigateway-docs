---
title: Operação
layout: default
parent: Manual do usuário
nav_order: 3
---

# Operação

## 6. Dashboard (`/`)

![Dashboard da organização]({{ site.baseurl }}/assets/images/manual/03-dashboard.png)

Visão geral da organização ativa.

| Elemento | Utilização |
|----------|------------|
| **Cards de KPI** | Contagens de conexões, APIs, queries, mapeamentos, papéis, usuários da API e permissões (em geral clicáveis para a tela correspondente). |
| **Rastreamento de chamadas à API** | Atalho para o log de invocações. |
| **Atividade recente** | Últimas alterações de configuração (operação, tabela, usuário, data). |
| **Top rotas** | Rotas mais chamadas (path público, quantidade, tempo). |

Use o dashboard para checar se a configuração está completa e se há tráfego nas rotas.

---

## 7. Conexões

Cadastro dos backends (Oracle, PostgreSQL, MySQL, SQL Server, MongoDB, etc.) usados pelos mapeamentos.

### 7.1 Lista

![Lista de conexões]({{ site.baseurl }}/assets/images/manual/03-conexoes-lista.png)

| Filtro / coluna | Utilização |
|-----------------|------------|
| **Busca** | Filtra por nome, host, database ou usuário. |
| **Tipo de banco** | Restringe ao motor escolhido. |
| **Todas / Apenas ativas / Apenas inativas** | Filtra pelo status. |
| **Nome, Tipo, Host/database, Usuário, Status, Atualizada em** | Identificação e estado. |
| **Ações** | Editar, excluir (se permitido), duplicar (gravação). |

### 7.2 Formulário (nova / editar)

![Formulário de conexão]({{ site.baseurl }}/assets/images/manual/03-conexoes-formulario.png)

| Campo | Utilização |
|-------|------------|
| **Nome** | Identificação amigável da conexão no painel. |
| **Tipo de banco** | Define o driver e quais queries são compatíveis. |
| **Host** | Endereço do servidor de banco. |
| **Porta** | Porta TCP do serviço. |
| **Database** | Nome do banco / serviço (conforme o tipo). |
| **Usuário** | Usuário de conexão no banco. |
| **Senha** | Obrigatória na criação; na edição, deixe vazio para manter a atual. |
| **Conexão ativa** | Só conexões ativas devem ser usadas em produção. |
| **Parâmetros extras (JSON)** | Opções adicionais do motor (SSL, service name Oracle, etc.). Há ajuda contextual por tipo. |

**Ações:** **Testar conexão** (valida acesso sem salvar o fluxo completo), **Cancelar**, **Criar** / **Salvar**.

---

## 8. Queries

Templates executados pelo gateway, com validação de parâmetros.

### 8.1 Lista

![Lista de queries]({{ site.baseurl }}/assets/images/manual/03-queries-lista.png)

| Filtro / coluna | Utilização |
|-----------------|------------|
| **Busca** | Localiza por nome. |
| **Ativas / Inativas** | Filtra status. |
| **Nome, Tipo, Banco, Coleção, Status, Atualizada em** | Resumo da query. |

### 8.2 Formulário

![Formulário de query]({{ site.baseurl }}/assets/images/manual/03-queries-formulario.png)

| Campo | Utilização |
|-------|------------|
| **Nome** | Nome da query no painel e nos mapeamentos. |
| **Banco alvo** | Tipo de banco compatível (deve casar com a conexão no mapeamento). |
| **Tipo de query** | SQL ou operação MongoDB (conforme o banco). |
| **Coleção (MongoDB)** | Coleção alvo quando aplicável. |
| **Query ativa** | Desative para impedir uso sem apagar o cadastro. |
| **Template (SQL ou JSON)** | Texto da consulta/comando. Use **Formatar** para organizar. |
| **paramSchema (JSON)** | Esquema dos parâmetros aceitos (tipos, obrigatórios, binds Oracle). Editor visual disponível. |
| **Descrição** | Documentação interna para a equipe. |

### 8.3 Editor visual do paramSchema

![Editor visual do paramSchema]({{ site.baseurl }}/assets/images/manual/03-queries-param-schema.png)

| Campo | Utilização |
|-------|------------|
| **Permitir propriedades extras** | Se desligado, parâmetros não declarados são rejeitados. |
| **Nome** | Nome do parâmetro (deve coincidir com o bind no SQL, ex.: `:TP_ID`). |
| **Tipo** | string, number, integer ou boolean. |
| **Required** | Obriga o cliente a enviar o parâmetro. |
| **Default** | Valor padrão quando omitido. |
| **minimum / maximum** | Limites numéricos. |
| **Bind Oracle** (quando Oracle) | Direção (`in` / `out` / `inout`), tipo (`string`, `number`, `date`, `clob`, `cursor`, etc.) e tamanho máximo quando necessário. |

Parâmetros **OUT** / **cursor** não são enviados pelo cliente; o gateway os preenche na resposta (`outParams`).

**Aplicar no JSON** grava o editor no campo `paramSchema`; **Recarregar do JSON** atualiza o editor a partir do texto.

### 8.4 Testar query

![Diálogo Testar query]({{ site.baseurl }}/assets/images/manual/03-queries-testar.png)

| Campo | Utilização |
|-------|------------|
| **Conexão** | Conexão do mesmo tipo de banco da query. |
| **Parâmetros (JSON)** | Valores dos parâmetros IN para o teste. |
| **Executar teste** | Roda a query e mostra resultado / mensagem / `outParams`. |

---

## 9. Definições de API

Define o contrato HTTP da rota pública (ainda sem ligar ao banco — isso é o mapeamento).

### 9.1 Lista

![Lista de definições de API]({{ site.baseurl }}/assets/images/manual/03-apis-lista.png)

| Filtro / coluna | Utilização |
|-----------------|------------|
| **Busca** | Filtra método/path. |
| **Ativas / Inativas** | Status. |
| **Método, API Path, Etapas, Timeout, Async, Status** | Resumo da definição. O path costuma aparecer com o prefixo `/{slug da organização}`. |

### 9.2 Formulário

![Formulário de definição de API]({{ site.baseurl }}/assets/images/manual/03-apis-formulario.png)

| Campo | Utilização |
|-------|------------|
| **Método** | GET, POST, PUT, PATCH, DELETE, etc. |
| **Path** | Caminho relativo da API (o slug da organização é prefixado automaticamente na URL pública). |
| **Timeout (ms)** | Tempo máximo de espera da execução síncrona (ou da etapa no worker). |
| **Ativa** | Rotas inativas não devem ser invocáveis. |
| **Execução assíncrona** | Se ativo, a chamada é enfileirada (HTTP 202) em vez de executar no request. |
| **Descrição** | Documentação da rota para a equipe. |

URL pública típica: `{método} https://{host-da-api}/{slug-org}{path}` com o header de token do usuário da API.

---

## 10. Mapeamento de rota

Associa uma **definição de API** a uma **query** e a uma **conexão**. Uma API pode ter várias etapas (vários mapeamentos com ordens diferentes).

### 10.1 Lista

![Lista de mapeamentos de rota]({{ site.baseurl }}/assets/images/manual/03-mapeamentos-lista.png)

| Coluna | Utilização |
|--------|------------|
| **Método / API Path** | Rota pública associada. |
| **Conexão / Query** | Onde e o que será executado. |
| **Ordem** | Sequência das etapas. |
| **Status** | Ativo ou inativo. |

### 10.2 Formulário

![Formulário de mapeamento de rota]({{ site.baseurl }}/assets/images/manual/03-mapeamentos-formulario.png)

| Campo | Utilização |
|-------|------------|
| **API Path** | Escolha da definição de API. |
| **Conexão** | Backend que executará a query. |
| **Query** | Lista filtrada pelo tipo da conexão escolhida. |
| **Ordem de execução** | Número da etapa (1, 2, …). |
| **Chave do resultado** | Nome sob o qual o resultado da etapa aparece no agregado (ex.: `step_1`). |
| **Mapeamento ativo** | Desative para suspender a etapa. |
| **Fallback** | Indica etapa de contingência conforme a regra do sistema. |
| **Condição (JSON)** | Condição opcional para executar a etapa (formato JSON). |

Sem mapeamento ativo, a definição de API existe mas não executa query.

---

*Interface sujeita a evolução; rótulos e campos seguem a versão atual do painel OmniGateway.*
