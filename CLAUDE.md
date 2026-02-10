# 🤖 Instruções para Claude Code

## 📋 Contexto do Projeto

Este é um sistema de gerenciamento de tarefas e erros com agentes automatizados.

## 🎯 Agentes Ativos

### 1. TODO Manager (`docs/agents/TODO-MANAGER.md`)

**Responsabilidade:** Processar descrições de erros e adicionar ao TODO.md de forma estruturada.

**Como funciona:**
1. Usuário descreve erro livremente
2. Claude processa e estrutura a informação
3. Adiciona entrada formatada no `docs/TODO.md`

**Formato de entrada do usuário:**
- Texto livre descrevendo o erro/problema
- Exemplo: "Na rotina de atendimento ao cadastrar um cliente aparece o erro X"

**Formato de saída no TODO.md:**
```markdown
## ❌ [Título do erro]
**Data:** DD/MM/AAAA HH:MM
**Categoria:** [Categoria identificada]
**Prioridade:** [Alta/Média/Baixa]
**Status:** 🔴 Pendente / 🟡 Em andamento / 🟢 Resolvido

**Descrição:**
[Descrição detalhada e clara]

**Impacto:**
[Impacto do problema]

**Ações necessárias:**
- [ ] [Ação 1]
- [ ] [Ação 2]

---
```

## 📝 Regras Importantes

1. **Sempre estruturar** as entradas de TODO de forma consistente
2. **Inferir categoria** baseado no contexto (Atendimento, Sistema, Cadastro, etc.)
3. **Estimar prioridade** baseado no impacto descrito
4. **Adicionar ao final** do arquivo TODO.md preservando entradas anteriores
5. **Data/hora atual** do sistema

### 2. Vendas Manager (`docs/agents/VENDAS-MANAGER.md`)

**Responsabilidade:** Registrar vendas, transferências e calcular totais diários.

**Como funciona:**
1. Usuário informa número da venda, valor e forma de pagamento
2. Claude registra no histórico diário
3. Atualiza totais por forma de pagamento e saldo de caixa

**Formato de entrada do usuário:**
- "Venda #480, R$ 126,15, débito"
- "Recebi transferência de 200 reais"
- "Enviei 50 reais"

**Arquivo de registro:** `docs/VENDAS.md`

## 📝 Regras Importantes (Vendas Manager)

1. **Registrar** cada venda com número, valor e forma de pagamento
2. **Transferências** recebidas somam ao caixa dinheiro, enviadas subtraem
3. **Totais por forma de pagamento** atualizados a cada registro
4. **Saldo de caixa dinheiro** = vendas dinheiro + recebidas - enviadas
5. **Separar por dia** mantendo histórico

## 🔄 Próximos Agentes

Conforme necessário, novos agentes serão criados em `docs/agents/`

---

**Versão:** 1.1
**Criado em:** 06/02/2025
**Atualizado em:** 09/02/2026
