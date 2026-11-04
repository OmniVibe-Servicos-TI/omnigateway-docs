---
title: Auditoria e chamadas
layout: default
parent: Manual do usuário
nav_order: 6
---

# Auditoria e chamadas

## 17. Auditoria

![Auditoria de configuração]({{ site.baseurl }}/assets/images/guia/06-auditoria.png)

Registro de alterações de configuração feitas no painel.

| Filtro / coluna | Utilização |
|-----------------|------------|
| **Busca** | Texto livre (tabela, usuário, id do registro). |
| **Tabela** | Entidade alterada. |
| **Operação** | INSERT, UPDATE ou DELETE. |
| **Usuário do painel** | Quem fez a alteração. |
| **De / Até** | Período. |
| **Data/Hora, Record ID, Snapshot** | Momento, identificador e resumo do que mudou. |

Use para investigar “quem mudou o quê” em conexões, APIs, permissões, etc.

---

## 18. Chamadas API (log de invocações)

Monitoramento das requisições à API pública.

### 18.1 Indicadores e filtros

![Log de chamadas da API]({{ site.baseurl }}/assets/images/guia/06-chamadas-api.png)

| Elemento | Utilização |
|----------|------------|
| **Total / Latências / Erros** | Resumo do filtro atual ou da página. |
| **Busca** | Correlation id, path, trechos de parâmetros, etc. |
| **Usuários da API** | Filtra pelo consumidor. |
| **Definição de API** | Filtra pela rota. |
| **Tipo** | Síncrono, Enfileirado (202) ou Job concluído. |
| **De / Até** | Período. |

### 18.2 Colunas da tabela

| Coluna | Utilização |
|--------|------------|
| **Data/Hora** | Momento da invocação. |
| **Método / Rota** | Endpoint chamado. |
| **Usuário** | Usuário da API (quando autenticado). |
| **Status** | Código HTTP. |
| **Erro** | Código de erro classificado (quando houver). |
| **HTTP ms / DB ms** | Tempos medidos. |
| **Tipo** | Síncrono / fila / job concluído. |
| **Req / Resp** | Tamanho estimado dos corpos. |
| **Detalhes (Ver)** | Abre o diálogo completo. |

### 18.3 Detalhe da chamada

| Seção | Utilização |
|-------|------------|
| **Correlation / Job** | Identificadores para cruzar com logs externos e status do job. |
| **Body request/response (estimado)** | Tamanho aproximado dos corpos. |
| **Parâmetros (sanitizados)** | Parâmetros gravados sem segredos. |
| **Quadro de diagnóstico** | Status, código de erro, tipo da chamada e textos de orientação (ex.: validação, timeout, fila 202, billing). |
| **Steps / tempos** | Tempos por etapa, quando a execução registrou steps (ausente em “só enfileirou”). |

**Nota:** o log guarda status e código de erro; a mensagem completa do banco (ex.: texto ORA) pode não aparecer aqui — use o correlation id e, em jobs, o status/`async_completed` ou o webhook.

---

*Interface sujeita a evolução; rótulos e campos seguem a versão atual do painel OmniGateway.*
