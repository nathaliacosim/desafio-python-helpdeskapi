# 📝 Conventional Commits

Você já aprendeu a criar commits. Agora vamos dar um passo além:

**Como escrever commits de forma padronizada e fácil de entender?**

Em projetos reais, é comum utilizar uma convenção para as mensagens de commit. Uma das mais conhecidas é o **Conventional Commits**.

A ideia é simples: seguir um formato que permita identificar rapidamente **o tipo da alteração e o que foi feito**.

---

## 📐 Estrutura

O formato básico é:

```text
tipo: descrição
```

Por exemplo:

```bash
git commit -m "feat: adiciona cadastro de usuários"
```

Também podemos informar uma área específica do projeto:

```text
tipo(escopo): descrição
```

Por exemplo:

```bash
git commit -m "feat(api): adiciona endpoint de usuários"
```

---

# 🏷️ Tipos de commit

Existem vários tipos que podem ser utilizados. Os mais comuns são:

| Tipo       | Quando usar                                                        |
| ---------- | ------------------------------------------------------------------ |
| `feat`     | Adição de uma nova funcionalidade                                  |
| `fix`      | Correção de um problema                                            |
| `docs`     | Alteração na documentação                                          |
| `style`    | Alterações de formatação que não mudam o comportamento             |
| `refactor` | Refatoração do código sem adicionar funcionalidade ou corrigir bug |
| `test`     | Criação ou alteração de testes                                     |
| `chore`    | Tarefas de manutenção                                              |
| `perf`     | Melhoria de performance                                            |
| `build`    | Alterações relacionadas ao build ou dependências                   |
| `ci`       | Alterações relacionadas à integração/entrega contínua              |

---

## ✨ `feat`

Use quando estiver adicionando uma **nova funcionalidade**.

```bash
git commit -m "feat: adiciona cadastro de usuários"
```

```bash
git commit -m "feat: adiciona filtro por categoria"
```

```bash
git commit -m "feat(api): cria endpoint de produtos"
```

---

## 🐛 `fix`

Use quando estiver **corrigindo um problema ou bug**.

```bash
git commit -m "fix: corrige validação de email"
```

```bash
git commit -m "fix: corrige cálculo do valor total"
```

```bash
git commit -m "fix(login): corrige validação de senha"
```

---

## 📚 `docs`

Use para alterações exclusivamente relacionadas à **documentação**.

```bash
git commit -m "docs: adiciona instruções de instalação"
```

```bash
git commit -m "docs: atualiza documentação da API"
```

---

## 🎨 `style`

Use quando a alteração modifica apenas **formatação ou estilo do código**, sem mudar seu comportamento.

Por exemplo:

* formatação;
* espaços;
* indentação;
* quebra de linhas.

```bash
git commit -m "style: ajusta formatação do código"
```

> ⚠️ Aqui, `style` não significa necessariamente alteração visual da aplicação.

---

## ♻️ `refactor`

Use quando você está **melhorando a estrutura do código sem alterar seu comportamento**.

Por exemplo:

```bash
git commit -m "refactor: simplifica serviço de usuários"
```

```bash
git commit -m "refactor: remove código duplicado"
```

A ideia é melhorar o código sem estar adicionando uma nova funcionalidade ou corrigindo um bug específico.

---

## 🧪 `test`

Use para alterações relacionadas aos **testes**.

```bash
git commit -m "test: adiciona testes para usuários"
```

```bash
git commit -m "test: adiciona cobertura para login"
```

---

## 🔧 `chore`

Use para tarefas de **manutenção** que não representam uma nova funcionalidade ou correção de bug.

Por exemplo:

```bash
git commit -m "chore: atualiza dependências"
```

```bash
git commit -m "chore: configura editorconfig"
```

---

## ⚡ `perf`

Use quando a alteração tem como objetivo melhorar a **performance** da aplicação.

```bash
git commit -m "perf: otimiza consulta de usuários"
```

```bash
git commit -m "perf: reduz chamadas ao banco"
```

---

## 📦 `build`

Use para alterações relacionadas ao **processo de build**, empacotamento ou dependências utilizadas para gerar o projeto.

```bash
git commit -m "build: atualiza dependências do projeto"
```

---

## 🔄 `ci`

Use para alterações relacionadas à **integração e entrega contínua (CI/CD)**.

