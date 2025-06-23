
# Resumo de Estudo JAVA

## 🧠 POO – Programação Orientada a Objetos (4 pilares)

### 1. Herança
Reuso de código. Uma classe herda atributos e métodos de outra.  
Ex: `class Cachorro extends Animal {}`

### 2. Polimorfismo
Um mesmo método pode ter comportamentos diferentes.
- **Sobrescrita (Override)**: método com mesma assinatura, mas implementação diferente em uma subclasse.
- **Sobrecarga (Overload)**: método com mesmo nome, mas parâmetros diferentes.

### 3. Abstração
Esconde os detalhes da implementação e expõe só o necessário.  
Usada com **interfaces** e **classes abstratas**.

### 4. Encapsulamento
Protege dados com `private`, acessando via `getters` e `setters`.  
Permite controle e validação de dados.

---

## 🔹 Exceções (Exception Handling)

- Situações anormais que podem causar falhas no sistema.
- **Unchecked (Runtime)**: `NullPointerException`, `ArithmeticException`.
- **Checked (Obrigam try/catch)**: `IOException`, `SQLException`.
- Tratadas com `try-catch-finally`, evitando que o programa quebre.

```java
try {
   // código que pode gerar exceção
} catch (Exception e) {
   // tratamento
} finally {
   // sempre executa
}
```

- Também é possível criar exceções personalizadas com `extends RuntimeException`.

---

## 🔹 Collections (Java Collections Framework)

Estruturas de dados prontas para uso:
- `List` (ex: `ArrayList`) → permite repetição e mantém ordem.
- `Set` (ex: `HashSet`) → não permite valores duplicados.
- `Map` (ex: `HashMap`) → estrutura chave/valor.

```java
List<String> nomes = new ArrayList<>();
Set<String> nomesUnicos = new HashSet<>(nomes);
```

---

## 🔹 Streams API (Java 8+)

Permite processar coleções de forma funcional e declarativa.

### Operações comuns:
- `filter()` – filtra elementos com base em condição
- `map()` – transforma dados
- `collect()` – junta os resultados (em `List`, `Set`, etc.)
- `forEach()` – percorre a stream
- `reduce()` – acumula valores

```java
nomes.stream()
     .filter(n -> n.startsWith("J"))
     .map(String::toUpperCase)
     .forEach(System.out::println);
```

---