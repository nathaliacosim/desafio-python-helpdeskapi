# 🌱 Git

Se você está começando no desenvolvimento, uma das primeiras ferramentas que precisa conhecer é o **Git**.

O Git é um sistema de **controle de versão**. Ele permite acompanhar as alterações do seu código, voltar para versões anteriores e trabalhar em equipe de forma organizada.

> 💡 Se você está começando no back-end, provavelmente vai usar o **Git** todos os dias.

No começo, alguns comandos podem parecer complicados. Mas, quando você entende **o que cada um faz e como eles se conectam**, o Git começa a fazer parte da rotina.

---

# 🧠 Local x Remoto

Antes dos comandos, é importante entender dois conceitos:

### 💻 Repositório local

É o repositório Git que está na sua máquina.

É onde você desenvolve, altera arquivos e cria commits.

### ☁️ Repositório remoto

É o repositório armazenado em um servidor, como GitHub, GitLab ou Azure Repos.

É onde seu código pode ser compartilhado e acessado por outras pessoas.

De forma simplificada:

```text
             Repositório remoto
                    ☁️
                  ↙   ↖
               pull   push
                ↙       ↖
              💻 Sua máquina
```

---

# 🚀 7 comandos essenciais

## 1. `git init`

Cria um novo repositório Git dentro do seu projeto.

Primeiro, entre na pasta do projeto:

```bash
cd meu-projeto
```

Depois:

```bash
git init
```

Agora sua pasta possui um **repositório Git local**.

> 💡 Você normalmente usa `git init` quando está começando um projeto do zero.

---

## 2. `git clone`

Usado quando o projeto já existe em um repositório remoto e você quer baixá-lo para sua máquina.

```bash
git clone https://github.com/seu-usuario/meu-projeto.git
```

O Git cria uma cópia do projeto na sua máquina, incluindo seu histórico de versões.

> 💡 Use `clone` quando você estiver começando a trabalhar em um projeto que já existe.

---

## 3. `git status`

Mostra o **estado atual do seu repositório**.

```bash
git status
```

Por exemplo, se você criou um arquivo chamado `README.md`, pode aparecer algo parecido com:

```text
Untracked files:
  README.md
```

Isso significa que o Git encontrou um novo arquivo, mas ele ainda não foi adicionado à próxima versão.

> 💡 Ficou na dúvida sobre o que mudou? Rode `git status`.

---

## 4. `git add`

Prepara as alterações para serem incluídas no próximo commit.

Para adicionar todas as alterações:

```bash
git add .
```

O `.` significa:

> "Adicione todas as alterações desta pasta."

Também é possível adicionar apenas um arquivo:

```bash
git add README.md
```

Depois, confira novamente:

```bash
git status
```

Agora o arquivo deverá aparecer como **staged**, ou seja, preparado para o commit.

---

## 5. `git commit`

O commit registra uma versão das alterações que foram preparadas com `git add`.

```bash
git commit -m "Adiciona README do projeto"
```

Procure escrever mensagens que expliquem **o que foi alterado**.

Por exemplo:

```bash
git commit -m "Adiciona cadastro de usuários"
```

```bash
git commit -m "Corrige validação de login"
```

```bash
git commit -m "Cria endpoint de produtos"
```

> 💡 Uma forma simples de pensar no commit é como uma **foto do seu projeto naquele momento**.

### 📝 Boas práticas para commits

Em projetos reais, é comum seguir um padrão para deixar o histórico mais organizado e fácil de entender.

Alguns tipos bastante utilizados são:

| Tipo       | Quando utilizar                                     |
| ---------- | --------------------------------------------------- |
| `feat`     | Nova funcionalidade                                 |
| `fix`      | Correção de um problema                             |
| `docs`     | Alteração na documentação                           |
| `refactor` | Refatoração sem alterar comportamento               |
| `test`     | Criação ou alteração de testes                      |
| `chore`    | Tarefas de manutenção                               |
| `style`    | Formatação ou estilo sem alteração de comportamento |

Exemplos:

```bash
git commit -m "feat: adiciona cadastro de usuários"
```

```bash
git commit -m "fix: corrige validação de email"
```

```bash
git commit -m "docs: atualiza documentação da API"
```

> 💡 Você não precisa decorar todos esses tipos agora. O importante é entender **por que existe um padrão para mensagens de commit**.

