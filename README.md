# 🚀 Desafio Python — HelpDesk API

> **Nível:** Júnior → Júnior avançado  
> **Dificuldade:** ⭐⭐⭐☆☆  
> **Objetivo:** construir uma aplicação real utilizando Python

---

## 🎯 O desafio

Imagine que uma pequena empresa precisa de um sistema simples para controlar os chamados de suporte dos seus funcionários.

Atualmente, os funcionários enviam mensagens pelo WhatsApp:

> "Meu computador está muito lento."

> "Não consigo acessar o sistema."

> "A impressora não está funcionando."

O problema é que os chamados se perdem facilmente e ninguém consegue saber quais problemas estão pendentes, quem está responsável por cada atendimento ou quais chamados já foram resolvidos.

### Sua missão

Construir uma **API REST de HelpDesk** utilizando Python.

A aplicação deverá permitir:

- Cadastrar usuários
- Abrir chamados
- Consultar chamados
- Atualizar chamados
- Alterar o status de um chamado
- Atribuir um chamado a um responsável
- Encerrar chamados
- Consultar informações sobre os chamados
- Excluir usuário
- Excluir chamado

Você **não receberá um passo a passo de como fazer cada funcionalidade**.
A ideia é que você pesquise, leia documentação, teste possibilidades, erre, corrija e aprenda durante o desenvolvimento.

> 💡 Na vida real, ninguém entrega a documentação completa dizendo exatamente qual código você precisa escrever. Saber pesquisar faz parte da profissão.

