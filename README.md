<div align="center">

# 🐾 Pet Mania API

**Uma API para ajudar bichinhos a encontrarem um lar, e para eu aprender a caçar bugs no caminho.**

![Java](https://img.shields.io/badge/Java-25-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-4.1.2-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-C71A36?style=for-the-badge&logo=apachemaven&logoColor=white)
![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)

</div>

---

## 💬 Por que este projeto existe

O **Pet Mania** nasceu como um desafio: recebi um back-end Java que *parecia* pronto, mas não rodava. Minha missão era descobrir o que estava quebrado, consertar e deixar a API funcionando de ponta a ponta, conectada a um banco MySQL e a um front-end.

Mais do que escrever código novo, este projeto foi sobre **ler código com atenção, entender cada erro e corrigir com critério**. Foi aí que eu mais aprendi.

---

## 🐛 O que eu encontrei (e consertei)

Antes de a API subir, havia uma lista bem generosa de problemas. Estes foram os principais:

| Onde | Problema | Correção |
|---|---|---|
| `PetController` | `@RequestMaping` com erro de digitação e rota passada dentro do `@RestController("api/pets")` | `@RestController` + `@RequestMapping("api/pets")` |
| `PetController` | `GET` e `POST` trocados entre os métodos | Cada anotação no método certo |
| `PetController` | `findById()` sem parâmetro para listar tudo | `findAll()` |
| `PetRepository` | Era uma `class` estendendo `CrudRepository<Pet, int>` | `interface` estendendo `JpaRepository<Pet, Integer>` |
| `Pet` | Faltavam `@Entity`, `@Id` e `@GeneratedValue`; sem construtor vazio | Entidade JPA completa, com ID autoincrementado |
| `Pet` | Tipo `ballena` no lugar de `boolean` | Tipos corrigidos |
| `Pet` | `setNome(int)` e `getIdade()` retornando `String` | `String` e `int` nos lugares certos |
| Enums | `fêmea` em minúsculo, fora do padrão | `Fêmea` |
| `pom.xml` | Starter genérico e sem JPA/Web MVC | Dependências corretas de JPA, Web MVC e testes |
| Configuração | Sem conexão com o banco | `application.properties` com MySQL e Hibernate |

---

## 🚀 O que a API faz

- ✅ Cadastra animais
- ✅ Lista todos os animais
- ✅ Busca um animal pelo ID
- ✅ Atualiza as informações de um animal
- ✅ Exclui um animal
- ✅ Persiste tudo em MySQL
- ✅ Conversa com o front-end do Pet Mania

---

## 🛠️ Stack

| Tecnologia | Papel no projeto |
|---|---|
| ☕ **Java 25** | Linguagem |
| 🍃 **Spring Boot 4.1.2** | Framework da API |
| 🗃️ **Spring Data JPA** | Persistência e acesso aos dados |
| 🐬 **MySQL** | Banco relacional |
| 📦 **Maven** | Gerenciamento de dependências |
| 📮 **Postman** | Validação dos endpoints |
| 🎨 **HTML, CSS e JavaScript** | Interface front-end |

---

## 📂 Estrutura

```text
Pet-mania-API/
├── src/
│   ├── main/
│   │   ├── java/com/dt2/petmania/
│   │   │   ├── controllers/
│   │   │   │   └── PetController.java
│   │   │   ├── entities/
│   │   │   │   ├── enums/          # Porte e Sexo
│   │   │   │   └── Pet.java
│   │   │   ├── repositories/
│   │   │   │   └── PetRepository.java
│   │   │   └── PetManiaApplication.java
│   │   └── resources/
│   │       ├── static/
│   │       │   └── index.html      # Front-end
│   │       └── application.properties
│   └── test/
├── pom.xml
└── README.md
```

---

## 🐶 Sobre os animais

| Campo | Descrição |
|---|---|
| `id` | Identificador do animal |
| `nome` | Como ele se chama |
| `especie` | Cachorro, gato... |
| `raca` | Raça |
| `idade` | Idade em anos |
| `sexo` | `Macho` ou `Fêmea` |
| `porte` | `Pequeno`, `Médio` ou `Grande` |
| `personalidade` | O jeitinho dele |
| `foto` | URL da imagem |
| `disponivel` | Se está disponível para adoção |

---

## 🔗 Endpoints

Base: `http://localhost:8080/api/pets`

| Método | Endpoint | O que faz |
|---|---|---|
| `GET` | `/api/pets` | Lista todos os animais |
| `GET` | `/api/pets/{id}` | Busca um animal pelo ID |
| `POST` | `/api/pets` | Cadastra um novo animal |
| `PUT` | `/api/pets/{id}` | Atualiza um animal |
| `DELETE` | `/api/pets/{id}` | Exclui um animal |

**Exemplo de corpo para cadastro:**

```json
{
  "nome": "Thor",
  "especie": "Cachorro",
  "raca": "Golden Retriever",
  "idade": 3,
  "sexo": "Macho",
  "porte": "Grande",
  "personalidade": "Brincalhão e carinhoso",
  "foto": "https://exemplo.com/thor.jpg",
  "disponivel": true
}
```

---

## ⚙️ Rodando na sua máquina

### Você vai precisar de

- Java JDK 25
- MySQL
- Git
- Uma IDE, como o IntelliJ IDEA

### Passo a passo

**1. Clone o repositório**

```bash
git clone https://github.com/SEU-USUARIO/Pet-mania-API.git
cd Pet-mania-API
```

**2. Crie o banco**

```sql
CREATE DATABASE Pet_Mania;
```

**3. Configure o `application.properties`** com as suas credenciais:

```properties
spring.application.name=petMania

spring.datasource.url=jdbc:mysql://localhost:3306/Pet_Mania
spring.datasource.username=SEU_USUARIO
spring.datasource.password=SUA_SENHA

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
```

**4. Execute a aplicação**

Abra o projeto na IDE e rode a classe `PetManiaApplication.java`.

A API sobe em **http://localhost:8080** e o front-end abre no mesmo endereço, já que está na pasta `static`.

---

## 🧪 Testes com Postman

Testei cada operação (consulta, cadastro, atualização e exclusão) no Postman antes de dar o trabalho como pronto.

**GET: listar animais**

![GET - Listar animais](./docs/img/get-pets.png)

---

## 🖥️ O front-end

Para não depender só do Postman, o projeto tem uma interface simples para gerenciar os animais.

**Tela inicial**

![Tela inicial](./docs/img/tela-inicial.png)

**Cadastro de animal**

![Cadastro de animal](./docs/img/cadastro.png)

**Atualização de animal**

![Atualização de animal](./docs/img/atualizacao.png)

---

## 📚 O que eu levo daqui

- Depurar um projeto Java lendo o erro com calma, em vez de sair mudando tudo
- Construir uma API REST com Spring Boot do zero ao CRUD completo
- Integrar Java e MySQL com Spring Data JPA
- Validar requisições HTTP com o Postman
- Conectar back-end e front-end
- Organizar o histórico do projeto com Git e GitHub

E uma lição que ficou: **boa parte dos bugs está em detalhes pequenos**, como uma anotação no lugar errado ou um tipo trocado.

---

## 👨‍💻 Autor

Feito por **Alexandre Sartori de Araújo**.

Projeto acadêmico desenvolvido no desafio **Pet Mania**. 🐾

<div align="center">

*Se este projeto te ajudou ou te divertiu, deixa uma ⭐ no repositório!*

</div>
