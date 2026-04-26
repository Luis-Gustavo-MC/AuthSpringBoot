# AuthSpringBoot 🔐

O **AuthSpringBoot** é uma API REST desenvolvida com Java e Spring Boot para implementar um ecossistema de segurança robusto baseado em **OAuth2** e **JWT (JSON Web Tokens)**. O projeto utiliza o fluxo `password grant` para autenticação e autorização de usuários, separando as responsabilidades de Servidor de Autorização e Servidor de Recursos.

## 🚀 Tecnologias e Padrões
* **Java 17+**
* **Spring Boot 3**
* **Spring Security & OAuth2**
* **JWT (JSON Web Token)**
* **Fluxo de Autenticação**: Password Grant Type.

## 🛠️ Funcionalidades e Endpoints
Baseado na coleção de testes incluída no projeto, a API está dividida em:

### 1. Authorization Server (Servidor de Autorização)
Responsável por validar as credenciais e emitir os tokens de acesso.
* **Endpoint de Login**: `POST /oauth2/token`.
* **Autenticação**: Requer **Basic Auth** (Client ID e Client Secret) no cabeçalho e as credenciais do usuário (`username`/`password`) no corpo da requisição via `x-www-form-urlencoded`.

### 2. Resource Server (Servidor de Recursos)
Endpoints protegidos que gerenciam o domínio de produtos:
* **Listar Produtos**: `GET /products` (Acesso Público).
* **Detalhar Produto**: `GET /products/{id}` (Requer **Bearer Token** válido).
* **Criar Produto**: `POST /products` (Restrito a usuários com perfil **ADMIN**).

## 🧪 Como Testar (Postman)
Para facilitar o desenvolvimento, utilize o arquivo `Oauth2 JWT password.postman_collection.json` fornecido no repositório.

1.  **Importe a coleção** no seu Postman.
2.  **Configure o Ambiente**: Defina as variáveis globais ou de ambiente:
    * `ashost`: URL do Servidor de Autorização (ex: `http://localhost:8080`).
    * `rshost`: URL do Servidor de Recursos (ex: `http://localhost:8080`).
    * `client-id` / `client-secret`: Credenciais da aplicação.
    * `username` / `password`: Credenciais de um usuário cadastrado.
3.  **Token Automático**: Ao realizar o login com sucesso, a coleção possui um script que salva automaticamente o token na variável `{{token}}` para as próximas requisições.

## ⚙️ Configuração Local
1.  Clone o repositório:
    ```bash
    git clone https://github.com/Luis-Gustavo-MC/AuthSpringBoot.git
    ```
2.  Configure o banco de dados no arquivo `application.properties`.
3.  Execute a aplicação via Maven:
    ```bash
    mvn spring-boot:run
    ```

## 📚 Créditos e Contribuição
Este projeto foi desenvolvido seguindo as orientações e padrões de excelência do curso:

Curso: Java Spring Professional

Instrutor: Nelio Alves (DevSuperior)

## 🤝 Contribuição
Sinta-se à vontade para abrir *Issues* ou enviar *Pull Requests* para melhorias.

A implementação reflete as melhores práticas de segurança ensinadas no treinamento para a construção de sistemas prontos para produção.

**Mantido por:** [Luis Gustavo](https://github.com/Luis-Gustavo-MC).
