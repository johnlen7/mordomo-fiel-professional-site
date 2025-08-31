# 🚀 Guia de Deploy - Railway

Este guia te ajudará a fazer o deploy do site da Mordomo Fiel no Railway de forma simples e rápida.

## 📋 Pré-requisitos

1. **Conta no Railway**: [railway.app](https://railway.app)
2. **Conta no GitHub**: Para conectar o repositório
3. **Repositório Git**: Com todos os arquivos do projeto

## 🛠️ Preparação do Projeto

### 1. Estrutura de Arquivos
Certifique-se de que seu projeto tenha esta estrutura:

```
mordomo-fiel-website/
├── index.html
├── styles.css
├── script.js
├── package.json
├── server.js
├── railway.json
├── .gitignore
├── README.md
└── DEPLOY.md
```

### 2. Verificar package.json
O arquivo `package.json` deve conter:

```json
{
  "name": "mordomo-fiel-website",
  "version": "1.0.0",
  "main": "server.js",
  "scripts": {
    "start": "node server.js"
  },
  "dependencies": {
    "express": "^4.18.2",
    "compression": "^1.7.4",
    "helmet": "^7.1.0"
  },
  "engines": {
    "node": ">=18.0.0"
  }
}
```

## 🚀 Deploy no Railway

### Método 1: Deploy via GitHub (Recomendado)

1. **Faça push para o GitHub**:
   ```bash
   git init
   git add .
   git commit -m "Primeiro commit - Site Mordomo Fiel"
   git branch -M main
   git remote add origin https://github.com/SEU_USUARIO/mordomo-fiel-website.git
   git push -u origin main
   ```

2. **Acesse o Railway**:
   - Vá para [railway.app](https://railway.app)
   - Faça login com sua conta GitHub

3. **Crie um novo projeto**:
   - Clique em "New Project"
   - Selecione "Deploy from GitHub repo"
   - Escolha seu repositório `mordomo-fiel-website`

4. **Configure o deploy**:
   - O Railway detectará automaticamente que é um projeto Node.js
   - Aguarde o build e deploy automático

### Método 2: Deploy via CLI

1. **Instale o Railway CLI**:
   ```bash
   npm install -g @railway/cli
   ```

2. **Faça login**:
   ```bash
   railway login
   ```

3. **Inicialize o projeto**:
   ```bash
   railway init
   ```

4. **Deploy**:
   ```bash
   railway up
   ```

## ⚙️ Configurações do Railway

### Variáveis de Ambiente (Opcional)
No painel do Railway, você pode configurar:

```
NODE_ENV=production
PORT=3000
```

### Domínio Personalizado
1. No painel do Railway, vá em "Settings"
2. Clique em "Domains"
3. Adicione seu domínio personalizado
4. Configure os registros DNS conforme instruído

## 🔍 Verificação do Deploy

### 1. Logs do Railway
- Acesse o painel do Railway
- Vá em "Deployments"
- Clique no deploy mais recente
- Verifique os logs para garantir que não há erros

### 2. Teste o Site
- Acesse a URL fornecida pelo Railway
- Teste todas as funcionalidades:
  - Navegação
  - Formulário de contato
  - Responsividade
  - Animações

### 3. Performance
- Use o Lighthouse para testar performance
- Verifique se o site carrega rapidamente
- Teste em diferentes dispositivos

## 🛠️ Troubleshooting

### Problema: Build falha
**Solução**:
- Verifique se o `package.json` está correto
- Confirme se todas as dependências estão listadas
- Verifique os logs de erro no Railway

### Problema: Site não carrega
**Solução**:
- Verifique se o `server.js` está configurado corretamente
- Confirme se a porta está sendo usada corretamente
- Verifique os logs do servidor

### Problema: Assets não carregam
**Solução**:
- Verifique se os caminhos dos arquivos estão corretos
- Confirme se o `express.static()` está configurado
- Verifique as políticas de segurança no `helmet`

## 📊 Monitoramento

### Railway Analytics
- Acesse "Metrics" no painel do Railway
- Monitore:
  - CPU e memória
  - Requests por minuto
  - Tempo de resposta
  - Erros

### Logs
- Configure alertas para erros
- Monitore logs regularmente
- Use ferramentas externas se necessário

## 🔄 Deploy Automático

### GitHub Actions (Opcional)
Crie `.github/workflows/deploy.yml`:

```yaml
name: Deploy to Railway
on:
  push:
    branches: [main]
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Deploy to Railway
        uses: railway/deploy@v1
        with:
          railway_token: ${{ secrets.RAILWAY_TOKEN }}
```

## 🎯 Próximos Passos

1. **Configurar domínio personalizado**
2. **Configurar SSL/HTTPS**
3. **Implementar monitoramento**
4. **Configurar backup**
5. **Otimizar performance**

## 📞 Suporte

Se encontrar problemas:

1. **Documentação do Railway**: [docs.railway.app](https://docs.railway.app)
2. **GitHub Issues**: Abra uma issue no repositório
3. **Comunidade**: Discord do Railway

---

**🎉 Parabéns! Seu site da Mordomo Fiel está online no Railway!**