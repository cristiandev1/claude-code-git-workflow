---
description: Inicia o processo de descoberta para criar uma nova feature
---

# Feature Discovery Mode

Você está no modo **FEATURE DISCOVERY**. Seu objetivo é entender completamente o que precisa ser desenvolvido ANTES de implementar qualquer código.

## IMPORTANTE: Criação de Branch

Antes de começar, execute:
```bash
git checkout -b feature/[nome-descritivo-da-feature]
```

Use um nome descritivo e em kebab-case (ex: `feature/user-authentication`, `feature/payment-integration`)

## Processo:

1. **Entenda o objetivo**:
   - Qual é o propósito da feature?
   - Que problema ela resolve?
   - Quem vai usar isso?

2. **Detalhes funcionais**:
   - Como deve funcionar?
   - Quais são os fluxos principais?
   - Quais são os edge cases?
   - Como tratar erros e validações?

3. **UI/UX (se aplicável)**:
   - Como deve ser a interface?
   - Onde ela se encaixa na aplicação atual?
   - Qual é a experiência esperada do usuário?

4. **Integrações**:
   - Depende de APIs existentes?
   - Precisa de novos endpoints?
   - Integra com outras features?

## Diretrizes:

- Faça perguntas abertas para entender o contexto
- Use a ferramenta AskUserQuestion para oferecer opções quando relevante
- NÃO explore código ainda - foque no produto
- Seja conversacional e faça uma pergunta por vez quando necessário
- Confirme seu entendimento antes de documentar

## Entrega:

Após entender completamente, crie o arquivo `.claude/context/current-task.md` com:

```markdown
# [Título da Feature]

**Tipo:** Feature
**Data:** [data atual]

## Contexto e Objetivo
[Por que essa feature existe e o que ela resolve]

## Requisitos Funcionais
- Requisito 1
- Requisito 2
- ...

## Fluxos Principais
1. Fluxo A
2. Fluxo B
...

## Edge Cases e Validações
- Edge case 1
- Validação 1
...

## UI/UX
[Descrição da interface e experiência esperada]

## Integrações
[APIs, serviços, outras features envolvidas]

## Notas Adicionais
[Qualquer outra informação relevante]
```

Ao finalizar, informe: "✓ Contexto documentado em .claude/context/current-task.md. Execute `/execute` quando estiver pronto para ver o plano técnico."

## Após implementação e commit:

Quando estiver pronto para fazer push e finalizar:
1. Faça o commit das mudanças
2. Execute: `git push -u origin feature/[nome-da-branch]`
3. Limpe o arquivo de contexto: remova o conteúdo de `.claude/context/current-task.md`
4. Volte para a branch principal se necessário: `git checkout main`
