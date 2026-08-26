# 🍃 RESTful API with Spring Boot & MongoDB

[![Java](https://img.shields.io/badge/Java-11%2B-orange?style=for-the-badge&logo=openjdk)](https://www.oracle.com/java/)
[![Spring Boot](https://img.shields.io/badge/Spring_Boot-2.x%2F3.x-6DB33F?style=for-the-badge&logo=spring-boot)](https://spring.io/projects/spring-boot)
[![MongoDB](https://img.shields.io/badge/MongoDB-4.7%2B-47A248?style=for-the-badge&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![License](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](LICENSE)

API RESTful desenvolvida com **Java** e **Spring Boot**, utilizando **MongoDB** como banco de dados NoSQL. O projeto aborda a criação de um sistema de rede social simples (usuários e postagens com comentários), demonstrando relacionamentos entre documentos (*DBRef* e aninhamento de DTOs), manipulação de dados e consultas personalizadas.

---

## 📌 Funcionalidades Principais

- 👥 **Gestão de Usuários (CRUD Completo):** Cadastro, listagem, busca por ID, atualização e remoção de usuários.
- 📝 **Postagens Aninhadas:** Associação de postagens a usuários e visualização das postagens de um usuário específico.
- 💬 **Comentários Aninhados:** Inclusão de comentários em posts através de padrões DTO (*Data Transfer Object*).
- 🔍 **Consultas Personalizadas no MongoDB:**
  - Busca por palavra-chave no título das postagens usando `@Query` do Spring Data.
  - Busca multicritério (texto, intervalo de datas inicial e final).
- 🛡️ **Tratamento Global de Exceções:** Respostas HTTP apropriadas e padronizadas para recursos não encontrados (`404 Not Found`).

---

## 🛠️ Tecnologias e Padrões Utilizados

- **Linguagem:** Java (JDK 11+)
- **Framework Principal:** Spring Boot
- **Acesso a Dados:** Spring Data MongoDB
- **Banco de Dados:** MongoDB (NoSQL orientado a documentos)
- **Padrões de Arquitetura & Design:**
  - **Camadas (Layered Architecture):**
    - `Resource / Controller`: Exposição dos endpoints REST.
    - `Service`: Regras de negócio e orquestração.
    - `Repository`: Interface de persistência estendendo `MongoRepository`.
  - **DTO Pattern (Data Transfer Object):** Otimização do tráfego de dados na rede e encapsulamento de visões específicas.
  - **Exception Handling:** Trata exceções da aplicação via `@ControllerAdvice` e `StandardError`.

---

## 📁 Estrutura do Projeto

```text
src/main/java/com/seuusuario/apirest_mongodb/
├── config/             # Configurações iniciais (Instanciação/Carga de dados no MongoDB)
├── domain/             # Entidades do domínio (User, Post)
├── dto/                # Objetos de Transferência de Dados (UserDTO, AuthorDTO, CommentDTO)
├── repository/         # Interfaces Spring Data MongoRepository
├── resources/          # Controllers / Endpoints REST (UserResource, PostResource)
│   └── exception/      # Tratamento global de exceções da API
└── services/           # Camada de serviços e regras de negócio
```

---

## 📍 Endpoints da API

### **Usuários (`/users`)**

| Método | Endpoint | Descrição |
| :--- | :--- | :--- |
| `GET` | `/users` | Retorna todos os usuários cadastrados |
| `GET` | `/users/{id}` | Retorna um usuário pelo ID |
| `POST` | `/users` | Cria um novo usuário |
| `PUT` | `/users/{id}` | Atualiza os dados de um usuário existente |
| `DELETE` | `/users/{id}` | Remove um usuário |
| `GET` | `/users/{id}/posts` | Retorna todas as postagens de um usuário |

### **Postagens (`/posts`)**

| Método | Endpoint | Descrição |
| :--- | :--- | :--- |
| `GET` | `/posts/{id}` | Retorna uma postagem pelo ID |
| `GET` | `/posts/titlesearch?text=...` | Busca postagens por texto no título |
| `GET` | `/posts/fullsearch?text=...&minDate=...&maxDate=...` | Busca avançada por texto e intervalo de datas |

---

## ⚙️ Pré-requisitos

Para executar o projeto localmente, você precisará de:

- [JDK 11+](https://www.oracle.com/java/technologies/downloads/)
- [Maven](https://maven.apache.org/) (opcional se usar o wrapper `mvnw`)
- [MongoDB Community Server](https://www.mongodb.com/try/download/community) rodando na porta padrão (`27017`) ou via **Docker**.
- Um cliente HTTP para testar a API (ex: [Postman](https://www.postman.com/), [Insomnia](https://insomnia.rest/) ou VS Code Thunder Client).

---

## 🚀 Como Executar o Projeto

1. **Clone o repositório:**
   ```bash
   git clone [https://github.com/andrade111/apiRest_mongodb.git](https://github.com/andrade111/apiRest_mongodb.git)
   ```

2. **Acesse a pasta do projeto:**
   ```bash
   cd apiRest_mongodb
   ```

3. **Certifique-se de que o serviço do MongoDB está em execução:**
   - **Caso use Docker:**
     ```bash
     docker run -d -p 27017:27017 --name mongodb mongo
     ```

4. **Execute a aplicação:**
   ```bash
   ./mvnw spring-boot:run
   ```

5. A API estará acessível em: `http://localhost:8080`

---

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

<p align="center">Desenvolvido por <a href="https://github.com/andrade111">Gusta Andrade</a> 👋</p>
