# Contribuindo para Claude Code Git Workflow

Antes de mais nada, obrigado por considerar contribuir! 🎉

Este projeto visa ajudar desenvolvedores a trabalhar de forma mais eficaz com Claude Code, fornecendo workflows Git estruturados.

## Como Posso Contribuir?

### 1. Compartilhe Suas Ideias de Comandos

Tem uma ideia para um comando de workflow útil? Adoraríamos ouvir!

**Abra uma issue com:**
- Nome do comando (ex: `/test`, `/refactor`, `/hotfix`)
- Caso de uso: Quando desenvolvedores usariam isso?
- Passos do workflow: O que deveria acontecer?
- Padrão de branch: Qual convenção de nomenclatura?

### 2. Melhore Comandos Existentes

Encontrou uma forma de melhorar um comando?

**Submeta um PR com:**
- O que você melhorou e por quê
- Exemplo da melhoria em ação
- Documentação atualizada se necessário

### 3. Adicione Novos Comandos

Quer contribuir com um novo comando completo?

**Crie um PR com:**
1. Novo arquivo de comando em `.claude/commands/seu-comando.md`
2. Documentação no README.md
3. Exemplo de caso de uso
4. Teste primeiro com Claude Code!

### 4. Melhore a Documentação

- Corrija erros de digitação
- Adicione exemplos
- Clarifique instruções
- Traduza para outros idiomas

### 5. Compartilhe Exemplos do Mundo Real

Ajude outros a aprender compartilhando:
- Como você usou estes workflows
- Problemas que resolveu
- Adaptações que fez

## Estrutura de Comando

Ao criar um novo comando, siga esta estrutura:

```markdown
---
description: Breve descrição do que este comando faz
---

# Modo Nome do Comando

Você está no modo **NOME DO COMANDO**. [Declaração de propósito]

## IMPORTANTE: Criação de Branch

Antes de começar, execute:
\```bash
git checkout -b [tipo]/[nome-descritivo]
\```

## Processo:

1. **Fase de Descoberta:**
   - Quais perguntas fazer
   - Quais informações coletar

2. **Documentação:**
   - O que documentar
   - Onde salvar

3. **Próximos Passos:**
   - O que acontece após a descoberta

## Entrega:

Crie `.claude/context/current-task.md` com:

\```markdown
# [Título da Tarefa]

**Tipo:** [Tipo do Comando]
**Data:** [Data Atual]

[Estrutura do template...]
\```

## Após Implementação:

1. Commitar mudanças
2. Push para branch
3. Limpar current-task.md
4. Retornar para main se necessário
```

## Processo de Pull Request

1. **Faça fork do repo**
2. **Crie uma branch de feature:** `git checkout -b feature/sua-feature`
3. **Faça suas mudanças**
4. **Teste com Claude Code** - Garanta que o comando funciona
5. **Atualize a documentação** - Adicione ao README.md
6. **Commit com mensagens semânticas:**
   - `feat: adiciona comando /test para workflow TDD`
   - `docs: melhora exemplos do comando /feature`
   - `fix: corrige padrão de branch no /analyze`
7. **Push para seu fork**
8. **Abra um Pull Request**

## Checklist de PR

- [ ] Comando testado com Claude Code
- [ ] Documentação atualizada no README.md
- [ ] Exemplos fornecidos
- [ ] Segue estrutura de comando existente
- [ ] Mensagens de commit claras
- [ ] Sem breaking changes (ou claramente documentadas)

## Código de Conduta

### Nosso Compromisso

Este é um projeto acolhedor e inclusivo. Nos comprometemos a tornar a participação livre de assédio para todos.

### Nossos Padrões

**Comportamento positivo:**
- Ser respeitoso e construtivo
- Aceitar feedback graciosamente
- Focar no que é melhor para a comunidade
- Mostrar empatia

**Comportamento inaceitável:**
- Assédio ou linguagem discriminatória
- Trolling ou comentários insultuosos
- Publicar informações privadas de outros
- Conduta não profissional

## Dúvidas?

- Abra uma issue com a label `pergunta`
- Aba de discussões (se habilitada)

## Reconhecimento

Contribuidores serão reconhecidos em:
- Seção de contribuidores do README.md
- Notas de release
- Documentação do projeto

## Licença

Ao contribuir, você concorda que suas contribuições serão licenciadas sob a Licença MIT.

---

Obrigado por ajudar a tornar workflows de desenvolvimento melhores para todos! 🚀
