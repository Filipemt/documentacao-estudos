## 🔹 Maven

Ferramenta de gerenciamento de dependências e automação de build.

- Usa o arquivo `pom.xml` para configurar bibliotecas e plugins.
- Baixa bibliotecas automaticamente do Maven Central.
- Garante que o projeto funcione igual em qualquer máquina.
- Muito usado com Spring Boot.

### 🛠️ Build Lifecycle (Ciclo de Build do Maven)

As fases do ciclo de build são:

| Fase     | O que faz                                   |
|----------|----------------------------------------------|
| clean    | Remove arquivos antigos de build             |
| validate | Verifica se o projeto está estruturado       |
| compile  | Compila o código fonte                       |
| test     | Executa testes automatizados                 |
| package  | Empacota o projeto (.jar, .war)              |
| install  | Instala o artefato no repositório local      |
| deploy   | Publica o artefato em um repositório remoto  |

### 🔹 Spring Boot

- **Spring Boot** é um framework do ecossistema Spring que facilita a criação de aplicações Java, especialmente APIs REST.

- Focado em **agilidade e produtividade**, ele reduz a configuração manual usando o conceito de **auto-configuração**.

- Permite criar **aplicações standalone**, com **servidor embarcado** (como Tomcat), sem necessidade de configurar servidores externos.

- Utiliza **anotações** para estruturar a aplicação em camadas:
  - `@RestController` – Camada de controle (API)
  - `@Service` – Camada de regra de negócio
  - `@Repository` – Acesso ao banco de dados
  
- Integra facilmente com **Spring Data JPA** para comunicação com bancos relacionais.
- Também oferece suporte a segurança, monitoramento, testes, e configurações externas via `application.properties` ou `application.yml`.

### 🔹 JPA (Java Persistence API)

- **JPA** é uma especificação Java para persistência de dados em bancos relacionais.
- O **Hibernate** é a implementação mais comum do JPA no ecossistema Spring.
- Utiliza o conceito de **ORM (Object-Relational Mapping)**: transforma objetos Java em registros de tabelas.
- Usamos anotações para mapear entidades:
  - `@Entity`, `@Table`, `@Id`, `@GeneratedValue`, `@Column`
- O Spring simplifica ainda mais com o uso de **JpaRepository**, que já fornece métodos CRUD prontos:
  - `save()`, `findAll()`, `findById()`, `deleteById()`
- Também é possível criar consultas personalizadas com:
  - **Query Methods**: `findByNome`, `findByEmailContaining`
  - **@Query**: permite escrever consultas JPQL/SQL diretamente

  ### 🔹 API REST

- **API REST** é uma arquitetura para comunicação entre sistemas via protocolo HTTP.
- Funciona no modelo **request/response**, geralmente com dados em **JSON**.
- Cada recurso é acessado por meio de uma URL e manipulado com **verbos HTTP**:

| Verbo HTTP | Operação |
|------------|----------|
| `GET`      | Leitura (Read) |
| `POST`     | Criação (Create) |
| `PUT` / `PATCH` | Atualização (Update) |
| `DELETE`   | Remoção (Delete) |

- As respostas da API trazem um **status code** indicando o resultado:

| Código | Significado |
|--------|-------------|
| 200    | OK (sucesso) |
| 201    | Created (criado com sucesso) |
| 400    | Bad Request (erro na requisição) |
| 404    | Not Found (recurso não encontrado) |
| 500    | Internal Server Error (erro inesperado no servidor) |

- No Spring Boot, usamos:
  - `@RestController` para expor endpoints
  - `@RequestMapping` ou `@GetMapping`, `@PostMapping`, etc. para mapear rotas
- Retorno padrão é em **JSON**, graças à anotação `@RestController`
- Erros e exceções são tratados com `try-catch`, classes customizadas e `ResponseEntity`

#### 🧠 Extras para uma entrevista:
- APIs REST são **stateless** (não armazenam estado entre requisições).
- É possível **versionar endpoints** (ex: `/api/v1/produtos`).
- Podemos usar filtros, validações (`@Valid`), e controle de status de forma personalizada.
- Em aplicações REST, o design limpo dos endpoints e o uso correto dos verbos HTTP são sinais de boas práticas.

### 🔹 Camadas da aplicação (Controller, Service, Repository)

- Arquitetura em camadas ajuda a manter o código organizado e escalável.
- No Spring Boot, usamos três camadas principais:

#### 1. Controller
- Responsável por **receber requisições HTTP** e **retornar respostas**.
- Mapeia os endpoints (`@RestController`, `@GetMapping`, etc).
- Não deve conter regra de negócio nem lógica de acesso a dados.

#### 2. Service
- Camada intermediária com as **regras de negócio da aplicação**.
- Contém validações, cálculos, chamadas a repositórios e construção de DTOs.
- Anotada com `@Service`.

#### 3. Repository
- Responsável por **persistir e consultar dados no banco**.
- Usa `JpaRepository` para métodos CRUD e consultas personalizadas.
- Anotada com `@Repository` (opcional com Spring Data JPA).

---

#### 🧠 Boas práticas complementares:

- **DTO (Data Transfer Object)**: classe usada para transportar dados entre camadas.
- **DAO (Data Access Object)**: alternativa ao repositório para abstrair acesso a dados.
- **Injeção de dependência** com `@Autowired` ou construtores.
- Cada camada deve ter uma **única responsabilidade** (princípio SRP).