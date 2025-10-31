# Comandos Customizados do Claude Code

Este diretório contém comandos slash customizados para Claude Code que implementam um workflow Git estruturado.

## Estrutura de Diretórios

```
.claude/
├── commands/          # Definições de comandos slash
│   ├── feature.md    # Criar novas features
│   ├── fix.md        # Corrigir bugs
│   ├── remove.md     # Remover código/features
│   ├── analyze.md    # Análise técnica
│   ├── execute.md    # Executar planos técnicos
│   └── README.md     # Documentação dos comandos
└── context/          # Contexto temporário de tarefas
    ├── .gitignore    # Ignorar arquivos de tarefa
    ├── .gitkeep      # Rastrear diretório
    └── current-task.md  # Contexto da tarefa ativa (auto-gerado)
```

## Como Funciona

### Comandos Slash

Claude Code detecta automaticamente arquivos `.md` em `.claude/commands/` e os disponibiliza como comandos slash.

**Arquivo:** `.claude/commands/feature.md`
**Comando:** `/feature`

Quando você digita `/feature`, Claude Code carrega o conteúdo de `feature.md` e segue essas instruções.

### Diretório de Contexto

O diretório `context/` armazena documentação temporária de tarefas:

- **current-task.md** - Documento vivo da tarefa ativa
- Criado por `/feature`, `/fix`, `/remove`, ou `/analyze`
- Usado por `/execute` para criar planos técnicos
- Limpo após conclusão da tarefa
- **NÃO rastreado no git** (veja `.gitignore`)

## Workflow dos Comandos

```
1. Descoberta     →  2. Planejamento   →  3. Execução
   /feature          /execute            Implementar
   /fix              Analisa             Testar
   /remove           Cria plano          Commitar
   /analyze          Aguarda aprovação   Push
   ↓                 ↓                   ↓
   Cria             Lê                   Limpa
   current-task.md  current-task.md     current-task.md
```

## Comandos Disponíveis

| Comando | Padrão de Branch | Propósito |
|---------|-----------------|-----------|
| `/feature` | `feature/[nome]` | Novas features |
| `/fix` | `fix/[nome]` | Correções de bugs |
| `/remove` | `remove/[nome]` | Remoção de código |
| `/analyze` | `analyze/[nome]` | Análise |
| `/execute` | *(atual)* | Planejamento & execução |

## Integração Git

Todos os comandos criam branches automaticamente seguindo convenções Git Flow:

- `feature/*` - Novas capacidades
- `fix/*` - Correções de bugs
- `remove/*` - Deleção de código
- `analyze/*` - Auditorias técnicas

## Customização

### Modificar Comandos Existentes

Edite os arquivos `.md` em `commands/` para mudar comportamento:

```bash
# Exemplo: Mudar padrão de branch
vim .claude/commands/feature.md

# Encontre:
git checkout -b feature/[nome]

# Mude para:
git checkout -b feat/[nome]
```

### Adicionar Novos Comandos

Crie um novo arquivo `.md` em `commands/`:

```bash
touch .claude/commands/refactor.md
```

Claude Code detectará automaticamente como `/refactor`.

### Contexto Específico do Projeto

Adicione sua stack técnica aos arquivos de comando:

```markdown
## Contexto do Projeto

Este projeto usa:
- React 18 + TypeScript
- Tailwind CSS
- Vitest para testes

Sempre siga estes padrões...
```

## Nomenclatura de Arquivos

Arquivos de comando devem:
- Estar em `.claude/commands/`
- Ter extensão `.md`
- Usar nomes em minúsculas
- Corresponder ao comando desejado

**Exemplos:**
- `feature.md` → `/feature`
- `fix.md` → `/fix`
- `analyze.md` → `/analyze`

## Controle de Versão

### O Que Rastrear

✅ **Rastrear no Git:**
- `.claude/commands/*.md` - Comandos são configuração do projeto
- `.claude/context/.gitignore` - Proteger arquivos temporários
- `.claude/context/.gitkeep` - Manter estrutura de diretório

❌ **Não Rastrear:**
- `.claude/context/current-task.md` - Temporário, específico da sessão

### Por Que Rastrear Comandos?

Comandos são **configuração do projeto**, similar a:
- `.eslintrc` - Regras de estilo de código
- `.prettierrc` - Configuração de formatação
- `package.json` - Dependências

Eles definem **como seu time trabalha**, então devem ser compartilhados.

## Solução de Problemas

### Comando Não Disponível

1. Verifique se arquivo existe: `ls .claude/commands/feature.md`
2. Verifique se extensão é `.md`
3. Reinicie Claude Code
4. Verifique versão do Claude Code (requer versão recente)

### current-task.md Não Limpa

```bash
# Limpeza manual
echo "" > .claude/context/current-task.md

# Ou delete
rm .claude/context/current-task.md
```

### Comandos Criando Branches Erradas

Edite o arquivo de comando e atualize a linha `git checkout -b`:

```markdown
## Antes
git checkout -b feature/[nome]

## Depois
git checkout -b seu-padrao/[nome]
```

## Boas Práticas

1. **Não edite current-task.md manualmente** - Deixe os comandos gerenciarem
2. **Limpe após push** - Previne poluição de contexto
3. **Uma tarefa por branch** - Não misture features/fixes
4. **Nomes descritivos de branch** - Use kebab-case

## Saiba Mais

- [Documentação Claude Code](https://docs.claude.com/pt/docs/claude-code)
- [README Principal](../README.md)
- [Guia de Contribuição](../CONTRIBUTING.md)

---

Dúvidas? Abra uma issue no repositório principal!
