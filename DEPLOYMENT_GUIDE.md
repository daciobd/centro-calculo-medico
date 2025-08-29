# Guia de Deploy - Centro de Cálculo Médico

Este guia fornece instruções detalhadas para deploy da aplicação no GitHub e Render.

## 📋 Pré-requisitos

- Conta no GitHub
- Conta no Render
- Banco PostgreSQL (Neon Database recomendado)

## 🚀 Deploy no GitHub

### 1. Preparação do Repositório

1. **Crie um novo repositório no GitHub:**
   - Nome: `centro-calculo-medico`
   - Descrição: "Sistema médico integrado com 9 centros especializados"
   - Público ou Privado (sua escolha)

2. **Configure o Git localmente:**
```bash
git init
git add .
git commit -m "Initial commit: Complete medical center application"
git branch -M main
git remote add origin https://github.com/SEU_USUARIO/centro-calculo-medico.git
git push -u origin main
```

### 2. Configuração de Variáveis de Ambiente

Crie um arquivo `.env` baseado no `.env.example`:

```env
DATABASE_URL="postgresql://username:password@host:5432/database_name"
NODE_ENV="production"
```

## 🌐 Deploy no Render

### 1. Configuração do Banco de Dados

1. **No Render Dashboard:**
   - Clique em "New +"
   - Selecione "PostgreSQL"
   - Nome: `medical-center-db`
   - Plano: Starter (gratuito)
   - Anote a `Connection String`

### 2. Deploy da Aplicação

1. **No Render Dashboard:**
   - Clique em "New +"
   - Selecione "Web Service"
   - Conecte seu repositório GitHub

2. **Configurações:**
   - **Name:** `centro-calculo-medico`
   - **Root Directory:** (deixe vazio)
   - **Environment:** `Node`
   - **Build Command:** `npm install && npm run build`
   - **Start Command:** `npm run start`

3. **Variáveis de Ambiente:**
   - `NODE_ENV`: `production`
   - `DATABASE_URL`: (cole a connection string do PostgreSQL)

4. **Configurações Avançadas:**
   - **Health Check Path:** `/health`
   - **Auto-Deploy:** `Yes`

### 3. Configuração do Banco (Primeira Execução)

Após o deploy, execute as migrações:

1. Acesse o Render Shell ou use uma ferramenta local
2. Execute: `npm run db:push`

## 🔧 Configurações Adicionais

### HTTPS e Domínio Personalizado

1. **No Render:**
   - Vá para Settings do seu serviço
   - Em "Custom Domains", adicione seu domínio
   - Configure os DNS records conforme instruído

### Monitoramento

1. **Health Checks:**
   - O endpoint `/health` está configurado
   - Retorna status da aplicação

2. **Logs:**
   - Acesse "Logs" no painel do Render
   - Monitore erros e performance

## 🔐 Segurança

### Variáveis Sensíveis

Nunca commite no GitHub:
- `DATABASE_URL`
- API Keys
- Secrets de sessão

### Headers de Segurança

A aplicação já inclui:
- Validação de dados com Zod
- Sanitização de entradas
- Headers de segurança

## 📊 Monitoramento de Performance

### Métricas Importantes

1. **Response Time:**
   - Endpoint `/health` deve responder < 200ms
   - APIs médicas < 500ms

2. **Uptime:**
   - Meta: 99.9%
   - Monitorar através do Render

3. **Database Performance:**
   - Queries < 100ms
   - Conexões ativas

## 🔄 CI/CD Automatizado

### GitHub Actions (Opcional)

Crie `.github/workflows/deploy.yml`:

```yaml
name: Deploy to Render

on:
  push:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - name: Deploy to Render
      run: |
        curl -X POST "https://api.render.com/deploy/srv-YOUR_SERVICE_ID?key=YOUR_DEPLOY_KEY"
```

## 🆘 Troubleshooting

### Problemas Comuns

1. **Build Error:**
   - Verifique as dependências
   - Confirme Node.js version (18+)

2. **Database Connection:**
   - Verifique DATABASE_URL
   - Confirme IP whitelist no Neon

3. **Environment Variables:**
   - Confirme todas as variáveis necessárias
   - Reinicie o serviço após mudanças

### Logs Úteis

```bash
# Ver logs do Render
render logs -s seu-servico

# Testar localmente
npm run build
npm run start
```

## 📈 Otimização

### Performance

1. **CDN:** Configure para assets estáticos
2. **Compression:** Gzip já habilitado
3. **Caching:** Headers de cache configurados

### Escalabilidade

1. **Database:** Considere upgrading plan conforme uso
2. **Compute:** Monitor CPU/Memory usage
3. **Horizontal Scaling:** Render suporta múltiplas instâncias

## ✅ Checklist Final

- [ ] Repositório GitHub criado e configurado
- [ ] Banco PostgreSQL configurado no Render
- [ ] Web service configurado no Render
- [ ] Variáveis de ambiente definidas
- [ ] Deploy realizado com sucesso
- [ ] Health check funcionando (`/health`)
- [ ] Migrações do banco executadas
- [ ] Aplicação acessível via URL do Render
- [ ] Todas as funcionalidades testadas

## 🔗 Links Úteis

- [Documentação do Render](https://render.com/docs)
- [GitHub Help](https://help.github.com/)
- [Neon Database Docs](https://neon.tech/docs)

---

🎉 **Parabéns!** Sua aplicação médica está agora em produção e pronta para uso por profissionais de saúde!