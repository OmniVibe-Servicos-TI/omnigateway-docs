---
title: Billing
layout: default
parent: Manual do usuário
nav_order: 7
---

# Billing

## 19. Billing

Gestão de consumo e cotas da organização (quando habilitado no ambiente).

Abas principais:

### 19.1 Configuração

![Billing — configuração]({{ site.baseurl }}/assets/images/guia/07-billing-configuracao.png)

| Campo | Utilização |
|-------|------------|
| **Billing ativo** | Liga a cobrança/contabilização. |
| **Modo quando saldo zera** | Apenas alerta ou **bloquear** novas chamadas (HTTP 402). |
| **Tokens mensais padrão (sem plano)** | Cota padrão para quem não tem plano específico. |

### 19.2 Custos globais

![Billing — custos globais]({{ site.baseurl }}/assets/images/guia/07-billing-custos.png)

Tabela de preços vigentes (base por requisição, por ms de banco, por byte) com validade. No cadastro novo: **Válido a partir de**, valores unitários e **Notas**.

### 19.3 Overrides de rota (billing)

![Billing — overrides de rota]({{ site.baseurl }}/assets/images/guia/07-billing-overrides.png)

| Campo | Utilização |
|-------|------------|
| **Rota (API)** | Definição com custo diferenciado. |
| **Válido a partir de** | Início da vigência. |
| **Multiplicador** | Fator sobre o custo padrão. |

### 19.4 Planos por usuário

![Billing — planos por usuário]({{ site.baseurl }}/assets/images/guia/07-billing-planos.png)

| Campo | Utilização |
|-------|------------|
| **Usuário da API** | Consumidor. |
| **Válido a partir de** | Início do plano. |
| **Tokens mensais** | Cota do período. |
| **Multiplicador** | Ajuste de custo. |

### 19.5 Saldos

![Billing — saldos]({{ site.baseurl }}/assets/images/guia/07-billing-saldos.png)

| Campo / coluna | Utilização |
|----------------|------------|
| **Mês de faturamento** | Período consultado. |
| **Usuário (opcional)** | Filtro. |
| **Concedidos / Usados / Restantes** | Posição do saldo. |
| **Recarregar** | Ajusta **Tokens concedidos no período**. |

### 19.6 Consumo

![Billing — consumo]({{ site.baseurl }}/assets/images/guia/07-billing-consumo.png)

Ledger de uso: quando, usuário, rota, ms de DB, bytes, tipo (incluso / sob demanda) e tokens debitados.

---

*Interface sujeita a evolução; rótulos e campos seguem a versão atual do painel OmniGateway.*
