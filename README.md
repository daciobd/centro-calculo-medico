# Centro de Cálculo Médico - Sistema Integrado de Medicina Clínica

Um sistema médico completo e integrado que oferece aos profissionais de saúde ferramentas avançadas para cálculos médicos, interpretação de exames, análise de imagens com IA, monitoramento em tempo real e gerenciamento farmacológico.

## 🏥 Visão Geral

O Centro de Cálculo Médico é uma plataforma unificada que combina 9 centros especializados em um único sistema, proporcionando uma experiência completa e integrada para profissionais de saúde.

### 🎯 Centros Integrados

1. **🧮 Centro de Cálculo Médico**
   - Calculadoras de risco cardiovascular (Framingham, CHA₂DS₂-VASc)
   - Escores de gravidade (SOFA, APACHE II)
   - Índices clínicos e fórmulas médicas

2. **📋 Centro de Protocolos**
   - Protocolos de emergência
   - Diretrizes clínicas
   - Fluxogramas de decisão

3. **🔬 Centro de Exames**
   - Interpretação automatizada de exames laboratoriais
   - Referências clínicas atualizadas
   - Análise de perfis metabólicos

4. **💬 Comunicação com Paciente**
   - Resumos em linguagem simples
   - Material educativo
   - Orientações personalizadas

5. **🔬 Centro de Pesquisa Clínica**
   - Randomização de pacientes
   - Formulários eletrônicos (eCRF)
   - Análise estatística automatizada

6. **💊 Centro de Farmácia Clínica**
   - Verificação de interações medicamentosas
   - Ajuste de doses
   - Farmacovigilância

7. **📊 Centro de Monitoramento**
   - Dashboard em tempo real
   - Alertas automáticos
   - Integração com dispositivos IoT

8. **🔬 Centro de Análise de Imagens Médicas**
   - Interpretação automatizada com IA
   - Detecção de anomalias por deep learning
   - Sistema DICOM integrado

## 🚀 Tecnologias

### Frontend
- **React 18** com TypeScript
- **Vite** para build e desenvolvimento
- **Tailwind CSS** para estilização
- **shadcn/ui** para componentes
- **React Query** para gerenciamento de estado
- **Wouter** para roteamento

### Backend
- **Node.js** com Express.js
- **TypeScript** para type safety
- **Drizzle ORM** para banco de dados
- **PostgreSQL** (Neon Database)
- **Zod** para validação

### Recursos Avançados
- **WebSocket** para comunicação em tempo real
- **AI/ML** para análise de imagens médicas
- **Sistema DICOM** para imagens médicas
- **IoT Integration** para dispositivos médicos

## 📦 Instalação e Desenvolvimento

### Pré-requisitos
- Node.js 18+
- PostgreSQL
- Git

### Configuração Local

1. **Clone o repositório**
```bash
git clone https://github.com/seu-usuario/centro-calculo-medico.git
cd centro-calculo-medico
```

2. **Instale as dependências**
```bash
npm install
```

3. **Configure as variáveis de ambiente**
```bash
cp .env.example .env
```

Edite o arquivo `.env` com suas configurações:
```env
DATABASE_URL="postgresql://user:password@localhost:5432/medical_center"
NODE_ENV="development"
PORT=5000
```

4. **Execute as migrações do banco**
```bash
npm run db:push
```

5. **Inicie o servidor de desenvolvimento**
```bash
npm run dev
```

O aplicativo estará disponível em `http://localhost:5000`

## 🔧 Scripts Disponíveis

- `npm run dev` - Inicia o servidor de desenvolvimento
- `npm run build` - Gera o build de produção
- `npm run start` - Inicia o servidor de produção
- `npm run db:push` - Aplica mudanças no schema do banco
- `npm run db:studio` - Abre o Drizzle Studio
- `npm run lint` - Executa o linter
- `npm run type-check` - Verifica tipos TypeScript

## 🚀 Deploy

### Render (Recomendado)

1. **Conecte seu repositório GitHub ao Render**

2. **Configure as variáveis de ambiente no Render:**
```env
DATABASE_URL=postgresql://...
NODE_ENV=production
```

3. **Configure o comando de build:**
```bash
npm run build
```

4. **Configure o comando de start:**
```bash
npm run start
```

### Docker (Opcional)

```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production
COPY . .
RUN npm run build
EXPOSE 5000
CMD ["npm", "start"]
```

## 🔒 Segurança

- Validação rigorosa de dados com Zod
- Sanitização de entradas
- Rate limiting implementado
- Logs de auditoria
- Criptografia de dados sensíveis

## 📖 Documentação da API

### Endpoints Principais

#### Calculadoras Médicas
- `GET /api/calculators` - Lista todas as calculadoras
- `POST /api/calculations` - Executa um cálculo
- `GET /api/calculations/recent` - Histórico de cálculos

#### Interpretação de Exames
- `POST /api/exam-interpretations` - Interpreta exames
- `GET /api/exam-interpretations/recent` - Histórico de interpretações

#### Análise de Imagens
- `POST /api/medical-imaging/analyze` - Análise de imagem com IA
- `GET /api/medical-imaging/reports/:id` - Relatório de análise

#### Monitoramento
- `GET /api/monitoring/dashboard` - Dashboard em tempo real
- `POST /api/monitoring/alerts` - Configurar alertas

## 🤝 Contribuição

1. Fork o projeto
2. Crie uma branch para sua feature (`git checkout -b feature/nova-feature`)
3. Commit suas mudanças (`git commit -m 'Adiciona nova feature'`)
4. Push para a branch (`git push origin feature/nova-feature`)
5. Abra um Pull Request

## 📋 Requisitos do Sistema

### Mínimos
- RAM: 4GB
- Processador: Dual-core 2.0GHz
- Armazenamento: 10GB

### Recomendados
- RAM: 8GB
- Processador: Quad-core 2.5GHz+
- Armazenamento: 50GB SSD

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

## 🆘 Suporte

Para suporte e dúvidas:
- 📧 Email: suporte@centrocalculomedico.com
- 📱 WhatsApp: +55 (11) 99999-9999
- 🌐 Website: https://centrocalculomedico.com

## 🏆 Reconhecimentos

- Desenvolvido para profissionais de saúde
- Baseado em diretrizes médicas atualizadas
- Validado por especialistas em medicina
- Interface otimizada para uso clínico

---

**Versão:** 2.0.0  
**Última atualização:** Agosto 2025  
**Status:** Produção ✅