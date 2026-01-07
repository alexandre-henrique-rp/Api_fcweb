# API FCWeb

<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo-small.svg" width="200" alt="Nest Logo" /></a>
</p>

[circleci-image]: https://img.shields.io/circleci/build/github/nestjs/nest/master?token=abc123def456
[circleci-url]: https://circleci.com/gh/nestjs/nest

  <p align="center">A progressive <a href="http://nodejs.org" target="_blank">Node.js</a> framework for building efficient and scalable server-side applications.</p>
    <p align="center">
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/v/@nestjs/core.svg" alt="NPM Version" /></a>
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/l/@nestjs/core.svg" alt="Package License" /></a>
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/dm/@nestjs/common.svg" alt="NPM Downloads" /></a>
<a href="https://circleci.com/gh/nestjs/nest" target="_blank"><img src="https://img.shields.io/circleci/build/github/nestjs/nest/master" alt="CircleCI" /></a>
<a href="https://coveralls.io/github/nestjs/nest?branch=master" target="_blank"><img src="https://coveralls.io/repos/github/nestjs/nest/badge.svg?branch=master#9" alt="Coverage" /></a>
<a href="https://discord.gg/G7Qnnhy" target="_blank"><img src="https://img.shields.io/badge/discord-online-brightgreen.svg" alt="Discord"/></a>
<a href="https://opencollective.com/nest#backer" target="_blank"><img src="https://img.shields.io/npm/l/@nestjs/core.svg" alt="Backers on Open Collective" /></a>

## 📋 Descrição do Projeto

A **API FCWeb** é uma aplicação backend construída com **NestJS** que oferece serviços completos para gestão de certificados digitais e processos administrativos. A API é projetada para automatizar e gerenciar o ciclo de vida de certificados, desde a solicitação inicial até a aprovação final, incluindo gestão de clientes, agentes e agendamentos.

### 🎯 Funcionalidades Principais

- **📋 Gestão de FCWeb**: Controle completo de processos de certificação
- **👥 Gestão de AGRV**: Administração de agentes de registro externo
- **📅 Sistema de Agendamentos**: Agendamento de serviços e consultas
- **🔐 Autenticação Segura**: Basic Auth para controle de acesso
- **📊 Importação de Dados**: Bulk import de informações
- **📄 Documentação Automática**: Swagger/OpenAPI integrado
- **🗄️ Banco MySQL**: Persistência robusta com Prisma ORM

## 🏗️ Arquitetura do Projeto

### Estrutura de Diretórios

```
backend/Api_fcweb/
├── src/
│   ├── app.module.ts             # Módulo raiz da aplicação
│   ├── main.ts                   # Ponto de entrada e configuração
│   ├── api/                      # Módulos da API
│   │   ├── fcweb/               # Módulo FCWeb (certificados)
│   │   │   ├── fcweb.controller.ts  # Controlador FCWeb
│   │   │   ├── fcweb.service.ts     # Serviço FCWeb
│   │   │   ├── fcweb.module.ts      # Módulo FCWeb
│   │   │   ├── dto/                 # DTOs FCWeb
│   │   │   └── entities/            # Entidades FCWeb
│   │   └── agrv/               # Módulo AGRV (agentes)
│   │       ├── agrv.controller.ts  # Controlador AGRV
│   │       ├── agrv.service.ts     # Serviço AGRV
│   │       ├── agrv.module.ts      # Módulo AGRV
│   │       ├── dto/                 # DTOs AGRV
│   │       └── entities/            # Entidades AGRV
│   ├── auth/                     # Módulo de autenticação
│   │   ├── auth.guard.ts         # Guard de Basic Auth
│   │   └── auth.module.ts        # Módulo de auth
│   └── prisma/                   # Configuração do Prisma
│       ├── prisma.service.ts     # Serviço do Prisma
│       └── prisma.filter.ts      # Filtro de exceções
├── prisma/
│   └── schema.prisma             # Schema do banco de dados
├── test/                         # Testes
├── .env                          # Variáveis de ambiente
├── Dockerfile                    # Configuração Docker
└── README.md                     # Documentação
```

