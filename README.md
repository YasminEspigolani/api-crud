# CRUD de Usuários - API REST com Node.js 👤

Uma aplicação web completa para cadastro de usuários, com back-end em Node.js e Express, banco de dados MySQL e uma interface simples em HTML e JavaScript puro. O projeto implementa as quatro operações fundamentais de um CRUD (criar, ler, atualizar e excluir) por meio de uma API REST, e o front-end consome essa API com `fetch`.

## 🚀 Funcionalidades e Modelagem

O sistema é dividido em três camadas:

**Banco de dados (MySQL):**
- Banco `user_yas` com a tabela `users`, composta por `id` (chave primária com auto incremento), `nome` e `email`.
- Script com 10 usuários de exemplo para testar a aplicação logo de início.

**Back-end (Node.js + Express):**
- **`server.js`:** Inicia o servidor na porta 3000, serve os arquivos estáticos da pasta `public` e registra as rotas da API.
- **`db.js`:** Conexão com o MySQL usando `mysql2`, com as credenciais lidas de variáveis de ambiente (`dotenv`).
- **`scripts/api.js`:** Rotas da API, organizadas com `express.Router`.

**Front-end (HTML + JavaScript):**
- Formulário para cadastrar um novo usuário.
- Lista dos usuários cadastrados, com botões para **editar** (por meio de `prompt`) e **excluir** (com confirmação).
- A lista é atualizada automaticamente após cada operação.

## 🔌 Endpoints da API

| Método | Rota             | Descrição                          | Retorno                  |
| ------ | ---------------- | ---------------------------------- | ------------------------ |
| POST   | `/api/users/`    | Cadastra um usuário (`nome`, `email`) | `201` com o usuário criado |
| GET    | `/api/users/`    | Lista todos os usuários            | `200` com a lista em JSON  |
| PUT    | `/api/users/:id` | Atualiza nome e email de um usuário | `200` com os dados atualizados |
| DELETE | `/api/users/:id` | Remove um usuário                  | `204` sem conteúdo         |

Exemplo de corpo para cadastro ou edição:
```json
{
  "nome": "Ana Silva",
  "email": "ana.silva@exemplo.com"
}
```

## 🛠️ Tecnologias Utilizadas

- **Node.js**: Ambiente de execução do back-end.
- **Express 5**: Framework para criação da API e servidor de arquivos estáticos.
- **MySQL e mysql2**: Banco de dados relacional e driver de conexão.
- **dotenv**: Gerenciamento das credenciais por variáveis de ambiente.
- **HTML5, CSS3 e JavaScript**: Interface e consumo da API com `fetch`.

## 📁 Estrutura do Projeto

```
API_TESTE_SOFTWARE/
├── public/
│   ├── index.html     # Página com formulário e lista de usuários
│   ├── app.js         # Lógica do front-end e chamadas à API
│   └── style.css      # Estilos da página
├── scripts/
│   └── api.js         # Rotas do CRUD
├── db.js              # Conexão com o banco de dados
├── server.js          # Servidor Express
├── user_yas.sql       # Criação do banco, da tabela e dados de exemplo
├── package.json       # Dependências do projeto
└── .gitignore         # Ignora node_modules e arquivos .env
```

## ▶️ Como executar

**Pré-requisitos:** Node.js (versão 18 ou superior) e MySQL instalados.

**1. Clone este repositório:**
```bash
git clone https://github.com/SEU-USUARIO/API_TESTE_SOFTWARE.git
```

**2. Navegue até a pasta do projeto:**
```bash
cd API_TESTE_SOFTWARE
```

**3. Instale as dependências:**
```bash
npm install
```

**4. Crie o banco de dados:**
```bash
mysql -u root -p < user_yas.sql
```

**5. Crie o arquivo `.env` na raiz do projeto com as credenciais do seu MySQL:**
```env
DB_HOST=localhost
DB_USER=root
DB_PASS=sua_senha
DB_NAME=user_yas
```

**6. Inicie o servidor:**
```bash
node server.js
```

**7. Acesse no navegador:**
```
http://localhost:3000
```
