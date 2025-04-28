# Documentação Super Já

**Link do Repositório:** [GitHub - SuperJa](https://github.com/abilafora/superJa)  

**Projeto:** Aplicativo de Delivery

**Integrantes:**
- [Abiqueila de Souza](https://github.com/abilafora)
- [Evelyn Pereira](https://github.com/evelyn-pereira)
- [Hellen Gleice](https://github.com/hellengleice)
- [Isabela Santos](https://github.com/isabelasantos)
- [Maytê Araújo](https://github.com/maytearaujo)
- [Thainara Cruz](https://github.com/thainaracruz)

## Objetivo

O **SuperJá** é um aplicativo de delivery destinado a realizar entregas de compras feitas em supermercados. Ele permite o cadastro de usuários, gerenciamento de produtos e associação dos produtos a suas respectivas categorias.

---

## Estrutura do Projeto

### 1. **Packages Utilizados**:

#### **Model**
- **Representa os dados (Produto, Usuário, Categoria)**.
  - **Usuario**:  
    Atributos: `id`, `nome`, `e-mail`, `foto`, `senha`.  
    Relacionamento: Um usuário pode ter vários produtos.
  
  - **UsuarioLogin**:  
    Atributos: `id`, `nome`, `e-mail`, `foto`, `senha`, `token`.  
    Relacionamento: Cada usuário tem um token único para login.

  - **Produto**:  
    Atributos: `id`, `nomeProduto`, `estoque`, `preco`, `validade`.  
    Relacionamento: Cada produto pertence a uma categoria e pode estar associado a vários usuários.

  - **Categoria**:  
    Atributos: `id`, `setor`.  
    Relacionamento: Uma categoria pode ter vários produtos associados.

#### **Repository**
- **Camada responsável pela comunicação com o banco de dados (Spring Data JPA)**.
  - **UsuarioRepository**: Manipula dados de usuários.
  - **ProdutoRepository**: Manipula dados de produtos.
  - **CategoriaRepository**: Manipula dados de categorias.

#### **Controller**
- **Expõe funcionalidades com os endpoints REST**.
  - **UsuarioController**: Endpoints para cadastro, atualização e consulta de usuários.
  - **ProdutoController**: Endpoints para cadastro, atualização, consulta e exclusão de produtos.
  - **CategoriaController**: Endpoints para cadastro, atualização e consulta de categorias.

#### **Service**
- **Camada de lógica de negócios**.
  - **UsuarioService**: Valida o cadastro de usuário, garantindo a autenticação antes do cadastro.
  - **ProdutoService**: Aplica desconto de 10% no preço de produtos acima de R$ 50,00.

#### **Security**
- **Camada de segurança**: Responsável pela autenticação e autorização no sistema. 
  - **Classes**: `UserDetailsServiceImpl`, `UserDetailsImpl`, `JwtService`, `JwtAuthFilter`, `BasicSecurityConfig`.

---

## Endpoints

### 1. **UsuarioController**
- **GET /usuarios/logar**: Permite o login do usuário.
- **GET /usuarios/all**: Retorna todos os usuários cadastrados.
- **GET /usuarios/{id}**: Retorna um usuário específico pelo ID.
- **POST /usuarios/cadastrar**: Cria um novo usuário (somente mulheres).
- **PUT /usuarios/atualizar**: Atualiza os dados de um usuário.

### 2. **ProdutoController**
- **GET /produtos**: Retorna todos os produtos cadastrados.
- **GET /produtos/{id}**: Retorna um produto específico pelo ID.
- **GET /produtos/nomeProduto/{nomeProduto}**: Retorna produtos filtrados pelo nome.
- **POST /produtos**: Cria um novo produto, associando-o a uma categoria e a um usuário.
- **PUT /produtos**: Atualiza os dados de um produto.
- **DELETE /produtos/{id}**: Exclui um produto pelo ID.

### 3. **CategoriaController**
- **GET /categorias**: Retorna todas as categorias cadastradas.
- **GET /categorias/{id}**: Retorna uma categoria específica pelo ID.
- **GET /categorias/setor/{setor}**: Filtra categorias pelo setor.
- **POST /categorias**: Cria uma nova categoria.
- **PUT /categorias**: Atualiza os dados de uma categoria.
- **DELETE /categorias/{id}**: Exclui uma categoria pelo ID.

---

## Validações

### Cadastro de Produto
- A criação de um produto exige o preenchimento correto dos campos obrigatórios: `nomeProduto`, `estoque`, `preco` e `validade`.
- Produtos com preço acima de R$ 50,00 recebem um desconto de 10%.

---

## Tecnologias Utilizadas

- **Spring Framework**: Framework principal para desenvolvimento da aplicação.
- **Spring Boot**: Facilita a criação e configuração do projeto Spring.
- **JPA (Java Persistence API)**: Mapeia objetos Java para tabelas de bancos de dados relacionais.
- **Spring Web**: Criação de APIs RESTful.
- **Insomnia**: Ferramenta para testar e depurar APIs RESTful.
- **MySQL**: Banco de dados relacional para persistência dos dados.
- **Swagger**: Geração de documentação automatizada da API, código e testes.

---

## Como Executar o Projeto

### Pré-requisitos:
- **Java 17 ou superior**: O projeto usa o Spring Boot 2.x.
- **IDE** (como STS): Para editar e rodar o projeto.
- **Maven**: Para gerenciar dependências

---