## 🔧 Tecnologias Utilizadas

### Backend Framework
- **NestJS**: Framework TypeScript para construção de APIs robustas
- **TypeScript**: Superset tipado do JavaScript

### Banco de Dados
- **Prisma ORM**: ORM moderno e type-safe
- **MySQL**: Banco de dados relacional

### Documentação e Validação
- **Swagger/OpenAPI**: Documentação automática da API
- **Class Validator**: Validação de DTOs
- **Class Transformer**: Transformação de dados

### Desenvolvimento e Deploy
- **Docker**: Containerização
- **Jest**: Framework de testes
- **ESLint/Prettier**: Qualidade de código

## 🗄️ Modelo de Dados

### Entidades Principais

#### **fcweb**
Registro principal de processos de certificação:
```typescript
interface fcweb {
  id: number;                    // ID único
  referencia: string;            // Referência do processo
  unidade: string;               // Unidade de atendimento
  responsavel: string;           // Responsável pelo processo
  criou_fc: string;              // Quem criou o FC
  andamento: string;             // Status do andamento
  prioridade: string;            // Nível de prioridade
  solicitacao: string;           // Tipo de solicitação
  venda: string;                 // Tipo de venda
  cpf: string;                   // CPF do cliente
  cnpj: string;                  // CNPJ do cliente
  nome: string;                  // Nome do cliente
  razaosocial: string;            // Razão social
  vectoboleto: Date;             // Vencimento do boleto
  tipocd: string;                // Tipo de certificado
  valorcd: string;               // Valor do certificado
  estatos_pgto: string;          // Status do pagamento
  formapgto: string;             // Forma de pagamento
  telefone: string;              // Telefone
  email: string;                 // Email
  endereco: string;              // Endereço
  cidade: string;                // Cidade
  uf: string;                    // Estado
  observacao: string;            // Observações
  createdAt: Date;               // Data de criação
  updatedAt: Date;               // Data de atualização
}
```

#### **AGRV**
Agentes de registro externo:
```typescript
interface AGRV {
  idagrv: number;                // ID único
  nome: string;                  // Nome do agente
  cpf: string;                   // CPF
  nascimento: Date;              // Data de nascimento
  rg: string;                    // RG
  linkcnh: string;               // Link da CNH
  linkfotoperfil: string;        // Link da foto
  logradouro: string;            // Endereço
  numero: string;                // Número
  complemento: string;           // Complemento
  cep: string;                   // CEP
  municipio: string;             // Município
  uf: string;                    // Estado
  whatsapp: string;              // WhatsApp
  celular: string;               // Celular
  email: string;                 // Email
  chavepix: string;              // Chave PIX
  nomebanco: string;             // Nome do banco
  numeroconta: string;           // Número da conta
  tipocontabanco: string;        // Tipo de conta
  nomepolo: string;              // Nome do polo
  numeropolo: number;            // Número do polo
  createdAt: Date;               // Data de criação
  updatedAt: Date;               // Data de atualização
}
```

#### **agendamentos**
Sistema de agendamentos:
```typescript
interface agendamentos {
  id: number;                    // ID único
  id_fcweb: number;              // ID do FCWeb relacionado
  data_agendada: Date;           // Data agendada
  hora_agendada: Date;           // Hora agendada
  modalidade: string;            // Modalidade do agendamento
  agente_id: number;             // ID do agente
  criado_em: Date;               // Data de criação
}
```

#### **leads**
Gestão de leads:
```typescript
interface leads {
  id: number;                    // ID único
  nome: string;                  // Nome do lead
  telefone_1: string;            // Telefone principal
  email: string;                 // Email
  cpf: string;                   // CPF
  cnpj: string;                  // CNPJ
  data_nascimento: string;       // Data de nascimento
  razao_social: string;          // Razão social
  tipo_lead: string;             // Tipo de lead
  certificado: string;           // Certificado desejado
  valor: number;                 // Valor
  cupom_desconto: string;        // Cupom de desconto
  criado_em: Date;               // Data de criação
  atualizado_em: Date;           // Data de atualização
}
```

