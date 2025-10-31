---
description: Analisa e documenta padrões, arquitetura e convenções do projeto
---

# Pattern Analysis Mode

Você está no modo **PATTERN ANALYSIS**. Seu objetivo é realizar uma análise profunda e automática dos padrões de código, arquitetura e convenções do projeto.

## IMPORTANTE: Branch Opcional

Este comando pode ser executado em qualquer branch. Se for fazer commits de melhorias baseadas na análise, crie uma branch:
```bash
git checkout -b pattern/analysis
```

## Processo de Análise Automática:

### 1. **Detecção de Stack Tecnológica**
Analise automaticamente:
- Linguagens principais (TypeScript, JavaScript, Python, Go, Java, etc.)
- Frameworks e bibliotecas principais
- Build tools e package managers
- Versões relevantes

**Como detectar:**
- Leia `package.json`, `requirements.txt`, `go.mod`, `pom.xml`, etc.
- Identifique dependências principais e suas versões
- Detecte configurações de build (Vite, Webpack, etc.)

### 2. **Detecção de Arquitetura**
Identifique automaticamente a arquitetura utilizada:

**Padrões comuns a detectar:**
- **MVC** (Model-View-Controller): Pastas `models/`, `views/`, `controllers/`
- **Clean Architecture**: Camadas `domain/`, `application/`, `infrastructure/`, `presentation/`
- **Hexagonal**: `ports/`, `adapters/`, `domain/`
- **Layered**: `data/`, `business/`, `presentation/`
- **Feature-based**: Pastas organizadas por feature (`features/`, `modules/`)
- **Atomic Design**: `atoms/`, `molecules/`, `organisms/`, `templates/`, `pages/`
- **Domain-Driven Design**: `domains/`, `bounded-contexts/`, `aggregates/`

**Como detectar:**
- Use Task tool com Explore para mapear estrutura de pastas
- Identifique padrões de nomenclatura de diretórios
- Analise imports/exports para entender fluxo de dependências

### 3. **Detecção de Design Patterns**
Identifique automaticamente patterns implementados:

**Patterns a procurar:**
- **Repository Pattern**: Classes/arquivos com "Repository" no nome
- **Factory Pattern**: "Factory", "Builder" no código
- **Singleton**: Exports únicos, getInstance()
- **Observer/PubSub**: Event emitters, listeners, subscribers
- **Dependency Injection**: Containers, providers, inject decorators
- **Strategy Pattern**: Classes intercambiáveis com mesma interface
- **Adapter Pattern**: Wrappers de bibliotecas externas
- **Facade Pattern**: Interfaces simplificadas para sistemas complexos

**Como detectar:**
- Grep por palavras-chave: "Repository", "Factory", "Service", etc.
- Analise estrutura de classes e exports
- Identifique padrões de injeção de dependência

### 4. **Detecção de Convenções de Código**

**Naming Conventions:**
- camelCase, PascalCase, snake_case, kebab-case
- Prefixos/sufixos comuns (I para interfaces, Abstract, Base, etc.)
- Nomenclatura de arquivos (.service.ts, .controller.js, etc.)

**Estrutura de Arquivos:**
- Co-location (testes junto com código) vs separados
- Index files (barrel exports)
- Organização por tipo vs por feature

**Import/Export Patterns:**
- Named exports vs default exports
- Absolute vs relative imports
- Path aliases (@/, ~/, etc.)

**Como detectar:**
- Analise nomes de arquivos e diretórios
- Examine padrões de import em múltiplos arquivos
- Identifique configurações em tsconfig.json, jsconfig.json

### 5. **Detecção de Padrões de Teste**

**Framework de Testes:**
- Jest, Vitest, Mocha, Pytest, Go testing, JUnit, etc.

**Estrutura de Testes:**
- Localização: `__tests__/`, `tests/`, `*.test.ts`, `*.spec.ts`
- Organização: Mirror da estrutura de código ou separado
- Tipos: Unit, Integration, E2E

**Padrões de Escrita:**
- AAA (Arrange-Act-Assert)
- Given-When-Then
- Describe/It blocks

**Coverage:**
- Existe configuração de coverage?
- Qual o threshold esperado?

**Como detectar:**
- Grep por arquivos de teste (.test., .spec., _test.go, etc.)
- Leia package.json, pytest.ini, go.mod para frameworks
- Analise estrutura de alguns arquivos de teste

### 6. **Code Quality & Metrics**

**Linters e Formatters:**
- ESLint, Prettier, Black, gofmt, etc.
- Configurações personalizadas

**Padrões de Qualidade:**
- Complexidade ciclomática aceitável
- Tamanho máximo de funções/arquivos
- Code smells comuns a evitar

**Como detectar:**
- Leia .eslintrc, .prettierrc, pyproject.toml
- Analise configurações em package.json

### 7. **Padrões de Estado e Data Fetching**

**State Management:**
- Redux, Zustand, Jotai, Context API, MobX, etc.

**Data Fetching:**
- React Query, SWR, Apollo Client, Axios, Fetch API

**Como detectar:**
- Verifique dependências em package.json
- Grep por imports dessas bibliotecas
- Analise estrutura de stores/providers

