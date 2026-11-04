---
title: Boas práticas e glossário
layout: default
parent: Manual do usuário
nav_order: 8
---

# Boas práticas e glossário

## 20. Boas práticas de operação

1. **Teste a conexão** antes de criar mapeamentos.
2. **Teste a query** no painel com parâmetros reais (ou próximos) antes de liberar a API.
3. Mantenha **paramSchema** alinhado aos binds do SQL; marque OUT/cursor corretamente no Oracle.
4. Publique na ordem: conexão → query → API → mapeamento → permissão → token.
5. Use **papéis** granulares e liberte só as APIs necessárias.
6. Em rotas longas, prefira **execução assíncrona** + webhook ou polling do job.
7. Monitore **Chamadas API** após mudanças; use o quadro de diagnóstico do detalhe.
8. Revise **Auditoria** quando algo “parar de funcionar” após alteração de config.
9. Não compartilhe tokens em canais inseguros; rotacione com identificação clara e validade.
10. Desative (em vez de apagar) registros que ainda precisam de histórico.

---

## 21. Glossário rápido

| Termo | Significado |
|-------|-------------|
| **Organização** | Tenant; escopo de toda a configuração no painel. |
| **Slug** | Identificador curto da org no path público da API. |
| **Conexão** | Credenciais e host de um banco. |
| **Query** | Template + parâmetros a executar. |
| **Definição de API** | Método + path HTTP publicados. |
| **Mapeamento** | Liga API + query + conexão. |
| **Usuário da API** | Consumidor externo (tokens). |
| **Papel da API** | Grupo de permissões do consumidor. |
| **Perfil de acesso** | Permissões das telas do painel. |
| **Usuário do sistema** | Pessoa que entra no `/admin`. |
| **Job** | Execução assíncrona enfileirada. |
| **Correlation id** | Identificador para rastrear uma chamada. |

---

*Interface sujeita a evolução; rótulos e campos seguem a versão atual do painel OmniGateway.*

---

*Interface sujeita a evolução; rótulos e campos seguem a versão atual do painel OmniGateway.*
