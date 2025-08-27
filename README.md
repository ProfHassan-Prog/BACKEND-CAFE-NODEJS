Perfeito! Aqui está o **README.md** inteiro já formatado em Markdown — só copiar e colar direto no seu repositório:

---

````markdown
# ☕ Backend Café Node.js

Este projeto é a base do **sistema de gestão de um café**, desenvolvido em **Node.js + Express + MySQL**.  
Ele implementa uma API inicial para gerenciamento de **usuários** (cadastro com verificação de email único),  
utilizando boas práticas de organização em camadas, variáveis de ambiente e controle de dependências.

---

## 📌 Primeiros Passos do Desenvolvimento

### 1. Instalação de Pré-requisitos
- **Node.js** → Ambiente de execução JavaScript no lado do servidor.
- **MySQL** → Banco de dados relacional para persistência dos dados.

### 2. Inicialização do Projeto
```bash
npm init
````

Cria o arquivo `package.json`, que armazena as configurações e dependências do projeto.

### 3. Instalação de Dependências

```bash
npm install --save express mysql dotenv cors
```

* **express** → Framework para construção do servidor HTTP e rotas.
* **mysql** → Conector do Node.js com MySQL.
* **dotenv** → Carregamento de variáveis de ambiente do arquivo `.env`.
* **cors** → Permite que aplicações frontend externas acessem a API.

### 4. Dependências de Desenvolvimento

```bash
npm install --save-dev nodemon
```

* **nodemon** → Reinicia o servidor automaticamente ao detectar mudanças nos arquivos.

### 5. Scripts no `package.json`

```json
"scripts": {
  "start": "nodemon server.js"
}
```

Permite rodar o servidor com:

```bash
npm start
```

### 6. Estrutura dos Arquivos

```
BACKEND-CAFE-NODEJS/
├── routes/
│   └── user.js          # Rotas de usuário (ex: /signup)
├── connection.js         # Conexão com banco MySQL
├── index.js              # Configuração do Express (middlewares e rotas)
├── server.js             # Inicialização do servidor
├── table.sql             # Script SQL (criação da tabela user e seed inicial)
├── .env                  # Variáveis de ambiente (não versionado)
└── package.json          # Configuração do projeto e dependências
```

---

## 📂 Explicação dos Arquivos

* **server.js** → Cria e inicia o servidor HTTP na porta definida em `.env`.
* **index.js** → Configura middlewares (`cors`, `express.json`) e registra rotas.
* **connection.js** → Configura a conexão com MySQL usando variáveis de ambiente.
* **routes/user.js** → Contém a rota `POST /user/signup`, que:

  * Verifica se o email já está cadastrado.
  * Insere novo usuário com status `false` e role `user`.
  * Retorna mensagens de sucesso ou erro.
* **table.sql** → Cria a tabela `user` e insere o primeiro usuário administrador.
* **.env** → Armazena credenciais e variáveis de ambiente (excluído do GitHub via `.gitignore`).

---

## 🗄️ Banco de Dados (MySQL)

### Estrutura inicial (`table.sql`)

```sql
create table user(
    id int primary key AUTO_INCREMENT,
    name varchar(250),
    contactNumber varchar(20),
    email varchar(50) unique,
    password varchar(250),
    status varchar(20),
    role varchar(20)
);

insert into user(name, contactNumber, email, password, status, role)
values ('Admin', '123123123', 'admin@gmail.com', 'admin', 'true', 'admin');
```

---

## 🚀 Executando o Projeto

1. Clone este repositório:

```bash
git clone https://github.com/ProfHassan-Prog/BACKEND-CAFE-NODEJS.git
```

2. Instale as dependências:

```bash
npm install
```

3. Configure o arquivo `.env`:

```env
# Server
PORT=8080

# Database
DB_PORT=3306
DB_HOST=localhost
DB_USERNAME=root
DB_PASSWORD=123456
DB_NAME=cafenodejs
```

4. Inicie o servidor:

```bash
npm start
```

5. Teste no Postman:

* **POST** → `http://localhost:8080/user/signup`
* Body (JSON):

```json
{
  "name": "João da Silva",
  "contactNumber": "11999999999",
  "email": "joao@email.com",
  "password": "123456"
}
```

---

## ✅ Status Atual

* Ambiente configurado
* Estrutura inicial concluída
* API conectada ao MySQL
* Cadastro de usuários funcionando via Postman
* **Commit inicial realizado** 🎉

---

## 📌 Próximos Passos

* Implementar login e autenticação (JWT).
* Adicionar hash de senha com **bcrypt**.
* Criar rotas de administração (aprovar usuários, gerenciar permissões).
* Expandir para produtos, pedidos e relatórios.

---

👨‍💻 Desenvolvido por [ProfHassan-Prog](https://github.com/ProfHassan-Prog)

```