## 🔄 Fluxo de Processamento

### 1. Criação de Processo FCWeb
```mermaid
sequenceDiagram
    participant Client as Cliente
    participant API as API FCWeb
    participant DB as Banco MySQL
    
    Client->>API: POST /fcweb (dados do certificado)
    API->>API: Validar autenticação Basic Auth
    API->>API: Validar dados do DTO
    API->>DB: Criar registro fcweb
    DB-->>API: Retornar registro criado
    API-->>Client: Retornar FCWeb com ID
```

### 2. Gestão de Agentes AGRV
```mermaid
sequenceDiagram
    participant Admin as Administrador
    participant API as API FCWeb
    participant DB as Banco MySQL
    
    Admin->>API: POST /agrv (dados do agente)
    API->>API: Validar autenticação
    API->>DB: Criar registro AGRV
    DB-->>API: Retornar agente criado
    API-->>Admin: Confirmação com ID
```

### 3. Sistema de Agendamentos
```mermaid
sequenceDiagram
    participant Agent as Agente
    participant API as API FCWeb
    participant DB as Banco MySQL
    
    Agent->>API: POST /agendamentos (dados do agendamento)
    API->>API: Validar disponibilidade
    API->>DB: Criar agendamento
    API->>DB: Atualizar FCWeb relacionado
    DB-->>API: Confirmação
    API-->>Agent: Agendamento confirmado
```

## 🚀 Endpoints da API

### Autenticação
Todos os endpoints requerem **Basic Auth**:
- **Header**: `Authorization: Basic base64(usuario:senha)`
- **Variáveis**: `USERAPI` e `PASSAPI` no `.env`

### FCWeb - Gestão de Certificados
- **POST /fcweb** - Criar novo processo
- **GET /fcweb** - Listar todos os processos (limit: 300)
- **GET /fcweb/:id** - Obter processo por ID
- **PATCH /fcweb/:id** - Atualizar processo
- **DELETE /fcweb/:id** - Deletar processo
- **POST /fcweb/import** - Importar dados em lote

### AGRV - Gestão de Agentes
- **POST /agrv** - Criar novo agente
- **GET /agrv** - Listar todos os agentes
- **GET /agrv/:id** - Obter agente por ID
- **PATCH /agrv/:id** - Atualizar agente
- **DELETE /agrv/:id** - Deletar agente

### Agendamentos
- **POST /agendamentos** - Criar agendamento
- **GET /agendamentos** - Listar agendamentos
- **GET /agendamentos/:id** - Obter agendamento por ID
- **PATCH /agendamentos/:id** - Atualizar agendamento
- **DELETE /agendamentos/:id** - Cancelar agendamento

### Leads
- **POST /leads** - Criar novo lead
- **GET /leads** - Listar leads
- **GET /leads/:id** - Obter lead por ID
- **PATCH /leads/:id** - Atualizar lead
- **DELETE /leads/:id** - Deletar lead

## 🔐 Segurança

### Autenticação Basic Auth
- Todas as requisições precisam incluir header `Authorization`
- Formato: `Basic base64(usuario:senha)`
- Validação contra variáveis de ambiente
- Exemplo: `Authorization: Basic dXN1YXJpbzpzZW5oYQ==`

### Validação de Dados
- DTOs com validação automática
- Class Validator para regras de negócio
- Sanitização de entrada de dados
- Tratamento de exceções global

### CORS Configurado
- Origin: `*` (configurável por ambiente)
- Methods: GET, HEAD, PUT, PATCH, POST, DELETE
- Headers: Content-Type, Accept, Authorization
- Credentials: true

## 📊 Documentação Swagger

