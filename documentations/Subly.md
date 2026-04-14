# Subly - SaaS de Gerenciamento de Assinaturas

[![Laravel 13](https://img.shields.io/badge/Laravel-13.0-FF2D20?style=flat-square&logo=laravel)](https://laravel.com)
[![PHP 8.3+](https://img.shields.io/badge/PHP-8.3%2B-777BB4?style=flat-square&logo=php)](https://www.php.net)
[![MySQL 8.0](https://img.shields.io/badge/MySQL-8.0-4479A1?style=flat-square&logo=mysql)](https://www.mysql.com)
[![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?style=flat-square&logo=docker)](https://www.docker.com)
[![License MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Subly é uma plataforma SaaS moderna para gerenciamento de assinaturas com integração nativa do Stripe, construída com Laravel 13, Livewire 4 e Cashier.

## 📋 Sobre o Projeto

Subly é um sistema completo de gestão de assinaturas recorrentes que permite:

- 💳 Gerenciar assinaturas de clientes em tempo real
- 📊 Dashboard intuitivo com métricas e relatórios
- 🔐 Autenticação segura com 2FA (Two-Factor Authentication)
- 💰 Integração nativa com Stripe para pagamentos
- 📧 Gestão de faturas e e-mails transacionais
- 🔔 Webhooks para eventos de pagamento
- 📱 Interface responsiva com Flux UI
- ⚡ Performance otimizada com cache e queue
- 🧪 Testes automatizados com Pest.php
- 🐳 Containerização com Docker

## 🚀 Começar Rápido

### Pré-requisitos

- PHP 8.3 ou superior
- Composer 2.0+
- Node.js 18+ e npm
- Docker e Docker Compose (para desenvolvimento local)
- MySQL 8.0 (no Docker)
- Conta Stripe (para integração de pagamentos)

### Instalação

1. **Clonar o repositório**
   ```bash
   git clone https://github.com/seu-usuario/subly.git
   cd subly
   ```

2. **Instalar dependências**
   ```bash
   composer install
   npm install
   ```

3. **Configurar ambiente**
   ```bash
   cp .env.example .env
   php artisan key:generate
   ```

4. **Iniciar MySQL (Docker)**
   ```bash
   ./dev.sh start
   # ou
   docker compose up -d
   ```

5. **Rodar migrations**
   ```bash
   php artisan migrate
   ```

6. **Iniciar servidor**
   ```bash
   ./dev.sh serve
   # ou
   php artisan serve --host=0.0.0.0 --port=8000
   ```

7. **Acessar aplicação**
   ```
   http://localhost:8000
   ```

## 📦 Stack Tecnológico

### Backend
- **Laravel 13** - Framework web PHP moderno
- **Laravel Cashier 16.5** - Integração com Stripe
- **Laravel Fortify** - Autenticação e 2FA
- **Livewire 4** - Componentes reativos
- **Pest.php** - Framework de testes

### Frontend
- **Flux UI** - Sistema de design integrado
- **Tailwind CSS** - Framework CSS utility-first
- **Alpine.js** - Interatividade leve
- **Vite** - Build tool moderno

### Banco de Dados
- **MySQL 8.0** - Banco de dados relacional
- **Redis** - Cache e filas (opcional)
- **Laravel Cache** - Sistema de cache flexível

### Infraestrutura
- **Docker** - Containerização
- **Docker Compose** - Orquestração
- **Laravel Sail** - Ambiente de desenvolvimento

## 📁 Estrutura do Projeto

```
Subly/
├── app/                          # Código da aplicação
│   ├── Models/                   # Modelos Eloquent
│   │   └── User.php             # Modelo de usuário com Billable
│   ├── Http/
│   │   └── Controllers/          # Controladores
│   ├── Livewire/
│   │   └── Actions/             # Componentes Livewire
│   ├── Concerns/                # Traits compartilhados
│   │   ├── PasswordValidationRules.php
│   │   └── ProfileValidationRules.php
│   └── Providers/               # Service Providers
│       ├── AppServiceProvider.php
│       └── FortifyServiceProvider.php
│
├── database/                     # Migrações e seeders
│   ├── migrations/              # Arquivos de migração
│   ├── factories/               # Factories para testes
│   └── seeders/                 # Seeders iniciais
│
├── routes/                      # Definição de rotas
│   ├── web.php                 # Rotas web
│   ├── console.php             # Comandos Artisan
│   └── settings.php            # Rotas de configurações
│
├── resources/                   # Assets frontend
│   ├── views/                  # Templates Blade
│   │   ├── welcome.blade.php   # Página inicial
│   │   ├── dashboard.blade.php # Dashboard
│   │   ├── layouts/            # Layouts base
│   │   ├── components/         # Componentes reutilizáveis
│   │   ├── flux/               # Componentes Flux
│   │   └── partials/           # Partials
│   ├── css/
│   │   └── app.css             # Estilos globais
│   └── js/
│       └── app.js              # JavaScript da aplicação
│
├── tests/                       # Testes automatizados
│   ├── Feature/                # Testes de feature
│   │   ├── Auth/               # Testes de autenticação
│   │   ├── Settings/           # Testes de configurações
│   │   └── DashboardTest.php
│   └── Unit/                   # Testes unitários
│
├── config/                      # Arquivos de configuração
│   ├── app.php                 # Configurações gerais
│   ├── auth.php                # Autenticação
│   ├── database.php            # Banco de dados
│   ├── cache.php               # Cache
│   ├── fortify.php             # Fortify
│   └── ...
│
├── storage/                     # Arquivos gerados
│   ├── app/                    # Upload de usuários
│   ├── logs/                   # Logs da aplicação
│   └── framework/              # Cache e sessions
│
├── public/                      # Arquivos públicos
│   ├── index.php               # Ponto de entrada
│   └── ...
│
├── Dockerfile                   # Imagem Docker
├── docker-compose.yml          # Composição Docker
├── .dockerignore               # Arquivos ignorados no Docker
├── docker/
│   └── entrypoint.sh          # Script de inicialização
│
├── dev.sh                      # Helper de desenvolvimento
├── QUICKSTART.sh              # Guia rápido
├── README.md                  # Este arquivo
├── README_SETUP.md            # Setup detalhado
├── SETUP_RESUMO.md            # Resumo do setup
├── DOCKER_SETUP.md            # Guia Docker
│
├── composer.json              # Dependências PHP
├── package.json               # Dependências Node
├── vite.config.js             # Configuração Vite
├── pint.json                  # Configuração Pint (code style)
├── phpunit.xml                # Configuração Testes
└── artisan                    # CLI Laravel

```

## ⚙️ Configuração

### Variáveis de Ambiente (.env)

```env
# Aplicação
APP_NAME=Subly
APP_ENV=local
APP_KEY=base64:...
APP_DEBUG=true
APP_URL=http://localhost

# Banco de Dados
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3307
DB_DATABASE=subly
DB_USERNAME=root
DB_PASSWORD=secret

# Stripe (obrigatório para pagamentos)
STRIPE_KEY=pk_test_...
STRIPE_SECRET=sk_test_...
STRIPE_WEBHOOK_SECRET=whsec_...
CASHIER_CURRENCY=usd

# Cache & Session
CACHE_STORE=database
SESSION_DRIVER=database
QUEUE_CONNECTION=database

# Mail (opcional)
MAIL_MAILER=log
MAIL_FROM_ADDRESS=hello@example.com

# Redis (opcional)
REDIS_HOST=127.0.0.1
REDIS_PASSWORD=null
REDIS_PORT=6379
```

### Integração com Stripe

1. **Criar conta no Stripe**
   - Acesse https://stripe.com
   - Crie uma conta

2. **Obter chaves de API**
   - Vá para https://dashboard.stripe.com/apikeys
   - Copie `Publishable Key` e `Secret Key`
   - Adicione ao `.env`:
     ```env
     STRIPE_KEY=pk_test_...
     STRIPE_SECRET=sk_test_...
     ```

3. **Configurar webhooks locais**
   ```bash
   # Instalar Stripe CLI: https://stripe.com/docs/stripe-cli
   stripe login
   stripe listen --forward-to http://127.0.0.1:8000/stripe/webhook
   
   # Copie o STRIPE_WEBHOOK_SECRET que aparecer e adicione ao .env
   ```

## 🛠️ Desenvolvimento

### Usar o Helper Script (recomendado)

```bash
# Ver todos os comandos disponíveis
./dev.sh

# Iniciar MySQL
./dev.sh start

# Iniciar Laravel dev server
./dev.sh serve

# Rodar migrations
./dev.sh migrate

# Conectar ao MySQL CLI
./dev.sh db-cli

# Ver logs do MySQL
./dev.sh logs

# Reset completo do banco
./dev.sh fresh

# Parar containers
./dev.sh stop
```

### Comandos Artisan Úteis

```bash
# Gerar novo model com migration
php artisan make:model Nome -m

# Gerar controlador
php artisan make:controller NomeController -r

# Gerar componente Livewire
php artisan make:livewire component-name

# Rodar migrations
php artisan migrate

# Reverter última migration
php artisan migrate:rollback

# Resetar banco (CUIDADO!)
php artisan migrate:fresh --seed

# Abrir console interativa
php artisan tinker

# Limpar cache
php artisan cache:clear
```

### Build de Assets

```bash
# Development (watch mode)
npm run dev

# Production build
npm run build

# Linting com Pint
composer pint

# Linting JavaScript
npm run lint
```

## 🧪 Testes

### Rodar Testes

```bash
# Todos os testes
php artisan test

# Apenas testes de feature
php artisan test tests/Feature

# Apenas testes unitários
php artisan test tests/Unit

# Com output detalhado
php artisan test --verbose

# Coverage report
php artisan test --coverage
```

### Estrutura de Testes

```
tests/
├── Feature/
│   ├── Auth/
│   │   ├── LoginTest.php
│   │   ├── RegisterTest.php
│   │   └── TwoFactorTest.php
│   ├── Settings/
│   │   ├── ProfileTest.php
│   │   └── PasswordTest.php
│   └── DashboardTest.php
└── Unit/
    ├── Models/
    └── Services/
```

### Exemplo de Teste

```php
<?php

namespace Tests\Feature;

use App\Models\User;
use Tests\TestCase;

class DashboardTest extends TestCase
{
    public function test_dashboard_is_accessible_for_authenticated_users()
    {
        $user = User::factory()->create();

        $response = $this->actingAs($user)
            ->get('/dashboard');

        $response->assertStatus(200);
    }
}
```

## 📦 Dependências Principais

### Composer
- **laravel/framework** (13.0) - Framework web
- **laravel/cashier** (16.5) - Stripe integration
- **laravel/fortify** (1.34) - Autenticação
- **livewire/livewire** (4.1) - Componentes reativos
- **livewire/flux** (2.12) - Sistema de design
- **pestphp/pest** (4.4) - Framework de testes

### NPM
- **tailwindcss** - CSS framework
- **vite** - Build tool
- **alpinejs** - Interatividade frontend

## 🔐 Segurança

### Implementado

- ✅ Autenticação com Laravel Fortify
- ✅ Two-Factor Authentication (2FA)
- ✅ CSRF protection
- ✅ Password hashing com Bcrypt
- ✅ Rate limiting
- ✅ Validação de input
- ✅ Proteção de SQL injection
- ✅ HTTPS pronto para produção
- ✅ Webhook signature verification (Stripe)

### Boas Práticas

1. **Nunca commitar .env**
   ```bash
   # .env está no .gitignore
   ```

2. **Usar variáveis de ambiente**
   ```php
   $apiKey = env('STRIPE_KEY');
   ```

3. **Validar sempre**
   ```php
   $validated = $request->validate([
       'email' => 'required|email|unique:users',
       'password' => 'required|min:8',
   ]);
   ```

4. **Proteção de rota**
   ```php
   Route::middleware('auth:sanctum')->group(function () {
       Route::get('/dashboard', DashboardController::class);
   });
   ```

## 🚀 Deployment

### Preparação para Produção

1. **Build assets**
   ```bash
   npm run build
   ```

2. **Otimizar autoloader**
   ```bash
   composer install --optimize-autoloader --no-dev
   ```

3. **Cache de configuração**
   ```bash
   php artisan config:cache
   php artisan route:cache
   php artisan view:cache
   ```

4. **Gerar APP_KEY seguro**
   ```bash
   php artisan key:generate
   ```

5. **Rodar migrations**
   ```bash
   php artisan migrate --force
   ```

### Deploying com Docker

```bash
# Build imagem
docker build -t subly:latest .

# Rodar container
docker run -d \
  --name subly \
  -p 8000:8000 \
  -e APP_KEY=base64:... \
  -e DB_HOST=mysql \
  subly:latest
```

### Variáveis de Ambiente em Produção

```env
APP_ENV=production
APP_DEBUG=false
APP_URL=https://seu-dominio.com

# Stripe - chaves de produção
STRIPE_KEY=pk_live_...
STRIPE_SECRET=sk_live_...

# Database - produção
DB_HOST=db-produção.seu-provider.com
DB_PASSWORD=senha-super-segura

# Cache
CACHE_STORE=redis
REDIS_URL=redis://seu-redis:6379

# Queue
QUEUE_CONNECTION=redis
```

## 🐛 Troubleshooting

### MySQL não conecta

**Problema:** Connection refused ao banco de dados

**Solução:**
```bash
# Aguardar MySQL inicializar (10-15 segundos)
docker compose ps mysql

# Verificar logs
./dev.sh logs

# Reiniciar
docker compose down -v
docker compose up -d
```

### Porta 3307 em uso

**Problema:** Port 3307 already in use

**Solução:**
```bash
# Editar docker-compose.yml
# Mudar ports de ['3307:3306'] para ['3308:3306']
# Atualizar .env: DB_PORT=3308
```

### Erro de APP_KEY

**Problema:** No application encryption key has been specified

**Solução:**
```bash
php artisan key:generate
```

### Cashier/Billable não funciona

**Problema:** Class Billable not found

**Solução:**
```bash
# Regenerar autoloader
composer dump-autoload -o

# Reiniciar servidor
./dev.sh stop
./dev.sh start
./dev.sh serve
```

### Migrations falham

**Problema:** Migration failed

**Solução:**
```bash
# Ver status
php artisan migrate:status

# Rollback última
php artisan migrate:rollback

# Rollback tudo e refazer
php artisan migrate:refresh --seed
```

## 📚 Documentação Adicional

- [DOCKER_SETUP.md](DOCKER_SETUP.md) - Setup Docker detalhado
- [README_SETUP.md](README_SETUP.md) - Guia técnico completo
- [SETUP_RESUMO.md](SETUP_RESUMO.md) - Resumo visual do setup
- [Documentação Laravel](https://laravel.com/docs)
- [Documentação Stripe](https://stripe.com/docs)
- [Documentação Livewire](https://livewire.laravel.com)

## 🤝 Contribuindo

### Como Contribuir

1. Fork o projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

### Padrões de Código

- Siga o padrão PSR-12 (enforce com `composer pint`)
- Escreva testes para novas features
- Documente funções públicas
- Mantenha 80%+ cobertura de testes

### Relatando Bugs

Abra uma issue com:
- Descrição clara do problema
- Passos para reproduzir
- Comportamento esperado vs. atual
- Screenshots (se aplicável)
- Ambiente (OS, PHP version, etc)

## 📄 Licença

Este projeto está licenciado sob a Licença MIT - veja o arquivo [LICENSE](LICENSE) para detalhes.

## 👥 Autores

- **Diego Garcia**

## 🙏 Agradecimentos

- [Taylor Otwell](https://github.com/taylorotwell) - Laravel
- [Stripe](https://stripe.com) - Pagamentos
- [Livewire](https://livewire.laravel.com) - Componentes reativos

## 🗺️ Roadmap

- [ ] Mobile app (React Native)
- [ ] API RESTful completa
- [ ] Multi-tenancy support
- [ ] Advanced reporting
- [ ] Integração com outros gateways (PayPal, Square)
- [ ] Automation workflows
- [ ] Customer portal

---

**Última atualização:** 26 de Março de 2026

Made with ❤️ by Nexora