📚 Quer aprender mais sobre esse padrão?

👉 [Boas práticas para mensagens de commit](./git-conventional-commits.md)

---

## 6. `git pull`

Busca as alterações que estão no repositório remoto e atualiza seu código local.

```bash
git pull
```

Imagine que outra pessoa fez alterações no projeto e enviou para o repositório remoto.

Você pode usar `git pull` para trazer essas alterações para sua máquina.

De forma simplificada:

```text
Repositório remoto
        ↓
     git pull
        ↓
    Sua máquina
```

> ⚠️ Em projetos compartilhados, é comum atualizar seu código antes de começar a trabalhar.

---

## 7. `git push`

Envia seus commits locais para o repositório remoto.

```bash
git push
```

De forma simplificada:

```text
Sua máquina
    ↓
  git push
    ↓
Repositório remoto
```

Depois do `push`, suas alterações ficam disponíveis no repositório remoto.

---

# 🔄 Entendendo o fluxo

Agora que você conhece os principais comandos, vamos juntá-los.

Imagine que você acabou de implementar uma nova funcionalidade.

### 1. Veja o que mudou

```bash
git status
```

### 2. Prepare as alterações

```bash
git add .
```

### 3. Registre as alterações

```bash
git commit -m "feat: adiciona nova funcionalidade"
```

### 4. Envie para o repositório remoto

```bash
git push
```

O fluxo básico é:

```text
git status
     ↓
git add .
     ↓
git commit
     ↓
git push
```

E quando precisar **trazer alterações do repositório remoto**:

```bash
git pull
```

> 💡 Não tente decorar comandos sem entender o fluxo.
>
> O mais importante é **entender o que está acontecendo com o seu código** e saber qual ferramenta usar em cada situação.

---

# 🧪 Agora é com você!

Chega de só ler comando. 😎

A melhor forma de aprender Git é **usando Git**.

## Desafio prático

Crie um pequeno projeto para praticar.

### 1. Crie uma pasta

```bash
mkdir meu-primeiro-projeto
```

Entre nela:

```bash
cd meu-primeiro-projeto
```

### 2. Inicialize o Git

```bash
git init
```

### 3. Crie um arquivo

Crie um arquivo chamado:

```text
README.md
```

Adicione algum conteúdo nele.

### 4. Confira o status

```bash
git status
```

Observe o que o Git está mostrando.

### 5. Adicione o arquivo

```bash
git add .
```

Confira novamente:

```bash
git status
```

Observe a diferença.

### 6. Crie seu primeiro commit

```bash
git commit -m "docs: adiciona README do projeto"
```

### 7. Crie um repositório remoto

Crie um repositório no GitHub e conecte seu projeto local a ele.

Depois, envie seu código:

```bash
git push
```

### 8. Faça uma nova alteração

Edite o `README.md` e adicione alguma informação.

Depois:

```bash
git status
```

Adicione a alteração:

```bash
git add .
```

Crie um novo commit:

```bash
git commit -m "docs: atualiza README"
```

E envie novamente:

```bash
git push
```

---

# 🎯 O que você precisa entender?

Ao terminar esse exercício, você deve conseguir explicar com suas próprias palavras:

* O que é Git?
* O que é um repositório?
* Qual a diferença entre repositório local e remoto?
* Para que serve `git init`?
* Quando usar `git clone`?
* Para que serve `git status`?
* Qual a diferença entre `git add` e `git commit`?
* Quando usar `git pull`?
* Quando usar `git push`?
* O que é um commit?
* Por que devemos escrever boas mensagens de commit?
* O que significam `feat`, `fix`, `docs` e `refactor`?

> 🚀 **Não tenha pressa para decorar tudo.**
>
> Desenvolvedores não sabem todos os comandos de cabeça. O importante é entender o problema, saber o que precisa ser feito e **saber pesquisar quando não souber**.

---

## 📚 Para continuar estudando

Se algum comando ou conceito não fizer sentido, **pesquise antes de pedir a resposta**.

Essa é uma habilidade que você vai usar durante toda a sua carreira como desenvolvedor.

* [Documentação oficial do Git](https://git-scm.com/doc)
* [Pro Git — Livro gratuito](https://git-scm.com/book/pt-br/v2)
* [GitHub Docs — Sobre o Git](https://docs.github.com/pt/get-started/using-git/about-git)
