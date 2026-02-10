# Vibe Coding Expert Setup (Node.js + React + MCP)

Tutorial objetivo para configurar um ambiente de alta produtividade com **Cursor**, **Antigravity** e **Codex**, usando práticas modernas de arquitetura, testes e fluxo de entrega.

---

## 1) Objetivo do setup

Criar um boilerplate que permita:
- Desenvolvimento rápido sem perder qualidade.
- Uso consistente de IA com regras claras.
- Arquitetura sustentável (DRY, KISS, Clean Architecture).
- Pipeline de commit/PR com padrão profissional.
- Testes focados em fluxos críticos (não em cobertura cega).

**Armadilha comum:** começar codando sem regras de projeto. Isso acelera no dia 1 e desacelera no mês 2.

---

## 2) Estrutura base do projeto

```txt
.
├── README.md
├── AGENTS.md
├── .cursor/
│   └── rules/
│       └── ecco-safet-project-rules/
│           └── RULE.md
├── .cursor/rules.yaml
├── .antigravity/
│   └── instructions.md
└── mcp/
    ├── codex.mcp.json
    ├── cursor.mcp.json
    └── antigravity.mcp.json
```

**Por quê:** organização explícita reduz ambiguidade entre ferramentas e deixa onboarding rápido.

---

## 3) Configuração de MCPs (modelo prático)

Os arquivos em `mcp/` já trazem boilerplates para conectar servidores MCP (filesystem, git, github, docs).

### Passos
1. Copie o arquivo correspondente ao seu cliente (`cursor.mcp.json`, `codex.mcp.json`, `antigravity.mcp.json`).
2. Ajuste caminhos locais e variáveis de ambiente.
3. Garanta tokens seguros via `.env`/secret manager (nunca no Git).
4. Reinicie o cliente e valide listagem de servidores MCP.

**Armadilhas/pegadinhas:**
- Token com escopo excessivo.
- Caminho de workspace errado.
- Ferramenta travada por conflito entre config global e local.

---

## 4) Regras de IA e arquitetura

- Regras do Cursor em `.cursor/rules.yaml` e `.cursor/rules/ecco-safet-project-rules/RULE.md`.
- Regras do Codex em `AGENTS.md`.
- Instruções do Antigravity em `.antigravity/instructions.md`.

Essas regras forçam:
- Separação por camadas (domain/application/infrastructure/interface).
- Sem lógica de negócio em controller/UI.
- Dependências apontando para dentro.
- Mudanças pequenas, focadas e rastreáveis.

---

## 5) Boilerplate de Node + React (direção recomendada)

Para projetos reais, padronize:
- **Monorepo pnpm** (`apps/web`, `apps/api`, `packages/*`).
- API em Node.js (Fastify/Nest/Express com boundaries claros).
- Frontend React (Vite + React Router + TanStack Query).
- Qualidade: ESLint + Prettier + TypeScript strict.

**Objetivo:** escalar sem reescrever projeto a cada novo módulo.

---

## 6) Boas práticas de arquitetura (simples e eficazes)

- **KISS:** use solução mais simples que resolve o problema atual.
- **DRY:** extraia duplicações reais, não “futuras”.
- **Clean Architecture:** domínio independente de framework.
- **Incrementalismo:** pequenos PRs, feedback rápido.

**Checklist rápido por feature:**
- Regra de negócio está no domínio/aplicação?
- Infra é adaptador (DB/API), não centro da solução?
- Nome de função/classe explica o propósito sem comentário?

---

## 7) Pipeline de commit e PR (GitHub)

### Branching
- `develop` como integração.
- `epic/*` para iniciativas longas.
- `feature/*` para entregas curtas.
- `fix/*`, `chore/*`, `docs/*`, `refactor/*` quando aplicável.

### Commit
Use Conventional Commits:
- `feat: add mcp boilerplates for codex/cursor/antigravity`
- `docs: add objective vibe-coding setup tutorial`

### PR
- Objetivo único.
- Diff pequeno.
- Descrição fiel ao que realmente mudou.
- Declarar impacto arquitetural quando houver.

**Armadilha comum:** PR gigante “resolve tudo”. Isso piora revisão, risco e rollback.

---

## 8) Estratégia de testes meaningful

Foco: **100% dos fluxos críticos**, não 100% de linhas.

### Pirâmide pragmática
- Unitários: regras de negócio críticas.
- Integração: contratos entre camadas e persistência.
- E2E (outra suíte): jornadas principais do usuário.

### O que testar primeiro
1. Fluxos que movimentam dinheiro/dados sensíveis.
2. Autenticação/autorização.
3. Criação/edição/exclusão de entidades centrais.
4. Cenários de erro que quebram operação.

**Regra de ouro:** se um bug nesse fluxo gera incidente, ele precisa de teste.

---

## 9) Revisão final do tutorial (para quem já programa, mas é novo em vibe coding)

Sim, este passo a passo é suficiente para levar alguém com experiência em código a um nível forte de entrega com IA, porque cobre:
- Setup das ferramentas (MCP + regras).
- Estrutura de projeto e arquitetura.
- Processo de versionamento e PR.
- Critério de testes focado em risco real.

Se a pessoa seguir os arquivos deste repositório como padrão e mantiver PRs pequenos com validação contínua, ela conseguirá gerar sistemas reais e entregáveis em produção com muito mais previsibilidade.

---

## 10) Próximo passo prático

1. Aplicar estes arquivos no seu repositório base.
2. Criar um primeiro módulo vertical (UI + API + persistência) usando as regras.
3. Abrir PR pequeno e revisar aderência às regras de arquitetura.
4. Repetir o ciclo com feedback do time.
