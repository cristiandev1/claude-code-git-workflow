---
description: Inicia o processo de descoberta para corrigir um bug ou problema
---

# Fix Discovery Mode

Você está no modo **FIX DISCOVERY**. Seu objetivo é entender completamente o problema ANTES de implementar a correção.

## IMPORTANTE: Criação de Branch

Antes de começar, execute:
```bash
git checkout -b fix/[nome-descritivo-do-bug]
```

Use um nome descritivo e em kebab-case (ex: `fix/login-validation`, `fix/payment-error`)

## Processo:

1. **Identifique o problema**:
   - Qual é o comportamento atual?
   - Qual deveria ser o comportamento esperado?
   - Como reproduzir o problema?
   - O problema ocorre sempre ou em situações específicas?

2. **Entenda o impacto**:
   - Quem é afetado?
   - Com que frequência ocorre?
   - Há workarounds atualmente?
   - É crítico ou pode ser planejado?

3. **Contexto técnico inicial**:
   - Em que parte da aplicação ocorre?
   - Desde quando existe esse problema?
   - Mudanças recentes podem ter causado?

4. **Requisitos da correção**:
   - O que precisa ser corrigido exatamente?
   - Há restrições ou considerações especiais?
   - Precisa de testes específicos?

## Diretrizes:

- Faça perguntas para entender o problema completamente
- Peça exemplos concretos e passos de reprodução
- Use AskUserQuestion para oferecer opções quando relevante
- NÃO explore código ainda - foque em entender o problema
- Confirme seu entendimento antes de documentar

## Entrega:

Após entender completamente, crie o arquivo `.claude/context/current-task.md` com:

```markdown
# [Título do Fix]

**Tipo:** Fix
**Data:** [data atual]

## Problema Atual
[Descrição do comportamento incorreto]

## Comportamento Esperado
[Como deveria funcionar]

## Passos para Reproduzir
1. Passo 1
2. Passo 2
...

## Contexto
[Quando começou, quem afeta, frequência, etc.]

## Requisitos da Correção
- O que deve ser corrigido
- O que NÃO deve ser alterado
- Validações necessárias

## Impacto e Prioridade
[Gravidade, usuários afetados, urgência]

## Notas Adicionais
[Qualquer outra informação relevante]
```

Ao finalizar, informe: "✓ Contexto documentado em .claude/context/current-task.md. Execute `/execute` quando estiver pronto para ver o plano técnico."

## Após implementação e commit:

Quando estiver pronto para fazer push e finalizar:
1. Faça o commit das mudanças
2. Execute: `git push -u origin fix/[nome-da-branch]`
3. Limpe o arquivo de contexto: remova o conteúdo de `.claude/context/current-task.md`
4. Volte para a branch principal se necessário: `git checkout main`
