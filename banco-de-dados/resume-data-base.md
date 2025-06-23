## 🔹 Banco de Dados (Relacional e Não-Relacional)

### 🧱 O que é um banco de dados?

Um banco de dados é um sistema que permite **armazenar, organizar e recuperar informações**. É a base de qualquer aplicação que precisa guardar dados de forma estruturada, como usuários, produtos, pedidos, etc.

Existem dois grandes tipos de bancos de dados:

---

### 🟦 Bancos de Dados Relacionais (SQL)

Os bancos relacionais, como **MySQL**, **PostgreSQL** e **Oracle**, armazenam os dados em **tabelas** com linhas e colunas — semelhante a uma planilha.

Esses bancos seguem o modelo **relacional**, onde os dados estão interligados por **chaves primárias e estrangeiras**, o que permite **relacionar diferentes entidades** (ex: um cliente tem vários pedidos).

#### ✅ Comandos SQL básicos:

| Comando        | Função                             |
|----------------|------------------------------------|
| `CREATE TABLE` | Criação de uma nova tabela         |
| `INSERT INTO`  | Inserção de novos dados            |
| `SELECT`       | Consulta de dados                  |
| `UPDATE`       | Atualização de dados existentes    |
| `DELETE`       | Exclusão de dados                  |

---

#### 🔑 Conceitos importantes:

- **Primary Key**: identifica de forma única um registro da tabela.
- **Foreign Key**: cria um vínculo com a chave primária de outra tabela (relacionamento).
- **JOIN**: permite fazer consultas entre tabelas relacionadas.

Exemplo com `INNER JOIN`:

```sql
SELECT pedidos.id, clientes.nome
FROM pedidos
INNER JOIN clientes ON pedidos.cliente_id = clientes.id;

---
#### 🔗 Relacionamentos comuns:

| Tipo               | Exemplo prático                        |
|--------------------|----------------------------------------|
| Um-para-Muitos     | Um cliente tem vários pedidos          |
| Muitos-para-Um     | Muitos pedidos pertencem a um cliente  |
| Muitos-para-Muitos | Um aluno pode ter vários cursos, e vice-versa |

---

#### 🧠 Boas práticas com SQL:

- **Normalização**: divide os dados em tabelas para evitar redundância.
- **Índices**: melhoram a performance de buscas (`WHERE`, `JOIN`, `ORDER BY`).
- Sempre defina **chaves primárias e estrangeiras** corretamente.

---

### 🟨 Bancos de Dados Não-Relacionais (NoSQL)

Bancos **NoSQL** como **MongoDB**, **Cassandra**, **Redis** e **Firebase** trabalham de forma diferente: **não usam tabelas**.

Cada banco NoSQL tem seu próprio modelo de estrutura, por exemplo:

- **MongoDB**: documentos JSON (chave:valor)
- **Redis**: estrutura de chave e valor simples
- **Cassandra**: colunas distribuídas
- **Firebase**: árvore de dados (parecido com JSON)

Esses bancos são muito usados em sistemas que precisam de:

- Alta escalabilidade  
- Flexibilidade de estrutura  
- Menor complexidade de relações

> ⚠️ No contexto Spring Boot e Java, o mais comum é usar **banco relacional** com JPA/Hibernate.

---

