---
description: Inicia o processo de análise técnica do codebase
---

# Analyze Mode

Você está no modo **ANALYZE**. Seu objetivo é realizar uma análise técnica profunda do codebase ANTES de propor mudanças.

## IMPORTANTE: Criação de Branch

Antes de começar, execute:
```bash
git checkout -b analyze/[nome-descritivo-da-analise]
```

Use um nome descritivo e em kebab-case (ex: `analyze/performance`, `analyze/security-audit`)

## Processo:

1. **Entenda o escopo**:
   - O que precisa ser analisado?
   - Qual é o objetivo da análise?
   - Há algum problema específico ou é exploratório?

2. **Análise técnica**:
   - Arquitetura atual
   - Padrões de design utilizados
   - Performance e otimizações
   - Segurança e vulnerabilidades
   - Qualidade do código
   - Débito técnico

3. **Identificação de problemas**:
   - Bugs potenciais
   - Code smells
   - Anti-patterns
   - Gargalos de performance
   - Problemas de manutenibilidade

4. **Oportunidades de melhoria**:
   - Refatorações sugeridas
   - Otimizações possíveis
   - Melhorias de arquitetura
   - Testes faltantes

## Diretrizes:

- Faça perguntas para entender o escopo da análise
- Use a ferramenta Task com subagent_type=Explore para investigar o código
- Seja objetivo e técnico nas suas observações
- Priorize problemas por severidade
- Sugira soluções práticas

## Entrega:

Após a análise, crie o arquivo `.claude/context/current-task.md` com:

```markdown
# Análise: [Título da Análise]

**Tipo:** Análise
**Data:** [data atual]

## Escopo da Análise
[O que foi analisado e por quê]

## Arquitetura Atual
[Descrição da arquitetura encontrada]

## Problemas Identificados

### Críticos
- Problema 1
- Problema 2

### Médios
- Problema 1
- Problema 2

### Baixos
- Problema 1
- Problema 2

## Oportunidades de Melhoria
- Melhoria 1
- Melhoria 2

## Recomendações

### Imediatas
1. Ação 1
2. Ação 2

### Curto Prazo
1. Ação 1
2. Ação 2

### Longo Prazo
1. Ação 1
2. Ação 2

## Métricas e Observações
[Dados técnicos relevantes: performance, cobertura de testes, complexidade, etc.]

## Conclusão
[Resumo executivo da análise]
```

Ao finalizar, informe: "✓ Análise documentada em .claude/context/current-task.md. Execute `/execute` se quiser criar um plano de implementação das melhorias."

## Após implementação e commit:

Quando estiver pronto para fazer push e finalizar:
1. Faça o commit das mudanças (se houver)
2. Execute: `git push -u origin analyze/[nome-da-branch]`
3. Limpe o arquivo de contexto: remova o conteúdo de `.claude/context/current-task.md`
4. Volte para a branch principal se necessário: `git checkout main`
