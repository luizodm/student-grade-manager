# Student Grade Manager

API simples em Node.js para gerenciar notas de estudantes em memória, utilizando o módulo nativo `http` e a biblioteca `uuid` para geração de IDs.

O projeto expõe endpoints REST para **criar, listar, atualizar e deletar** registros de notas (`grades`).

---

## 🧰 Tecnologias utilizadas

- [Node.js](https://nodejs.org/) (ES Modules)
- Módulo nativo `http`
- [uuid](https://www.npmjs.com/package/uuid)
- [Thunder Client](https://www.thunderclient.com/) (coleção de requests incluída no repositório)

---

## ⚙️ Pré-requisitos

- Node.js **>= 18** instalado na máquina
- npm (vem junto com o Node)
- Cliente HTTP (Thunder Client, Postman, Insomnia etc.) — opcional, mas recomendado

---

## 🚀 Como rodar o projeto

1. **Clonar o repositório**

   ```bash
   git clone https://github.com/luizodm/student-grade-manager.git
   cd student-grade-manager
   ```

2. **Instalar as dependências**

   ```bash
   npm install
   ```

3. **Iniciar o servidor**

   ```bash
   node index.js
   ```

   O servidor será iniciado em:

   ```text
   http://localhost:3000
   ```

> Obs.: Os dados são mantidos apenas em memória (array `grades`). Sempre que o servidor for reiniciado, a lista volta ao estado inicial.

---

## 📡 Endpoints

### 1. Listar todas as notas

**GET** `/grades`

- **Descrição:** Retorna um array com todas as notas cadastradas.
- **Exemplo de resposta:**

```json
[
  {
    "id": "c74efb0f-78d0-4d1e-9c29-1c3f9c1a9e9a",
    "studentName": "Luiz",
    "subject": "English",
    "grade": "8"
  }
]
```

---

### 2. Criar uma nova nota

**POST** `/grades`

- **Descrição:** Cria um novo registro de nota.
- **Headers:**

```text
Content-Type: application/json
```

- **Body (JSON):**

```json
{
  "studentName": "Julia",
  "subject": "English",
  "grade": "10"
}
```

- **Exemplo de resposta (201):**

```json
{
  "id": "c74efb0f-78d0-4d1e-9c29-1c3f9c1a9e9a",
  "studentName": "Julia",
  "subject": "English",
  "grade": "10"
}
```

---

### 3. Atualizar uma nota existente

**PUT** `/grades/:id`

- **Descrição:** Atualiza um registro de nota pelo `id`.
- **Parâmetros de rota:**
  - `id` – ID da nota a ser atualizada
- **Headers:**

```text
Content-Type: application/json
```

- **Body (JSON):**

```json
{
  "studentName": "Thiago Lima",
  "subject": "English",
  "grade": "8"
}
```

- **Exemplo de requisição:**

```text
PUT http://localhost:3000/grades/c74efb0f-78d0-4d1e-9c29-1c3f9c1a9e9a
```

- **Respostas possíveis:**

  - `200 OK` – Retorna o objeto atualizado
  - `404 Not Found` – Quando a nota não é encontrada

```json
{
  "message": "Grade not found"
}
```

---

### 4. Deletar uma nota

**DELETE** `/grades/:id`

- **Descrição:** Remove uma nota pelo `id`.
- **Parâmetros de rota:**
  - `id` – ID da nota a ser removida
- **Exemplo de requisição:**

```text
DELETE http://localhost:3000/grades/c74efb0f-78d0-4d1e-9c29-1c3f9c1a9e9a
```

- **Respostas possíveis:**

  - `204 No Content` – Quando a nota é removida com sucesso
  - `404 Not Found` – Quando a nota não é encontrada

```json
{
  "message": "Grade not found"
}
```

---

## 🧪 Coleção Thunder Client

O arquivo `thunder-collection_student_grade_manager.json` contém uma coleção de requisições pronta para uso no **Thunder Client** (extensão do VS Code).

### Como importar:

1. Abra o VS Code.
2. Vá na aba **Thunder Client**.
3. Clique em **Collections**.
4. Use a opção **Import**.
5. Selecione o arquivo:

   ```text
   thunder-collection_student_grade_manager.json
   ```

Isso vai criar automaticamente as requisições:

- `GET http://localhost:3000/grades`
- `POST http://localhost:3000/grades`
- `PUT http://localhost:3000/grades/:id`
- `DELETE http://localhost:3000/grades/:id`

---

## 📂 Estrutura do projeto

```text
student-grade-manager/
├── index.js                               # Servidor HTTP e rotas
├── package.json                           # Configuração do projeto Node
├── package-lock.json                      # Lockfile do npm
├── .gitignore                             # Arquivos/dirs ignorados pelo Git
└── thunder-collection_student_grade_manager.json  # Coleção Thunder Client
```

---

## 📌 Observações

- O projeto usa `"type": "module"` no `package.json`, por isso os imports utilizam a sintaxe ES Modules: `import ... from`.
- As notas são armazenadas em um array em memória (`const grades = [];`). Não há persistência em banco de dados.

---

## 📄 Licença

Este projeto está licenciado sob a licença **ISC**.