### Acesso à Documentação
- **Produção**: https://apifcweb.redebrasilrp.com.br/api-docs
- **Desenvolvimento**: http://localhost:3000/api-docs

### Funcionalidades do Swagger
- **Interface Interativa**: Teste endpoints diretamente
- **Autenticação Integrada**: Botão "Authorize" para Basic Auth
- **Documentação Automática**: Geração baseada nos decorators
- **Exemplos de Requisição**: Body formatados
- **Respostas Esperadas**: Status codes e schemas

### Configuração do Swagger
```typescript
const config = new DocumentBuilder()
  .setTitle('API FCWeb')
  .setDescription('Documentação da API FCWeb')
  .setVersion('1.0')
  .addServer('https://apifcweb.redebrasilrp.com.br', 'Produção')
  .addBasicAuth()
  .build();
```

## 🛠️ Configuração e Instalação

### Pré-requisitos
- Node.js 18+
- MySQL 8.0+
- npm ou yarn

### Instalação
```bash
# Clonar repositório
git clone <repositorio>
cd Api_fcweb

# Instalar dependências
npm install

# Configurar variáveis de ambiente
cp .env.example .env
# Editar .env com suas configurações

# Rodar migrações do Prisma
npx prisma migrate deploy

# Gerar cliente Prisma
npx prisma generate

# Iniciar em desenvolvimento
npm run start:dev
```

### Scripts Disponíveis
```bash
# Desenvolvimento
npm run start:dev          # Iniciar com watch
npm run start:debug        # Iniciar com debug

# Produção
npm run build             # Compilar TypeScript
npm run start:prod        # Iniciar produção

# Testes
npm run test              # Rodar testes
npm run test:cov          # Testes com coverage
npm run test:e2e          # Testes E2E

# Banco de Dados
npm run prisma:studio     # Abrir Prisma Studio
npm run prisma:generate   # Gerar cliente
npm run prisma:migrate    # Rodar migrações

# Qualidade
npm run lint              # Lint do código
npm run format            # Formatar código
```

## 📝 Variáveis de Ambiente

```env
# Database
DATABASE_URL="mysql://user:password@localhost:3306/database"

# API
PORT=3000
NODE_ENV=development

# Autenticação
USERAPI=seu_usuario
PASSAPI=sua_senha

# Outras configurações
# (adicionar conforme necessário)
```

## 🐳 Docker

### Dockerfile
```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production
COPY . .
RUN npm run build
EXPOSE 3000
CMD ["npm", "run", "start:prod"]
```

### Build e Run
```bash
# Build da imagem
docker build -t api-fcweb .

# Rodar container
docker run -p 3000:3000 --env-file .env api-fcweb
```

## 📈 Performance

### Otimizações
- **Connection Pooling**: Prisma com pool de conexões
- **Queries Otimizadas**: Índices no banco de dados
- **Lazy Loading**: Carregamento sob demanda
- **Caching**: Implementar Redis se necessário

### Métricas de Performance
- **Response Time**: < 200ms para queries simples
- **Database Queries**: < 100ms com índices
- **Memory Usage**: < 512MB em produção
- **Concurrent Requests**: Suporte a múltiplas requisições

## 🧪 Testes

### Estrutura de Testes
- **Unitários**: Testes de serviços e controllers
- **Integração**: Testes de endpoints completos
- **E2E**: Testes de fluxo completo

### Exemplo de Teste
```bash
# Rodar todos os testes
npm run test

# Testes com coverage
npm run test:cov

# Testes E2E
npm run test:e2e
```

## 🔧 Monitoramento e Logs

### Estrutura de Logs
- **Console**: Logs de desenvolvimento
- **Prisma Filter**: Tratamento de exceções do banco
- **Error Handling**: Tratamento centralizado de erros

### Métricas Importantes
- Volume de requisições por endpoint
- Tempo médio de resposta
- Taxa de erro por endpoint
- Performance do banco de dados

## 🚀 Deploy

