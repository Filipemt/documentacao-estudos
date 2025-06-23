## 🔹 Banco de Dados com Spring Boot + JPA

O **Spring Boot** usa o **JPA (Java Persistence API)** como solução de persistência de dados com bancos relacionais.

O JPA é uma **especificação**, e o **Hibernate** é a implementação mais usada no ecossistema Spring.  
Ele realiza o **ORM (Mapeamento Objeto-Relacional)**: transforma classes Java em tabelas e objetos em registros do banco.

---

### ✅ Mapeamento com anotações:

| Anotação             | Função                                                |
|----------------------|-------------------------------------------------------|
| `@Entity`            | Indica que a classe será mapeada como uma tabela     |
| `@Id`                | Define o campo como chave primária                    |
| `@GeneratedValue`    | Gera valores automaticamente (ex: ID auto-incremento) |
| `@Column`            | Define os detalhes de uma coluna específica           |

```java
@Entity
public class Cliente {
  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  private Long id;

  @Column(nullable = false)
  private String nome;
}

### 🔗 Relacionamentos com JPA:

| Tipo de relacionamento | Anotação                             |
|------------------------|--------------------------------------|
| Um-para-Muitos         | `@OneToMany(mappedBy = "...")`       |
| Muitos-para-Um         | `@ManyToOne`                         |
| Muitos-para-Muitos     | `@ManyToMany`                        |

```java
@Entity
public class Pedido {
  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  private Long id;

  @ManyToOne
  private Cliente cliente;
}

### 📦 Repositórios com Spring Data JPA:

Ao usar `JpaRepository`, temos acesso a vários métodos prontos, sem precisar escrever SQL manualmente.

```java
@Repository
public interface ClienteRepository extends JpaRepository<Cliente, Long> {
    List<Cliente> findByNomeContaining(String nome);
}

#### 🔍 Métodos comuns disponíveis:

- `findAll()` – busca todos os registros.
- `findById(Long id)` – busca um registro pelo ID.
- `save(T entity)` – salva ou atualiza um registro.
- `deleteById(Long id)` – remove um registro pelo ID.

---

#### 🎯 Consultas personalizadas:

Você pode personalizar suas consultas de três formas:

1. **Por convenção de nome**  
   O Spring interpreta o nome do método e gera a query automaticamente:

   ```java
   List<Cliente> findByNome(String nome);
   List<Cliente> findByEmailContaining(String email);

   2. **Com `@Query` (JPQL ou SQL)**  
   Ideal quando a convenção de nome não é suficiente:

   ```java
   @Query("SELECT c FROM Cliente c WHERE c.nome = :nome")
   List<Cliente> buscarPorNome(@Param("nome") String nome);

   3. **Query nativa (`nativeQuery = true`)**  
   Quando você quer usar SQL direto:

   ```java
   @Query(value = "SELECT * FROM cliente WHERE nome = :nome", nativeQuery = true)
   List<Cliente> buscarPorNomeSQL(@Param("nome") String nome);

   ### 🧠 Boas práticas com Spring + Banco:

- 🔄 Use **DTOs** para trafegar dados entre camadas e evitar expor entidades diretamente.
- 💡 Marque métodos com `@Transactional` quando houver múltiplas operações de escrita.
- 🧱 Evite misturar lógica de negócio dentro da camada de repositório.
- 🧼 Mantenha cada camada com responsabilidade única:  
  - **Controller** → recebe e responde requisições  
  - **Service** → executa regras de negócio  
  - **Repository** → acessa e manipula dados no banco