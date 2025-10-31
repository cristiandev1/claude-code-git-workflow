---
description: Inicia o processo de descoberta para remover código ou funcionalidade
---

# Remove Discovery Mode

Você está no modo **REMOVE DISCOVERY**. Seu objetivo é entender completamente o que precisa ser removido e as implicações ANTES de fazer qualquer alteração.

## IMPORTANTE: Criação de Branch

Antes de começar, execute:
```bash
git checkout -b remove/[nome-descritivo-da-remocao]
```

Use um nome descritivo e em kebab-case (ex: `remove/old-api`, `remove/deprecated-feature`)

## Processo:

1. **Identifique o que remover**:
   - Qual feature/seção/componente deve ser removido?
   - Por que está sendo removido?
   - Está obsoleto, duplicado, ou não é mais necessário?

2. **Entenda as dependências**:
   - Outras partes da aplicação dependem disso?
   - Existem integrações externas?
   - Há dados associados que precisam ser considerados?

3. **Impacto em usuários**:
   - Quem usa isso atualmente?
   - Como comunicar a remoção?
   - Há funcionalidade substituta?

4. **Limpeza necessária**:
   - Remover apenas código ou também dados?
   - Remover testes relacionados?
   - Atualizar documentação?
   - Remover dependências/pacotes não utilizados?

## Diretrizes:

- Faça perguntas sobre dependências e impacto
- Use AskUserQuestion para confirmar o escopo da remoção
- NÃO explore código ainda - foque em entender o contexto
- Seja cauteloso - remoções podem ter impactos inesperados
- Confirme seu entendimento antes de documentar

## Entrega:

Após entender completamente, crie o arquivo `.claude/context/current-task.md` com:

```markdown
# [Título da Remoção]

**Tipo:** Remove
**Data:** [data atual]

## O Que Será Removido
[Descrição clara do que será removido]

## Motivo da Remoção
[Por que isso está sendo removido]

## Dependências Conhecidas
- Dependência 1
- Dependência 2
...

## Impacto em Usuários
[Quem usa, como será afetado, comunicação necessária]

## Escopo da Remoção
- [ ] Código
- [ ] Testes
- [ ] Dados/Migrations
- [ ] Documentação
- [ ] Dependências/Pacotes
- [ ] Configurações

## Funcionalidade Substituta
[Se houver alternativa ou migração necessária]

## Precauções
[Cuidados especiais, backups, rollback plans]

## Notas Adicionais
[Qualquer outra informação relevante]
```

Ao finalizar, informe: "✓ Contexto documentado em .claude/context/current-task.md. Execute `/execute` quando estiver pronto para ver o plano técnico."

**Nota:** O comando `/execute` irá automaticamente detectar e seguir os padrões do seu projeto (arquitetura, design patterns, convenções de código, testes, etc.). Se quiser revisar ou atualizar os padrões do projeto, execute `/pattern` antes.

## Após implementação e commit:

Quando estiver pronto para fazer push e finalizar:
1. Faça o commit das mudanças
2. Execute: `git push -u origin remove/[nome-da-branch]`
3. Limpe o arquivo de contexto: remova o conteúdo de `.claude/context/current-task.md`
4. Volte para a branch principal se necessário: `git checkout main`