### Produção
```bash
# Compilar aplicação
npm run build

# Iniciar com PM2
pm2 start ecosystem.config.json

# Ou com Docker
docker build -t api-fcweb .
docker run -p 3000:3000 --env-file .env.prod api-fcweb
```

### Variáveis de Produção
- `NODE_ENV=production`
- `PORT=3000`
- Configurar SSL/HTTPS
- Monitoramento de saúde
- Backup do banco de dados

## 🔮 Roadmap Futuro

### Próximas Funcionalidades
- [ ] **Webhooks**: Notificações em tempo real
- [ ] **Dashboard Analytics**: Métricas e gráficos
- [ ] **Multi-tenant**: Suporte a múltiplos clientes
- [ ] **OAuth2**: Autenticação avançada
- [ ] **Rate Limiting**: Controle de requisições
- [ ] **Cache Redis**: Performance otimizada

### Melhorias Técnicas
- [ ] **Microservices**: Separação em serviços independentes
- [ ] **Queue System**: Processamento assíncrono
- [ ] **Load Balancer**: Balanceamento de carga
- [ ] **Monitoring**: Prometheus + Grafana
- [ ] **CI/CD**: GitHub Actions

## 🤝 Contribuição

### Como Contribuir
1. Fork do projeto
2. Feature branch: `git checkout -b feature/nova-funcionalidade`
3. Commit: `git commit -m 'Add nova funcionalidade'`
4. Push: `git push origin feature/nova-funcionalidade`
5. Pull Request

### Padrões de Código
- Seguir ESLint e Prettier
- Escrever testes para novas funcionalidades
- Documentar APIs com Swagger
- Seguir convenções do NestJS

## 📄 Licença

Este projeto é privado e não licenciado para uso comercial sem autorização.

## 📞 Suporte

- **Email**: suporte@fcweb.com
- **Documentação**: https://apifcweb.redebrasilrp.com.br/api-docs
- **Issues**: [Link para issues do GitHub]

---

**API FCWeb** - Transformando gestão de certificados digitais em soluções de negócio 🚀
<a href="https://opencollective.com/nest#sponsor" target="_blank"><img src="https://opencollective.com/nest/sponsors/badge.svg" alt="Sponsors on Open Collective" /></a>
  <a href="https://paypal.me/kamilmysliwiec" target="_blank"><img src="https://img.shields.io/badge/Donate-PayPal-ff3f59.svg"/></a>
    <a href="https://opencollective.com/nest#sponsor"  target="_blank"><img src="https://img.shields.io/badge/Support%20us-Open%20Collective-41B883.svg" alt="Support us"></a>
  <a href="https://twitter.com/nestframework" target="_blank"><img src="https://img.shields.io/twitter/follow/nestframework.svg?style=social&label=Follow"></a>
</p>
  <!--[![Backers on Open Collective](https://opencollective.com/nest/backers/badge.svg)](https://opencollective.com/nest#backer)
  [![Sponsors on Open Collective](https://opencollective.com/nest/sponsors/badge.svg)](https://opencollective.com/nest#sponsor)-->

## Description

[Nest](https://github.com/nestjs/nest) framework TypeScript starter repository.

## Installation

```bash
$ yarn install
```

## Running the app

```bash
# development
$ yarn run start

# watch mode
$ yarn run start:dev

# production mode
$ yarn run start:prod
```

## Test

```bash
# unit tests
$ yarn run test

# e2e tests
$ yarn run test:e2e

# test coverage
$ yarn run test:cov
```

## Support

Nest is an MIT-licensed open source project. It can grow thanks to the sponsors and support by the amazing backers. If you'd like to join them, please [read more here](https://docs.nestjs.com/support).

## Stay in touch

- Author - [Kamil Myśliwiec](https://kamilmysliwiec.com)
- Website - [https://nestjs.com](https://nestjs.com/)
- Twitter - [@nestframework](https://twitter.com/nestframework)

## License

Nest is [MIT licensed](LICENSE).
