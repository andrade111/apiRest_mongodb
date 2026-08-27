<div align="center">

# 🍃 Spring Boot & MongoDB REST API

*Uma API robusta e escalável para redes sociais, explorando o potencial de bancos NoSQL orientados a documentos.*

[![Java](https://img.shields.io/badge/Java-11%2B-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)](https://www.oracle.com/java/)
[![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.x-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white)](https://spring.io/projects/spring-boot)
[![MongoDB](https://img.shields.io/badge/MongoDB-4.7%2B-47A248?style=for-the-badge&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![License](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](LICENSE)

</div>

---

### 💡 Sobre o Projeto

Esta aplicação foi desenvolvida com o objetivo de demonstrar a criação de uma **Web API RESTful** utilizando a pilha Java com **Spring Boot** conectada a um banco de dados não-relacional (**MongoDB**). 

O sistema modela uma estrutura de rede social com relacionamentos entre documentos (usuários, postagens e comentários), abordando conceitos fundamentais como **Data Transfer Objects (DTOs)**, **consultas customizadas com regex** e **tratamento global de exceções HTTP**.

---

### 🎯 Funcionalidades Principais

- 👤 **CRUD de Usuários:** Gestão completa de cadastros com busca por ID e suporte a atualização parcial/total.
- 📝 **Postagens & Autorias:** Associação de publicações aos seus respectivos autores utilizando referências (`DBRef`).
- 💬 **Comentários Aninhados:** Utilização de objetos aninhados (*Embedded Documents*) para garantir alta performance de leitura.
- 🔍 **Engine de Busca Avançada:**
  - Filtro simples por palavra-chave no título das postagens (usando `@Query` com *case-insensitive* regex).
  - Pesquisa multicritério combinando texto livre e intervalo de datas (`minDate` e `maxDate`).
- 🛡️ **Respostas HTTP Padronizadas:** Exceções tratadas centralizadamente com códigos de status HTTP apropriados (`404 Not Found`, etc.).

---

### 🧱 Arquitetura e Estrutura

```text
com.seuusuario.apirest_mongodb/
│
├── 🎛️ resources/       # Endpoints REST da API (UserResource, PostResource)
│   └── exception/      # Handler global de exceções (ResourceExceptionHandler)
│
├── 🧠 services/        # Camada de regras de negócio (UserService, PostService)
│
├── 📦 repository/      # Interfaces de acesso ao MongoDB (MongoRepository)
│
├── 📑 dto/             # Data Transfer Objects (UserDTO, AuthorDTO, CommentDTO)
│
├── 💎 domain/          # Entidades/Documentos NoSQL (User, Post)
│
└── ⚙️ config/          # Carga inicial e seeding do banco de dados
```

---

### 📡 Guia de Endpoints

<details>
<summary>📋 <b>Clique para expandir a tabela completa de rotas da API</b></summary>

<br/>

#### 👤 Recursos de Usuários (`/users`)

| Método | Endpoint | Descrição |
| :---: | :--- | :--- |
| `GET` | `/users` | Retorna todos os usuários cadastrados |
| `GET` | `/users/{id}` | Busca um usuário por seu ID único |
| `POST` | `/users` | Cadastra um novo usuário |
| `PUT` | `/users/{id}` | Atualiza os dados de um usuário existente |
| `DELETE` | `/users/{id}` | Remove um usuário do banco de dados |
| `GET` | `/users/{id}/posts` | Retorna todas as postagens publicadas por um usuário |

#### 📝 Recursos de Postagens (`/posts`)

| Método | Endpoint | Descrição |
| :---: | :--- | :--- |
| `GET` | `/posts/{id}` | Retorna os detalhes de um post específico com seus comentários |
| `GET` | `/posts/titlesearch` | Busca posts que contenham o texto informado no título |
| `GET` | `/posts/fullsearch` | Pesquisa avançada por texto e intervalo de datas |

</details>

---

### 🚀 Como Executar

#### 📌 Pré-requisitos
- **Java JDK 11** ou superior
- **Docker** ou serviço local do **MongoDB** (porta `27017`)

#### 1️⃣ Subir o MongoDB via Docker
```bash
docker run -d -p 27017:27017 --name mongodb mongo
```

#### 2️⃣ Clonar e iniciar a aplicação
```bash
# Clone o repositório
git clone [https://github.com/andrade111/apiRest_mongodb.git](https://github.com/andrade111/apiRest_mongodb.git)

# Acesse a pasta do projeto
cd apiRest_mongodb

# Execute o projeto com o Maven Wrapper
./mvnw spring-boot:run
```

🌐 **API disponível em:** `http://localhost:8080`

---

<div align="center">

Desenvolvido com ☕ por **[Gabriel Andrade](https://github.com/andrade111)** • Licença MIT

</div>