Por exemplo:

```bash
git commit -m "ci: adiciona pipeline de testes"
```

```bash
git commit -m "ci: ajusta workflow de deploy"
```

---

# 🎯 Escopo

O escopo é opcional e ajuda a indicar **qual parte do sistema foi alterada**.

Formato:

```text
tipo(escopo): descrição
```

Exemplos:

```bash
git commit -m "feat(api): adiciona endpoint de usuários"
```

```bash
git commit -m "fix(login): corrige validação de senha"
```

```bash
git commit -m "test(users): adiciona testes de cadastro"
```

Nesse caso:

```text
feat(api): adiciona endpoint de usuários
 │    │              │
 │    │              └── O que foi feito
 │    └───────────────── Área afetada
 └────────────────────── Tipo da alteração
```

O escopo depende da organização do projeto.

Pode ser:

```text
api
login
users
database
auth
payments
```

---

# ⚠️ Breaking Changes

Algumas alterações podem **quebrar a compatibilidade** com o que existia anteriormente.

Nesse caso, podemos utilizar `!` depois do tipo ou do escopo.

Exemplo:

```bash
git commit -m "feat!: remove autenticação antiga"
```

Ou:

```bash
git commit -m "feat(api)!: altera contrato do endpoint de usuários"
```

O `!` indica que existe uma **breaking change**, ou seja, uma alteração que pode exigir mudanças em quem utiliza aquela funcionalidade.

> 🚨 Não use `!` simplesmente porque a alteração é grande. Use quando existe uma quebra de compatibilidade.

---

# 🧩 Exemplos completos

### Nova funcionalidade

```bash
git commit -m "feat: adiciona recuperação de senha"
```

### Correção

```bash
git commit -m "fix: corrige cálculo do desconto"
```

### Funcionalidade com escopo

```bash
git commit -m "feat(api): adiciona endpoint de usuários"
```

### Correção com escopo

```bash
git commit -m "fix(login): corrige validação de senha"
```

### Testes

```bash
git commit -m "test(users): adiciona testes de cadastro"
```

### Refatoração

```bash
git commit -m "refactor: remove código duplicado"
```

### Breaking change

```bash
git commit -m "feat!: remove autenticação antiga"
```

---

# ❌ Evite mensagens assim

Mensagens muito genéricas não ajudam muito quando alguém precisa entender o histórico do projeto:

```bash
git commit -m "alterações"
```

```bash
git commit -m "mudanças"
```

```bash
git commit -m "fix"
```

```bash
git commit -m "coisas novas"
```

```bash
git commit -m "update"
```

O problema não é apenas a mensagem ser curta. É que, olhando o histórico daqui a algumas semanas, fica difícil entender **o que realmente aconteceu**.

Prefira algo como:

```bash
git commit -m "fix: corrige cálculo do valor total"
```

---

# 💡 Uma regra simples

Antes de criar um commit, pense:

> **O que eu alterei?**

Depois:

> **Por que estou fazendo essa alteração?**

E escolha o tipo que melhor representa o trabalho.

Por exemplo:

```text
Adicionei uma funcionalidade?
→ feat

Corrigi um bug?
→ fix

Alterei documentação?
→ docs

Melhorei a estrutura do código?
→ refactor

Criei ou alterei testes?
→ test

Melhorei performance?
→ perf
```

---

# 🧪 Desafio

Agora pratique.

Faça algumas alterações no seu projeto e tente criar commits seguindo o padrão.

Crie pelo menos:

* 1 commit `feat`
* 1 commit `fix`
* 1 commit `docs`
* 1 commit `refactor`
* 1 commit `test`

Depois confira o histórico:

```bash
git log --oneline
```

Você deverá conseguir identificar rapidamente o que aconteceu no projeto apenas olhando para as mensagens.

---

## 📚 Para continuar estudando

O **Conventional Commits** possui regras mais completas sobre estrutura, breaking changes e outras possibilidades.

👉 [Conventional Commits](https://www.conventionalcommits.org/)

> 🚀 **Não tente decorar tudo de uma vez.**
>
> No começo, concentre-se em `feat`, `fix`, `docs`, `refactor` e `test`. Conforme você trabalhar em projetos maiores, os outros tipos vão começar a fazer sentido naturalmente.
