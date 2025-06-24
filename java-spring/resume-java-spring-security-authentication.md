# Resumo Simplificado do Spring Security - Autenticação

## 1. AuthenticationManager  
**Gerente da autenticação**  
- Recebe os dados de login (usuário/senha)  
- Tenta autenticar chamando um ou mais `AuthenticationProvider`s  
- Se um provider autenticar, considera o usuário válido  

> *Analogia:* gerente da portaria que delega para os seguranças

---

## 2. AuthenticationProvider  
**Quem valida as credenciais**  
- Verifica se o login e senha estão corretos  
- Pode usar banco, memória, API externa, etc.  
- Retorna um objeto `Authentication` se der certo  

> *Analogia:* segurança que valida o crachá

---

## 3. CustomAuthenticationProvider  
**Seu próprio provider personalizado**  
- Implementa a validação usando seu banco de dados  
- Usado internamente pelo `AuthenticationManager`  

> *Analogia:* segurança personalizado que conhece as regras do seu sistema

---

## 4. Authentication  
**Objeto que representa o usuário autenticado**  
- Contém dados do usuário, roles, nome, etc.  
- Fica guardado no `SecurityContextHolder` durante a sessão  

> *Analogia:* crachá autenticado da pessoa logada

---

## 5. CustomAuthentication  
**Sua implementação personalizada de Authentication**  
- Carrega o objeto do usuário (`UserLogin`), roles e informações adicionais  
- Usado para informar o Spring quem está autenticado e com quais permissões  

> *Analogia:* seu crachá especial com informações extras do usuário

---

## Fluxo Resumido

```plaintext
Requisição de login (usuário + senha)
           ↓
     AuthenticationManager
           ↓
  chama → CustomAuthenticationProvider
           ↓
 Valida no banco, confere senha
           ↓
  cria → CustomAuthentication
           ↓
seta no SecurityContextHolder
           ↓
Spring sabe que o usuário está logado
           ↓
Usa as roles para permitir ou bloquear endpoints