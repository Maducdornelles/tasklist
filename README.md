# 📝 TaskList

Uma aplicação simples de linha de comando desenvolvida em Go para gerenciar tarefas.  
Utiliza contêineres Docker para facilitar a execução e o isolamento do ambiente.

## 🚀 Tecnologias Utilizadas

- [Go](https://golang.org/)
- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)
- [Postman](https://www.postman.com/)

## 📦 Pré-requisitos

- [Docker](https://www.docker.com/get-started) instalado
- [Docker Compose](https://docs.docker.com/compose/install/) instalado
- [Postman](https://www.postman.com/downloads/) para testar a API

## ⚙️ Como Executar

1. **Clone o repositório:**
   ```bash
   git clone https://github.com/Maducdornelles/tasklist.git
   cd tasklist
   ```

2. **Crie um arquivo `docker-compose.yml` no diretório raiz com o seguinte conteúdo:**
   ```yaml
   version: '3'

   services:
     tasklist:
       build: .
       ports:
         - "8080:8080"
       volumes:
         - .:/app
       command: go run main.go
   ```

3. **Construa e inicie os contêineres com Docker Compose:**
   ```bash
   docker-compose up --build
   ```

A aplicação estará disponível em `http://localhost:8080`.

## 🧪 Testando com Postman

Você pode testar a API utilizando o Postman.  
Abaixo estão os endpoints disponíveis:

### ➕ Adicionar Tarefa

- **Método:** `POST`
- **URL:** `http://localhost:8080/tasks`
- **Body (JSON):**
  ```json
  {
    "title": "estudar php",
    "completed": false
  }
  ```

### 📋 Listar Tarefas

- **Método:** `GET`
- **URL:** `http://localhost:8080/tasks`

### ✏️ Atualizar Tarefa

- **Método:** `PUT`
- **URL:** `http://localhost:8080/tasks/{id}`
- **Body (JSON):**
  ```json
  {
    "title": "estudar Go",
    "completed": true
  }
  ```

### ❌ Remover Tarefa

- **Método:** `DELETE`
- **URL:** `http://localhost:8080/tasks/{id}`

> Substitua `{id}` pelo ID da tarefa que deseja remover.

## 🧹 Encerrando a Aplicação

Para parar e remover os contêineres:
```bash
docker-compose down
```
