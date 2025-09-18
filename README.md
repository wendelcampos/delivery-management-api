# 🚀 RocketLog - API de Entregas

Uma API completa para gerenciamento de entregas de encomendas, desenvolvida com Node.js, TypeScript, Express e Prisma. Este projeto foi criado para treinar os fundamentos de desenvolvimento full-stack.

## 📋 Sobre o Projeto

O RocketLog é uma API REST que permite o gerenciamento de entregas de encomendas, incluindo autenticação de usuários, controle de status das entregas e logs de atividades. O projeto implementa boas práticas de desenvolvimento como validação de dados, tratamento de erros, autenticação JWT e testes automatizados.

## 🛠️ Tecnologias Utilizadas

### Backend
- **Node.js** - Runtime JavaScript
- **TypeScript** - Superset do JavaScript com tipagem estática
- **Express** - Framework web para Node.js
- **Prisma** - ORM para banco de dados
- **PostgreSQL** - Banco de dados relacional
- **JWT** - Autenticação baseada em tokens
- **bcrypt** - Criptografia de senhas
- **Zod** - Validação de schemas

### Testes
- **Jest** - Framework de testes
- **Supertest** - Testes de integração para APIs

### Desenvolvimento
- **Docker** - Containerização do banco de dados
- **tsx** - Execução de TypeScript em desenvolvimento

## 🏗️ Arquitetura do Projeto

```
src/
├── app.ts                 # Configuração principal da aplicação
├── server.ts             # Servidor HTTP
├── env.ts                # Validação de variáveis de ambiente
├── configs/
│   └── auth.ts           # Configurações de autenticação
├── controllers/          # Controladores das rotas
│   ├── users-controller.ts
│   ├── sessions-controller.ts
│   ├── deliveries-controller.ts
│   └── delivery-logs-controller.ts
├── middlewares/          # Middlewares personalizados
│   ├── ensure-authenticated.ts
│   ├── error-handling.ts
│   └── verifyUserAuthorization.ts
├── routes/               # Definição das rotas
│   ├── index.ts
│   ├── users-routes.ts
│   ├── sessions-routes.ts
│   ├── deliveries-routes.ts
│   └── delivery-logs-routes.ts
├── database/
│   └── prisma.ts         # Cliente Prisma
├── types/
│   └── express.d.ts      # Tipagens do Express
├── utils/
│   └── AppError.ts       # Classe de erro personalizada
└── tests/                # Testes automatizados
    ├── users-controller.test.ts
    └── sessions-controller.test.ts
```

## 🗄️ Modelo de Dados

### User
- `id` - Identificador único (UUID)
- `name` - Nome do usuário
- `email` - Email único
- `password` - Senha criptografada
- `role` - Papel do usuário (customer | sale)
- `createdAt` - Data de criação
- `updatedAt` - Data de atualização

### Delivery
- `id` - Identificador único (UUID)
- `userId` - ID do usuário proprietário
- `description` - Descrição da entrega
- `status` - Status da entrega (processing | shipped | delivered)
- `createdAt` - Data de criação
- `updatedAt` - Data de atualização

### DeliveryLog
- `id` - Identificador único (UUID)
- `description` - Descrição do log
- `deliveryId` - ID da entrega relacionada
- `createdAt` - Data de criação
- `updatedAt` - Data de atualização

## 🚀 Como Executar

### Pré-requisitos
- Node.js (versão 18 ou superior)
- Docker e Docker Compose
- npm ou yarn

### 1. Clone o repositório
```bash
git clone <url-do-repositorio>
cd rocketlog
```

### 2. Instale as dependências
```bash
npm install
```

### 3. Configure as variáveis de ambiente
Crie um arquivo `.env` na raiz do projeto:
```env
DATABASE_URL="postgresql://postgres:postgres@localhost:5432/rocketlog"
JWT_SECRET="sua-chave-secreta-jwt-aqui"
```

### 4. Inicie o banco de dados
```bash
docker-compose up -d
```

### 5. Execute as migrações
```bash
npx prisma migrate dev
```

### 6. Inicie o servidor de desenvolvimento
```bash
npm run dev
```

A API estará disponível em `http://localhost:3333`

## 📚 Endpoints da API

### Autenticação
- `POST /sessions` - Login de usuário
- `POST /users` - Criação de usuário

### Entregas
- `GET /deliveries` - Listar todas as entregas
- `POST /deliveries` - Criar nova entrega
- `PUT /deliveries/:id/status` - Atualizar status da entrega

### Logs de Entrega
- `GET /delivery-logs/:deliveryId` - Listar logs de uma entrega
- `POST /delivery-logs` - Criar novo log

## 🧪 Testes

Execute os testes com:
```bash
npm run test:dev
```

## 🔧 Scripts Disponíveis

- `npm run dev` - Inicia o servidor em modo desenvolvimento
- `npm run test:dev` - Executa os testes em modo watch

## 🔐 Autenticação

A API utiliza JWT (JSON Web Tokens) para autenticação. Para acessar rotas protegidas, inclua o token no header:

```
Authorization: Bearer <seu-token-jwt>
```

## 📝 Funcionalidades Implementadas

- ✅ Criação e autenticação de usuários
- ✅ Criptografia de senhas com bcrypt
- ✅ Validação de dados com Zod
- ✅ Middleware de autenticação JWT
- ✅ CRUD de entregas
- ✅ Sistema de logs para entregas
- ✅ Controle de status das entregas
- ✅ Tratamento de erros personalizado
- ✅ Testes automatizados
- ✅ Validação de variáveis de ambiente
- ✅ Migrações de banco de dados

## 🎯 Conceitos Aplicados

Este projeto demonstra a aplicação de conceitos fundamentais de desenvolvimento full-stack:

- **Arquitetura MVC** - Separação clara entre controladores, modelos e rotas
- **Middleware Pattern** - Interceptação de requisições para autenticação e tratamento de erros
- **Dependency Injection** - Uso do Prisma como cliente de banco de dados
- **Error Handling** - Tratamento centralizado de erros
- **Data Validation** - Validação de entrada com Zod
- **Security** - Criptografia de senhas e autenticação JWT
- **Testing** - Testes unitários e de integração
- **Environment Configuration** - Configuração segura de variáveis de ambiente
- **Database Migrations** - Versionamento do esquema do banco de dados

## 👨‍💻 Autor

**Wendel Campos Aguiar**