## Diretrizes de Execução:

1. **Execute análise AUTOMATICAMENTE** - Não pergunte ao usuário sobre cada detalhe
2. **Use Task tool com Explore** - Para mapear estrutura do projeto
3. **Seja completo mas eficiente** - Analise amostras representativas, não todo arquivo
4. **Quando houver ambiguidade** - Documente múltiplas possibilidades e pergunte
5. **Se não detectar padrões claros** - Pergunte ao usuário suas preferências usando AskUserQuestion

## Entrega:

Crie o arquivo `.claude/context/project-patterns.md` com a análise completa:

```markdown
# Project Patterns Analysis

**Data da Análise:** [data atual]
**Última Atualização:** [data atual]

---

## Stack Tecnológica

### Linguagens
- [Linguagem principal]: [versão]
- [Outras linguagens se houver]

### Frameworks e Bibliotecas Principais
- [Framework 1]: [versão] - [propósito]
- [Framework 2]: [versão] - [propósito]

### Build Tools
- [Tool]: [versão]

### Package Manager
- [npm/yarn/pnpm/pip/go mod/maven]: [versão]

---

## Arquitetura

### Padrão Arquitetural
**[Nome da arquitetura detectada]**

[Descrição de como está implementado]

### Estrutura de Pastas
```
src/
├── [pasta1]/
├── [pasta2]/
└── ...
```

### Fluxo de Dependências
[Como os módulos se relacionam]

---

## Design Patterns Identificados

### [Pattern 1]
- **Onde:** [arquivos/pastas]
- **Implementação:** [como está implementado]
- **Exemplo:** [exemplo de uso]

### [Pattern 2]
- **Onde:** [arquivos/pastas]
- **Implementação:** [como está implementado]
- **Exemplo:** [exemplo de uso]

---

## Convenções de Código

### Naming Conventions
- **Arquivos:** [padrão detectado]
- **Classes/Types:** [padrão detectado]
- **Funções:** [padrão detectado]
- **Variáveis:** [padrão detectado]
- **Constantes:** [padrão detectado]

### Estrutura de Arquivos
- **Localização de testes:** [padrão]
- **Index files:** [sim/não e como usado]
- **Organização:** [por tipo/por feature]

### Imports/Exports
- **Estilo:** [named/default]
- **Caminhos:** [absolute/relative]
- **Aliases:** [lista de aliases configurados]

---

## Padrões de Teste

### Framework
- **Principal:** [framework]
- **Versão:** [versão]

### Estrutura
- **Localização:** [onde ficam os testes]
- **Nomenclatura:** [padrão de nome]
- **Tipos:** [unit/integration/e2e]

### Estilo de Escrita
- **Padrão:** [AAA/Given-When-Then/etc]
- **Exemplo:**
```[linguagem]
[exemplo de teste representativo]
```

### Coverage
- **Configurado:** [sim/não]
- **Threshold:** [se houver]

---

## Code Quality

### Linters
- [Linter]: [versão]
- **Regras customizadas:** [sim/não]

### Formatters
- [Formatter]: [versão]
- **Configurações:** [principais configurações]

### Métricas de Qualidade
- **Complexidade máxima:** [se configurado]
- **Tamanho de função:** [se configurado]
- **Outros:** [outras métricas]

---

## State Management & Data Fetching

### State Management
- **Biblioteca:** [biblioteca]
- **Padrão:** [como está estruturado]

### Data Fetching
- **Biblioteca:** [biblioteca]
- **Padrão:** [como é feito]

---

## Padrões Específicos do Projeto

### [Categoria 1]
[Padrões únicos deste projeto que devem ser mantidos]

### [Categoria 2]
[Outros padrões identificados]

---

## Recomendações para Novas Implementações

Ao adicionar código novo (features, fixes, refactors), SEMPRE:

1. **Arquitetura:** Siga o padrão [arquitetura detectada]
2. **Organização:** Coloque arquivos em [estrutura esperada]
3. **Naming:** Use [convenções detectadas]
4. **Patterns:** Utilize [patterns identificados] quando aplicável
5. **Testes:** Escreva testes seguindo [padrão de teste]
6. **Estilo:** Mantenha consistência com [code style]

---

## Próximos Passos

- [ ] Revisar e validar esta análise
- [ ] Documentar padrões adicionais se necessário
- [ ] Compartilhar com o time
- [ ] Usar como referência em todos os `/execute`
```

## Após Análise:

1. **Mostre um resumo** dos padrões detectados
2. **Pergunte se o usuário quer ajustar algo** detectado incorretamente
3. **Confirme que este arquivo será usado** automaticamente pelos comandos `/execute`, `/feature`, `/fix`, `/remove`
4. **Sugira executar novamente** se o projeto mudar significativamente

## Integração com Outros Comandos:

Este arquivo será automaticamente consultado por:
- `/execute` - Para criar planos que seguem os padrões
- `/feature` - Para implementar features consistentes
- `/fix` - Para corrigir bugs mantendo padrões
- `/remove` - Para remover código de forma consistente

---

**Nota:** Esta análise é automática e baseada em heurísticas. Sempre valide com o usuário quando houver ambiguidade ou múltiplas possibilidades.