### Link Apoio
* [O que são métodos HTTP?](https://blog.postman.com/what-are-http-methods/)
* [API Methods](https://www.moesif.com/blog/technical/api-methods/)
* [O que é API, conceitos, benefícios e exemplos práticos](https://www.youtube.com/watch?v=luvsk5YjU6c)

---

# 🧠 O que você vai precisar aprender

Durante o desafio, você provavelmente precisará pesquisar sobre:

- Python
- Funções
- Classes
- Listas e dicionários
- Módulos e pacotes
- Tratamento de exceções
- Ambientes virtuais (`venv`)
- `pip`
- APIs REST
- HTTP
- JSON
- FastAPI
- SQLite
- SQL
- CRUD
- Validação de dados
- Status codes
- Testes automatizados
- Git
- Organização de projetos

Não precisa saber tudo antes de começar.

**O desafio foi criado justamente para você aprender essas coisas enquanto desenvolve.**

---

# 🛠️ Tecnologias

Utilize obrigatoriamente:

- **Python 3**
- **FastAPI**
- **SQLite**
- **Git**

Você pode utilizar outras bibliotecas se achar necessário, mas deverá saber explicar por que escolheu utilizá-las.

---
## 🌱 Antes de começar: Git

Antes de colocar a mão no código, você vai precisar aprender o básico de **Git**.

Durante o desafio, você deverá utilizar Git para versionar seu projeto e publicar seu código em um repositório remoto.

Não precisa saber tudo de Git agora. O objetivo é entender o fluxo básico e começar a criar o hábito de versionar seu código.

### 📚 Material de apoio

Preparei um guia separado com os principais comandos que você vai precisar:

👉 **[Guia de Git](./docs/git.md)**

No guia você encontrará exemplos práticos de:

* `git init`
* `git clone`
* `git status`
* `git add`
* `git commit`
* `git pull`
* `git push`

### 🎯 Ao final

Seu projeto deverá estar versionado em um repositório remoto e conter commits que mostrem a evolução do desenvolvimento.

> 💡 Não tenha medo de pesquisar. Desenvolvedor não é quem sabe todos os comandos de cabeça — é quem sabe **o que precisa fazer e como encontrar a informação para fazer**.

---
# 📋 Requisitos funcionais

## 1. 👤 Usuários

A aplicação deverá permitir cadastrar usuários.

Um usuário deve possuir, no mínimo:

```text
id
nome
email
data_de_criacao
```

A API deverá permitir:

```http
POST /usuarios
GET /usuarios
GET /usuarios/{id}
```

Você deverá decidir:

* Como validar o nome?
* Como validar o email?
* O que acontece quando o email já existe?
* Qual status HTTP retornar em cada situação?

---

# 🎫 2. Chamados

Um chamado deverá possuir, no mínimo:

```text
id
titulo
descricao
status
prioridade
usuario_id
responsavel_id
data_de_criacao
data_de_atualizacao
```

### Status sugeridos

```text
ABERTO
EM_ATENDIMENTO
RESOLVIDO
CANCELADO
```

### Prioridades sugeridas

```text
BAIXA
MEDIA
ALTA
CRITICA
```

Você pode utilizar outros nomes, desde que documente sua decisão.

---

# 🔄 3. CRUD de chamados

Implemente:

```http
POST   /chamados
GET    /chamados
GET    /chamados/{id}
PUT    /chamados/{id}
DELETE /chamados/{id}
```

O endpoint de listagem deverá permitir pelo menos **um filtro**.

Por exemplo:

```http
GET /chamados?status=ABERTO
```

ou:

```http
GET /chamados?prioridade=ALTA
```

ou:

```http
GET /chamados?usuario_id=10
```

Você decide quais filtros serão suportados.

---

# 👨‍💻 4. Responsável pelo chamado

Um chamado poderá ser atribuído a um usuário responsável.

Crie uma operação que permita fazer essa atribuição.

Por exemplo:

```http
PATCH /chamados/{id}/responsavel
```

O comportamento fica por sua conta.

Mas existem algumas regras:

* O usuário responsável precisa existir
* Um chamado inexistente não pode ser atualizado
* Você deve decidir o que acontece se o chamado já estiver encerrado

---

# 🚦 5. Regras de negócio

Aqui começa a parte mais interessante.

A aplicação deverá possuir algumas regras de negócio.

Implemente pelo menos:

### Regra 1

Um chamado criado deve iniciar como:

```text
ABERTO
```

### Regra 2

Um chamado `RESOLVIDO` não pode voltar para `EM_ATENDIMENTO`.

### Regra 3

Um chamado `CANCELADO` não pode receber novas alterações.

### Regra 4

Não é possível atribuir um chamado a um usuário inexistente.

### Regra 5

Título e descrição são obrigatórios.

### Regra 6

O email de um usuário deve ser único.

### Regra 7

Crie pelo menos **2 regras de negócio adicionais** por conta própria.

> 💡 Pense em situações que poderiam acontecer em um sistema real de HelpDesk.

---

# 🗄️ 6. Banco de dados

Os dados não podem ficar somente em memória.

Utilize **SQLite**.

Você deverá criar pelo menos duas tabelas:

```text
usuarios
chamados
```

E deverá existir um relacionamento entre elas.

Você precisará pesquisar:

* `CREATE TABLE`
* `PRIMARY KEY`
* `FOREIGN KEY`
* `INSERT`
* `SELECT`
* `UPDATE`
* `DELETE`
* `JOIN`

### 💡 Dica

Não precisa começar sabendo SQL.

Pesquise conforme a necessidade.

---

# 🌐 7. API REST

Utilize **FastAPI**.

A aplicação deverá disponibilizar endpoints HTTP e retornar dados em JSON.

Você deverá pesquisar e entender conceitos como:

```text
GET
POST
PUT
PATCH
DELETE
```

E também:

```text
200
201
204
400
404
409
422
500
```

Não basta fazer a API funcionar.

Você deverá escolher **status codes coerentes** para cada situação.

---

# ❌ 8. Tratamento de erros

A API não deve simplesmente quebrar quando recebe uma informação inválida.

Por exemplo:

```http
GET /chamados/999999
```

Se o chamado não existir, a aplicação deverá retornar uma resposta apropriada.

Outro exemplo:

```json
{
    "titulo": "",
    "descricao": ""
}
```

A aplicação deverá rejeitar essa requisição.

Pesquise sobre:

* Exceptions
* Validação
* `HTTPException`
* HTTP Status Codes
* Pydantic

---

# 🧪 9. Testes

Crie testes automatizados para sua aplicação.

Você deverá possuir **no mínimo 10 testes**.

Os testes devem contemplar:

* Criação de usuário
* Criação de chamado
* Consulta de chamado
* Chamado inexistente
* Usuário inexistente
* Atualização de chamado
* Alteração de status
* Regra de negócio
* Validação de dados
* Algum cenário de erro

Você pode escolher a ferramenta de testes.

Uma escolha comum no ecossistema Python é o **pytest**.

---

# 📁 10. Organização do projeto

Não coloque tudo dentro de um único `main.py`.

Você deverá pesquisar e definir uma estrutura organizada.

Por exemplo:

```text
helpdesk/
│
├── app/
│   ├── main.py
│   │
│   ├── models/
│   ├── schemas/
│   ├── routers/
│   ├── services/
│   ├── repositories/
│   └── database/
│
├── tests/
│
├── .gitignore
├── requirements.txt
├── README.md
└── ...
```

> ⚠️ Essa estrutura é apenas uma sugestão.

Você pode organizar de outra maneira.

Mas deverá conseguir explicar:

> "Por que eu organizei meu projeto dessa forma?"

---

# 📚 11. README

Seu projeto deverá possuir documentação.

O README deve explicar:

### O projeto

O que é e qual problema resolve.

### Tecnologias

Exemplo:

```text
Python
FastAPI
SQLite
Pytest
```

### Como executar

Uma pessoa que nunca viu seu projeto deverá conseguir executá-lo seguindo seu README.

### Exemplos de requisição

Mostre alguns exemplos de:

```http
POST
GET
PUT
PATCH
DELETE
```

### Decisões técnicas

Explique brevemente algumas decisões tomadas durante o desenvolvimento.

Por exemplo:

> "Escolhi SQLite porque o projeto possui baixa complexidade e não necessita de um servidor de banco separado."

---

# 🔎 Fontes para pesquisa

Você **pode e deve pesquisar na internet** durante o desenvolvimento.

Na verdade, algumas partes do desafio foram propositalmente deixadas abertas.

Você deverá descobrir:

* Como criar uma API com FastAPI
* Como criar um ambiente virtual
* Como conectar Python ao SQLite
* Como criar as tabelas
* Como fazer validação
* Como retornar erros HTTP
* Como escrever testes
* Como organizar o projeto
* Como documentar uma API

## 🐍 Python

* [Tutorial oficial do Python em português](https://docs.python.org/pt-br/3/tutorial/)
* [Documentação oficial do Python](https://docs.python.org/3/)

## ⚡ FastAPI

* [Tutorial oficial do FastAPI](https://fastapi.tiangolo.com/pt/tutorial/)
* [Primeiros passos com FastAPI](https://fastapi.tiangolo.com/tutorial/first-steps/)

## 🗄️ SQLite

* [Documentação oficial do SQLite](https://sqlite.org/docs.html)
* [SQLite com Python](https://docs.python.org/3/library/sqlite3.html)

## 🧪 Pytest

* [Documentação oficial do pytest](https://docs.pytest.org/)

## 🌱 Git

* [Documentação oficial do Git](https://git-scm.com/doc)

---

# 🚫 Uma regra importante

## Pesquisar é permitido. Copiar sem entender, não.

Se você encontrou um código na internet e utilizou no projeto, precisa entender:

> O que esse código faz?

> Por que ele funciona?

> O que aconteceria se eu alterasse determinada parte?

> Existe outra maneira de fazer isso?

Não tenha medo de pesquisar.

**Desenvolvedores pesquisam o tempo inteiro.**

A habilidade que você precisa desenvolver não é decorar todo o Python.

É saber:

**problema → pesquisa → tentativa → erro → aprendizado → solução**

---

# ⭐ Desafios extras

Terminou tudo?

Então agora começa a brincadeira. 😈

Escolha pelo menos **2** dos desafios abaixo.

---

## ⭐ Desafio 1 — Paginação

Implemente:

```http
GET /chamados?page=1&limit=10
```

Pesquise sobre paginação de APIs.

---

## ⭐ Desafio 2 — Ordenação

Permita ordenar os chamados:

```http
GET /chamados?sort=data_de_criacao
```

Você deverá decidir:

* Quais campos podem ser utilizados?
* Ordem crescente ou decrescente?
* O que acontece quando o campo informado não existe?

---

## ⭐ Desafio 3 — Busca

Permita pesquisar chamados pelo título:

```http
GET /chamados?search=computador
```

---

## ⭐ Desafio 4 — Dashboard

Crie:

```http
GET /dashboard
```

Que retorne algo semelhante a:

```json
{
    "total": 150,
    "abertos": 30,
    "em_atendimento": 20,
    "resolvidos": 90,
    "cancelados": 10
}
```

---

## ⭐ Desafio 5 — Docker

Crie um `Dockerfile` para executar a aplicação.

Pesquise:

* Docker
* Imagens
* Containers
* Dockerfile
* Portas

---

## ⭐ Desafio 6 — Autenticação

Implemente algum mecanismo de autenticação.

Você deverá pesquisar:

* JWT
* Tokens
* Autenticação
* Autorização
* Hash de senha

> 🔐 Não armazene senhas em texto puro.

---

## ⭐ Desafio 7 — Logs

Adicione logs à aplicação.

Registre, por exemplo:

```text
Chamado criado
Chamado atualizado
Usuário não encontrado
Erro ao consultar banco
```

Pesquise sobre o módulo `logging` do Python.

---

# 🏆 Critérios de avaliação

| Critério              |     Peso |
| --------------------- | -------: |
| Python e lógica       |      15% |
| API REST              |      15% |
| Banco de dados        |      15% |
| Regras de negócio     |      15% |
| Organização do código |      10% |
| Tratamento de erros   |      10% |
| Testes                |      10% |
| Git e documentação    |      10% |
| **Total**             | **100%** |

### ⭐ Bônus

Até **10% adicional** pelos desafios extras.

---

# 📦 Entrega

O projeto deverá ser disponibilizado em um repositório Git.

O repositório deve conter:

```text
README.md
código fonte
testes
requirements.txt
.gitignore
```

O README deve explicar como executar o projeto do zero.

---

# 🎤 Apresentação

Na apresentação, você deverá conseguir explicar:

1. Qual problema sua aplicação resolve?
2. Como sua API funciona?
3. Como os dados são armazenados?
4. Quais regras de negócio você implementou?
5. Como você tratou erros?
6. Como seus testes funcionam?
7. Qual foi a parte mais difícil?
8. O que você pesquisou para conseguir terminar?
9. O que você faria diferente se tivesse mais tempo?

**Não é necessário saber responder tudo de cabeça.**

Mas você precisa conseguir explicar aquilo que colocou no seu próprio código.

---

# 🎓 O que esperamos ao final

Ao terminar este projeto, você não precisa ser especialista em Python.

Mas deverá ser capaz de dizer:

> "Eu consigo pegar um problema, pesquisar as tecnologias necessárias, construir uma solução, testar, documentar e versionar meu código."

Esse é o objetivo real do desafio.

Programação não é decorar sintaxe.

É aprender a **resolver problemas**.

---

# 🚀 Boa sorte!

Você provavelmente vai travar em algum momento.

Vai pesquisar.

Vai encontrar três soluções diferentes.

Vai testar uma.

Vai quebrar outra.

Vai descobrir que esqueceu alguma coisa.

Vai pesquisar de novo.

E vai resolver.

**Isso não significa que você está indo mal.**

Isso é programação. 🐍💻
