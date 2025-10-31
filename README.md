# Claude Code Git Workflow

> Um sistema de workflow Git estruturado e guiado por descoberta para Claude Code que ajuda times a construir software melhor através de planejamento cuidadoso e padrões consistentes de branching.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code](https://img.shields.io/badge/Claude_Code-Compatible-blue.svg)](https://docs.claude.com/pt/docs/claude-code)

## 🎯 O Problema

O desenvolvimento tradicional frequentemente segue este padrão quebrado:
1. Recebe uma tarefa
2. Começa a codificar imediatamente
3. Percebe que não entendeu os requisitos
4. Refatora múltiplas vezes
5. Histórico Git bagunçado com commits "fix", "oops", "final fix"

Este workflow introduz as fases **Descoberta → Planejamento → Execução**, garantindo que você entenda o que está construindo antes de construir.

## ✨ O Que Isso Fornece

Um conjunto completo de comandos slash para Claude Code que:

- ✅ **Força descoberta antes de codificar** - Entenda os requisitos primeiro
- ✅ **Branching Git automático** - Padrões consistentes `feature/`, `fix/`, `remove/`, `analyze/`
- ✅ **Documentação viva** - Contexto preservado em `current-task.md`
- ✅ **Planejamento técnico** - Crie planos detalhados de implementação antes de codificar
- ✅ **Detecção automática de padrões** - Analisa e mantém consistência arquitetural e de código
- ✅ **Workflow limpo** - Limpeza automática após conclusão da tarefa

## 📦 Instalação

### Configuração Rápida

1. **Copie a pasta `.claude` para seu projeto:**

```bash
# Clone este repositório
git clone https://github.com/cristiandev1/claude-code-git-workflow.git

# Copie para seu projeto
cp -r claude-code-git-workflow/.claude seu-projeto/.claude

# Ou baixe apenas a pasta .claude do GitHub
```

2. **Pronto!** Claude Code detectará os comandos automaticamente.

### O Que É Instalado

```
seu-projeto/
└── .claude/
    ├── commands/
    │   ├── feature.md      # Criar novas features
    │   ├── fix.md          # Corrigir bugs
    │   ├── remove.md       # Remover código/features
    │   ├── analyze.md      # Análise técnica
    │   ├── pattern.md      # Detectar padrões do projeto (NOVO!)
    │   ├── execute.md      # Criar & executar plano técnico
    │   └── README.md       # Documentação dos comandos
    └── context/
        ├── .gitignore           # Ignorar current-task.md
        ├── .gitkeep             # Rastrear estrutura de diretório
        ├── current-task.md      # Contexto da tarefa atual (temporário)
        └── project-patterns.md  # Padrões do projeto (deve ser commitado)
```

## 🚀 Uso

### Comandos Disponíveis

| Comando | Propósito | Padrão de Branch | Quando Usar |
|---------|-----------|------------------|-------------|
| `/feature` | Criar nova funcionalidade | `feature/[nome]` | Adicionar novas capacidades |
| `/fix` | Corrigir bugs ou problemas | `fix/[nome]` | Corrigir comportamento quebrado |
| `/remove` | Remover código/features | `remove/[nome]` | Deletar código obsoleto |
| `/analyze` | Análise técnica | `analyze/[nome]` | Auditorias de código, planos de refatoração |
| `/pattern` | Detectar padrões do projeto | *(qualquer branch)* | Documentar arquitetura e convenções |
| `/execute` | Executar plano técnico | *(branch atual)* | Após descoberta estar completa |

### Detecção Automática de Padrões

O sistema agora **detecta automaticamente** os padrões do seu projeto e garante consistência em todas as implementações.

#### Como Funciona

1. **Primeira vez usando `/execute`**:
   - Detecta automaticamente arquitetura, design patterns, convenções de código, e padrões de teste
   - Cria `.claude/context/project-patterns.md` com a análise completa
   - Usa esses padrões no plano técnico

2. **Usos subsequentes**:
   - Consulta `project-patterns.md` automaticamente
   - Garante que todo código novo segue os mesmos padrões

3. **Comando `/pattern` (opcional)**:
   - Execute quando quiser atualizar ou revisar a análise de padrões
   - Útil após mudanças significativas no projeto

#### O Que é Detectado Automaticamente

- **Arquitetura**: MVC, Clean Architecture, Hexagonal, DDD, etc.
- **Design Patterns**: Repository, Factory, Singleton, DI, etc.
- **Naming Conventions**: camelCase, PascalCase, kebab-case, etc.
- **Estrutura de Pastas**: Por feature, por tipo, co-location, etc.
- **Stack Tecnológica**: Frameworks, bibliotecas, versões
- **Padrões de Teste**: Framework, estrutura, estilo (AAA, Given-When-Then)
- **Code Quality**: Linters, formatters, métricas
- **State Management**: Redux, Zustand, Context API, etc.

### Exemplo de Workflow Completo

#### 1. Iniciar Nova Feature

```
Usuário: /feature
Claude: Qual feature você quer construir?
Usuário: Quero adicionar autenticação com Google OAuth

Claude: [Faz perguntas sobre requisitos, casos extremos, etc.]
Claude: ✓ Contexto documentado. Execute /execute quando estiver pronto para o plano técnico.
```

**O que aconteceu:**
- Criou branch: `feature/google-oauth`
- Documentou requisitos em `.claude/context/current-task.md`
- Pronto para fase de planejamento

#### 2. Criar Plano Técnico

```
Usuário: /execute
Claude: [Explora codebase, cria plano técnico detalhado]

## Plano Técnico
### Arquivos a Criar:
- src/auth/GoogleOAuth.js - Handler OAuth
- src/components/GoogleLoginButton.jsx - Componente UI

### Arquivos a Modificar:
- src/routes/auth.js:45 - Adicionar rota OAuth
- src/config/passport.js:12 - Configurar estratégia

[... passos detalhados de implementação ...]

Pronto para implementar? (sim/não)
```

**O que aconteceu:**
- Verificou branch correta
- Analisou arquitetura do codebase
- Criou plano passo a passo de implementação
- Aguardando aprovação

#### 3. Implementar

```
Usuário: sim
Claude: [Implementa o plano passo a passo]
Claude: ✓ Implementação completa. Pronto para commitar?
Usuário: sim
```

**O que aconteceu:**
- Código implementado seguindo o plano
- Testes escritos
- Mudanças commitadas com mensagem semântica
- Push para `feature/google-oauth`
- `.claude/context/current-task.md` limpo

## 🏗️ Filosofia do Workflow

### Descoberta → Planejamento → Execução

```
┌─────────────┐      ┌──────────────┐      ┌─────────────┐
│  Descoberta │ ───> │ Planejamento │ ───> │  Execução   │
│             │      │              │      │             │
│ /feature    │      │  /execute    │      │ Implementar │
│ /fix        │      │  Cria plano  │      │ Testar      │
│ /remove     │      │  detalhado   │      │ Commitar    │
│ /analyze    │      │              │      │ Push        │
└─────────────┘      └──────────────┘      └─────────────┘
     │                     │                      │
     └─────────────────────┴──────────────────────┘
              Documentado em current-task.md
```

### Por Que Isso Funciona

1. **Melhor Entendimento dos Requisitos** - Fase de descoberta força clareza
2. **Menos Reescritas** - Planejamento previne erros arquiteturais
3. **Histórico Git Mais Limpo** - Uma feature = Uma branch bem nomeada
4. **Alinhamento do Time** - Todos seguem o mesmo processo
5. **Transferência de Conhecimento** - `current-task.md` preserva contexto
6. **Consistência Arquitetural** - Padrões detectados automaticamente e mantidos em todo código novo

## 🎯 Filosofia de Consistência

### Detecção e Manutenção de Padrões

Este workflow vai além de apenas estruturar tarefas - ele **garante consistência arquitetural** em todo o projeto:

**Antes (problema comum):**
```
Projeto usa Clean Architecture...
Dev 1 adiciona feature seguindo MVC
Dev 2 adiciona outra feature com estrutura diferente
→ Código inconsistente, difícil manutenção
```

**Agora (com detecção de padrões):**
```
Sistema detecta: "Este projeto usa Clean Architecture"
Todas as features seguem automaticamente:
- Mesma estrutura de pastas (domain/, application/, infrastructure/)
- Mesmos design patterns (Repository, Use Cases)
- Mesmas naming conventions
- Mesmos padrões de teste
→ Código consistente, fácil manutenção
```

### Quando os Padrões São Aplicados

1. **`/pattern`**: Analisa e documenta padrões do projeto
2. **`/execute`**: Detecta padrões automaticamente (se não existir `project-patterns.md`)
3. **Implementação**: Todo código segue os padrões documentados
4. **Code Review**: Revisores podem verificar conformidade com padrões

### Benefícios da Consistência

- **Onboarding mais rápido**: Novos devs entendem os padrões rapidamente
- **Código previsível**: Estrutura familiar em todo o projeto
- **Manutenção facilitada**: Padrões claros = menos decisões ad-hoc
- **Escalabilidade**: Fácil adicionar features mantendo qualidade

## 📚 Referência de Comandos

### `/feature` - Descoberta de Nova Feature

**Cria:** branch `feature/[nome-descritivo]`

**Perguntas de Descoberta:**
- Qual é a feature?
- Quem vai usar?
- Quais são os requisitos?
- Casos extremos e restrições?

**Saída:** Requisitos documentados em `current-task.md`

**Exemplos de nomes de branch:**
- `feature/autenticacao-usuario`
- `feature/integracao-pagamento`
- `feature/modo-escuro`

---

### `/fix` - Descoberta de Correção de Bug

**Cria:** branch `fix/[nome-descritivo]`

**Perguntas de Descoberta:**
- Qual é o comportamento atual?
- Qual deveria ser o comportamento esperado?
- Passos para reproduzir?
- Impacto e prioridade?

**Saída:** Análise do problema em `current-task.md`

**Exemplos de nomes de branch:**
- `fix/validacao-login`
- `fix/vazamento-memoria`
- `fix/timeout-pagamento`

---

### `/remove` - Descoberta de Remoção

**Cria:** branch `remove/[nome-descritivo]`

**Perguntas de Descoberta:**
- O que precisa ser removido?
- Por que está sendo removido?
- O que depende disso?
- Impacto nos usuários?

**Saída:** Plano de remoção em `current-task.md`

**Exemplos de nomes de branch:**
- `remove/api-deprecated`
- `remove/analytics-antiga`
- `remove/auth-legado`

---

### `/analyze` - Análise Técnica

**Cria:** branch `analyze/[nome-descritivo]`

**Áreas de Análise:**
- Padrões de arquitetura
- Gargalos de performance
- Vulnerabilidades de segurança
- Problemas de qualidade de código
- Débito técnico

**Saída:** Relatório detalhado de análise em `current-task.md`

**Exemplos de nomes de branch:**
- `analyze/performance`
- `analyze/auditoria-seguranca`
- `analyze/tamanho-bundle`

---

### `/pattern` - Detectar Padrões do Projeto

**Executa em:** Qualquer branch (não cria branch nova)

**O Que Faz:**
- Analisa automaticamente toda a estrutura do projeto
- Detecta arquitetura, design patterns e convenções
- Identifica stack tecnológica e frameworks
- Mapeia padrões de teste e code quality
- Documenta tudo em `.claude/context/project-patterns.md`

**Quando Usar:**
- Primeira vez configurando o projeto
- Após mudanças significativas na arquitetura
- Para revisar e atualizar padrões documentados
- Quando novos membros entram no time

**Saída:**
- Arquivo `.claude/context/project-patterns.md` com análise completa
- Usado automaticamente por `/execute` para manter consistência

**Nota:** O `/execute` já faz isso automaticamente se o arquivo não existir. Use `/pattern` quando quiser forçar uma re-análise.

---

### `/execute` - Criar & Executar Plano

**Requisitos:**
- Deve estar em uma branch de trabalho (`feature/*`, `fix/*`, `remove/*`, `analyze/*`)
- `current-task.md` deve existir com contexto

**Processo:**
1. Verifica branch correta
2. Lê `current-task.md`
3. Explora codebase
4. Cria plano técnico detalhado
5. Pede aprovação
6. Implementa após confirmação

---

## 🎨 Customização

### Adaptando Comandos

Os comandos são arquivos markdown em `.claude/commands/`. Você pode:

1. **Modificar comandos existentes** - Edite os arquivos `.md`
2. **Adicionar novos comandos** - Crie novos arquivos `.md`
3. **Mudar padrões de branching** - Atualize os comandos git checkout

**Exemplo - Adicionar comando `/refactor`:**

Crie `.claude/commands/refactor.md`:
```markdown
---
description: Refatorar código para melhor manutenibilidade
---

# Modo Refactor

Você está no modo **REFACTOR**.

## Criar Branch
git checkout -b refactor/[nome-descritivo]

## Processo:
1. Identificar code smells
2. Planejar passos de refatoração
3. Documentar mudanças
...
```

### Customização Específica do Projeto

Adicione contexto específico do projeto aos comandos:

```markdown
## Stack Técnica
Este projeto usa:
- React 18 com TypeScript
- Tailwind CSS
- Vitest para testes

Sempre siga estes padrões ao implementar...
```

## 🤝 Contribuindo

Contribuições são bem-vindas! Veja como você pode ajudar:

### Ideias para Novos Comandos
- `/test` - Workflow de desenvolvimento orientado a testes
- `/docs` - Atualizações de documentação
- `/refactor` - Workflow de refatoração de código
- `/hotfix` - Correções críticas de produção

### Submeta Suas Ideias
1. Abra uma issue descrevendo o comando
2. Explique o caso de uso e workflow
3. Compartilhe sua implementação se tiver uma

### Processo de Pull Request
1. Faça fork do repo
2. Crie uma branch: `feature/seu-comando`
3. Adicione seu comando em `.claude/commands/`
4. Atualize README.md com documentação
5. Submeta PR com descrição clara

## 📖 Boas Práticas

### 1. Uma Branch Por Tarefa
Não misture diferentes tipos de mudanças. Cada tarefa recebe sua própria branch.

**Bom:**
- `feature/modo-escuro` - Apenas código do modo escuro
- `fix/overflow-header` - Apenas corrige header

**Ruim:**
- `feature/modo-escuro` - Modo escuro + correções de bug + refatoração

### 2. Nomes Descritivos de Branch
Use nomes claros em kebab-case que descrevem a mudança.

**Bom:**
- `feature/login-google-oauth`
- `fix/erro-validacao-pagamento`
- `remove/sistema-autenticacao-legado`

**Ruim:**
- `feature/coisa-nova`
- `fix/bug`
- `remove/codigo`

### 3. Limpar Após Push
Sempre execute a limpeza após push:
```bash
echo "" > .claude/context/current-task.md
```

Isso previne poluição de contexto em tarefas futuras.

### 4. Use Commits Semânticos
Siga [Conventional Commits](https://www.conventionalcommits.org/):
- `feat:` - Novas features
- `fix:` - Correções de bugs
- `refactor:` - Refatoração de código
- `docs:` - Documentação
- `test:` - Testes

### 5. Mantenha project-patterns.md Atualizado
O arquivo `.claude/context/project-patterns.md` deve ser commitado e versionado:
```bash
# Após mudanças arquiteturais significativas, re-execute
/pattern

# Commite as atualizações
git add .claude/context/project-patterns.md
git commit -m "docs: atualizar análise de padrões do projeto"
```

**Quando re-executar `/pattern`:**
- Adoção de nova arquitetura ou patterns
- Mudança de framework principal
- Novos padrões de teste
- Onboarding de novos membros do time
- A cada 3-6 meses (manutenção)

## 🔍 Solução de Problemas

### Comandos Não Aparecem
- Verifique se o diretório `.claude/commands/` existe
- Verifique se os nomes dos arquivos correspondem exatamente (ex: `feature.md`)
- Reinicie Claude Code

### Branch Já Existe
```bash
# Deletar branch local
git branch -d feature/nome

# Forçar delete se necessário
git branch -D feature/nome

# Deletar branch remota
git push origin --delete feature/nome
```

### current-task.md Tem Conteúdo Antigo
```bash
# Limpar manualmente
echo "" > .claude/context/current-task.md
```

### Branch Errada
```bash
# Criar branch correta
git checkout -b feature/nome-correto

# Deletar branch errada
git branch -d nome-errado
```

## 📊 Exemplos do Mundo Real

### Exemplo 1: Feature de E-commerce
```
Usuário: /feature
> "Adicionar funcionalidade de carrinho de compras"

Claude: [Fase de descoberta - pergunta sobre persistência, UI, fluxo de checkout]
> Documentado em current-task.md

Usuário: /execute
> Claude cria plano: estado Redux, componente Cart, endpoints API, testes

Usuário: "aprovar"
> Claude implementa carrinho completo
> Branch: feature/carrinho-compras
> Commits com mensagens semânticas
> Push e limpeza
```

### Exemplo 2: Problema de Performance
```
Usuário: /fix
> "Dashboard carrega lentamente no mobile"

Claude: [Descoberta - passos de reprodução, métricas, profiling]
> Documenta problema de performance

Usuário: /execute
> Claude analisa, encontra query N+1, cria plano de otimização

Usuário: "implementar"
> Corrige query, adiciona cache, otimiza imagens
> Branch: fix/performance-dashboard
> Inclui métricas antes/depois no commit
```

### Exemplo 3: Remoção de Código
```
Usuário: /remove
> "Remover sistema de analytics antigo, migramos para Google Analytics"

Claude: [Descoberta - verifica dependências, migração de dados, impacto]
> Documenta escopo de remoção

Usuário: /execute
> Claude cria plano seguro de remoção com estratégia de rollback

Usuário: "prosseguir"
> Remove código antigo, atualiza configs, limpa dependências
> Branch: remove/analytics-legado
```

### Exemplo 4: Detecção de Padrões (Novo!)
```
Usuário: /pattern
> Claude detecta automaticamente:
  - Arquitetura: Clean Architecture
  - Patterns: Repository, UseCase, DI
  - Testes: Jest com AAA pattern
  - Naming: PascalCase para classes, camelCase para funções

> Cria .claude/context/project-patterns.md
> "✓ Padrões documentados. Use /execute - ele seguirá automaticamente esses padrões."

Usuário: /feature
> "Adicionar sistema de notificações"

Usuário: /execute
> Claude: "Detectei que o projeto usa Clean Architecture com Repository pattern..."
> Cria plano seguindo EXATAMENTE a mesma estrutura:
  - domain/entities/Notification.ts
  - domain/repositories/INotificationRepository.ts
  - application/usecases/SendNotificationUseCase.ts
  - infrastructure/repositories/NotificationRepository.ts
  - __tests__/usecases/SendNotificationUseCase.test.ts (Jest com AAA)

> Todo código mantém consistência com o resto do projeto!
```

## 🌟 Por Que Isso Importa

### Para Desenvolvedores Individuais
- **Menos estresse** - Processo claro para seguir
- **Código melhor** - Tempo para pensar antes de codificar
- **Aprendizado** - Entenda sistemas profundamente

### Para Times
- **Consistência** - Todos seguem mesmo workflow
- **Onboarding** - Novos devs aprendem o processo rapidamente
- **Code review** - PRs têm melhor contexto

### Para Projetos
- **Histórico limpo** - Branches e commits significativos
- **Documentação** - Contexto preservado em arquivos de tarefa
- **Qualidade** - Fase de planejamento captura problemas cedo

## 📄 Licença

Licença MIT - sinta-se livre para usar em qualquer projeto!

## 🙏 Agradecimentos

Construído com [Claude Code](https://claude.com/claude-code) da Anthropic.

Criado para ajudar desenvolvedores a construir software melhor através de workflows estruturados.

## 🔗 Links

- [Documentação Claude Code](https://docs.claude.com/pt/docs/claude-code)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [Git Flow](https://nvie.com/posts/a-successful-git-branching-model/)

---

**Feito com ❤️ para a comunidade de desenvolvedores**

*Se este workflow te ajudar, considere dar uma estrela no repo e compartilhar com seu time!*
