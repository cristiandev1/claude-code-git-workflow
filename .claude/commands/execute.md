---
description: Analisa o contexto e cria um plano técnico detalhado para implementação
---

# Execute Mode

Você está no modo **EXECUTE**. Agora você vai analisar o contexto documentado e criar um plano técnico detalhado.

## IMPORTANTE: Verificação de Branch

Antes de começar:
1. Verifique se você está na branch correta (feature/*, fix/*, remove/*, analyze/*)
2. Execute `git branch` para confirmar
3. Se não estiver em uma branch de trabalho, crie uma apropriada antes de continuar

## Processo:

1. **Leia o contexto**:
   - Leia o arquivo `.claude/context/current-task.md`
   - Se não existir, informe o usuário para rodar `/feature`, `/fix`, ou `/remove` primeiro

2. **Explore o codebase**:
   - Use o Task tool com subagent_type=Explore para entender a arquitetura
   - Identifique arquivos, componentes e padrões relevantes
   - Entenda como o código atual funciona

3. **Crie o plano técnico**:
   - Arquivos que serão criados/modificados/removidos
   - Componentes, funções e hooks envolvidos
   - Fluxo de dados e integrações
   - Estrutura de testes necessários
   - Considerações de performance, segurança, acessibilidade
   - Migrações ou mudanças de dados (se aplicável)

4. **Use TodoWrite**:
   - Crie uma lista de tarefas clara e detalhada
   - Organize em ordem lógica de implementação
   - Seja específico em cada item

5. **Apresente o plano**:
   - Mostre o plano técnico de forma clara
   - Explique suas decisões técnicas
   - Destaque pontos que precisam de atenção especial
   - Mencione trade-offs se houver

6. **AGUARDE CONFIRMAÇÃO**:
   - Pergunte se o usuário quer ajustar algo no plano
   - Ofereça alternativas se houver
   - **NÃO implemente nada ainda**
   - Só comece a implementar após confirmação explícita do usuário

## Formato da apresentação:

```
## Análise Técnica

[Resumo da análise do codebase e decisões arquiteturais]

## Arquivos Envolvidos

### Criar:
- arquivo1.ts - Descrição
- arquivo2.tsx - Descrição

### Modificar:
- arquivo3.ts:123 - O que será alterado
- arquivo4.tsx:45 - O que será alterado

### Remover:
- arquivo5.ts - Por que será removido

## Abordagem Técnica

[Explicação detalhada de como será implementado]

## Fluxo de Dados

[Como os dados fluirão pela aplicação]

## Testes

[Estratégia de testes e casos a cobrir]

## Considerações

[Performance, segurança, acessibilidade, etc.]

## Plano de Implementação

[Lista de tarefas criada com TodoWrite]

---

O plano está pronto. Você quer:
1. Começar a implementação
2. Ajustar alguma parte do plano
3. Discutir alternativas técnicas
```

## Diretrizes:

- Seja detalhado mas conciso
- Explique o "porquê" das decisões técnicas
- Considere a arquitetura existente do projeto
- Use o Task tool para explorar quando necessário
- NÃO faça suposições - se algo não está claro no contexto, pergunte
- Priorize código limpo, testável e manutenível
- **NUNCA implemente antes da aprovação do usuário**

## Após implementação e commit:

Quando estiver pronto para fazer push e finalizar:
1. Faça commit das mudanças com mensagem descritiva
2. Execute: `git push -u origin [nome-da-branch-atual]`
3. Limpe o arquivo de contexto executando:
   ```bash
   echo "" > .claude/context/current-task.md
   ```
4. Volte para a branch principal: `git checkout main`
5. Crie um Pull Request se necessário
