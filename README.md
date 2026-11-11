# 💻 Gabriel Baptista — Desenvolvedor Full Stack

> Automação, dados e integração de sistemas para operações reais de e-commerce e indústria.
> Vim da operação (compras e almoxarifado) para o desenvolvimento — o que significa que meus sistemas nascem de problemas que eu mesmo já vivi no chão de fábrica.

📍 Curitiba/PR · 🏢 Desenvolvedor Full Stack @ Auto Peças Marechal

---

## 🚀 Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)
![Django](https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![React Native](https://img.shields.io/badge/React_Native-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Electron](https://img.shields.io/badge/Electron-47848F?style=for-the-badge&logo=electron&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-336791?style=for-the-badge&logo=postgresql&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)
![Selenium](https://img.shields.io/badge/Selenium-43B02A?style=for-the-badge&logo=selenium&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white)
![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=power-bi&logoColor=black)
![Cloudflare](https://img.shields.io/badge/Cloudflare-F38020?style=for-the-badge&logo=cloudflare&logoColor=white)
![Shopify](https://img.shields.io/badge/Shopify-7AB55C?style=for-the-badge&logo=shopify&logoColor=white)
![Figma](https://img.shields.io/badge/Figma-F24E1E?style=for-the-badge&logo=figma&logoColor=white)
![Claude API](https://img.shields.io/badge/Claude_API-D97757?style=for-the-badge&logo=anthropic&logoColor=white)
![Expo](https://img.shields.io/badge/Expo-000020?style=for-the-badge&logo=expo&logoColor=white)

---

## ⭐ Projeto em destaque — Cadastro Bot

**Plataforma interna de cadastro, conferência e gestão de produtos**
`Python` · `Flask` · `python-telegram-bot` · `SQLite` · `PostgreSQL (Neon)` · `Chart.js` · `Bootstrap 5` · `Claude Vision API` · `Google Drive API`

Ecossistema completo que cobre o ciclo de vida de um produto no e-commerce — do recebimento da peça até o anúncio publicado — combinando um **bot de Telegram** (interface operacional para a equipe) com um **painel web** (interface gerencial).

**Bot de Telegram** — a operação na mão de quem está no estoque
- Cadastro de peças por **leitura de QR Code** (OpenCV) direto pela câmera do celular
- **Descrições geradas por IA** a partir das fotos do produto (Claude Vision)
- Pipeline de fotos com Google Drive, otimização com Pillow e geração automática de infográficos
- Fluxos de **pré-cadastro, conferência de preço, alocação e localização** em estoque
- Emissão e controle de **etiquetas**, e importação de **XML de NF-e**
- Arquitetura **assíncrona** com workers concorrentes (`asyncio`, `Semaphore`, `PerChatUpdateProcessor`) — todo I/O bloqueante isolado em threads para suportar múltiplos usuários simultâneos sem travar o event loop

**Painel web (Flask)** — a gestão
- **Dashboard de KPIs**, cadastros, conferência, alocações, histórico de localizações, vendas e NF-e
- Módulo de **análise de desempenho** com Chart.js: produtividade por colaborador, perfil por hora e **cálculo de ociosidade** ponderado pela jornada oficial da empresa (com almoço excluído e % de utilização)
- Gestão de usuários, papéis e permissões, com vínculo ao usuário do Telegram
- **Design system próprio** na identidade visual da marca — sidebar fixa que vira drawer no mobile, tipografia industrial (Barlow Semi Condensed / Inter / JetBrains Mono) e SKUs estilizados como plaquinhas
- Acesso interno restrito via **VPN WireGuard**

**Dados e integrações**
- Espelhamento incremental **SQLite → PostgreSQL (Neon)** com detecção de alteração via `PRAGMA data_version` e sync incremental por timestamp
- Integração com **ERP** e com os marketplaces onde a operação vende
- Índices e queries otimizados nos caminhos mais quentes (eliminação de full table scans)

> 💡 Resultado: cadastro de produtos que antes era manual e sujeito a erro virou um fluxo guiado, auditável e mensurável — com dados de produtividade que sustentam decisões de gestão.

---


## 🤖 Agente de atendimento no WhatsApp (IA com regras em código)
`Python` · `Claude API (tool use)` · `Olist/Tiny API` · `Flask` · `SQLite` · `Cloudflare Tunnel` · `Chart.js`

Agente que atende clientes de autopeças no WhatsApp: identifica a peça (carro, ano, lado, par), consulta estoque ao vivo e histórico de vendas, envia fotos e só informa o preço quando ele bate com o cadastro conferido.

- **Falha fechada:** a decisão de liberar uma peça é feita em **código**, não no prompt; se qualquer fonte falha ou diverge, a conversa vai para um vendedor
- **Painel ao vivo** para a TV da loja, **dashboard** de métricas (tempo de resposta, escaladas, peças cotadas x vendidas, leads novos) e **chat dos vendedores** na web e no app
- **Regras editáveis por chat** com aprovação e trilha de auditoria; divisão dos contatos entre vendedores por desempenho
- **Prompt caching** e controle de custo da API (~80% menos por chamada)

---
## 🧩 Outros projetos

### 🤖 Automação de Marketplaces (Selenium)
`Python` · `Selenium` · `Google Sheets API`
Robôs de publicação e manutenção de anúncios em marketplace via ERP: criação de listagens, preenchimento de **compatibilidade veicular**, enriquecimento de categoria, gestão de fotos e **sincronização de estoque** por filtro avançado de SKU. Registro incremental de execuções em Google Sheets como camada de coordenação entre contas.

### 📱 APM App (React Native / Expo)
`React Native` · `Expo` · `API REST`
App interno de gestão de estoque, com cadastro, conferência de preço e chat entre vendedores.

### 🔧 Scripts de correção fiscal e cadastral em massa
`Python` · `OAuth2` · `REST APIs`
Toolchain para atualização em lote de campos fiscais (**NCM, CEST, origem**) e controle de estoque em catálogos com **centenas de milhares de SKUs**, com rate limiting, renovação de token, checkpoint/resume e controle de reprocessamento — projetado para jobs de dezenas de horas sem perda de progresso.

### 💬 Atendimento via WhatsApp com IA
`Python` · `FastAPI` · `Cloudflare D1` · `NSSM` · `Windows Server`
Microsserviço que conecta um agente de IA de atendimento à base de estoque, permitindo consulta de disponibilidade e preço em tempo real durante a conversa com o cliente. Deploy como serviço no Windows Server.

### 🛒 Loja e vitrine interna (Shopify)
`Liquid` · `JavaScript` · `Cloudflare R2`
Tema Shopify customizado desenvolvido do zero e páginas internas de consulta de produtos alimentadas por catálogo servido via Cloudflare R2 — usadas pela equipe comercial no atendimento.

### 📊 Business Intelligence e relatórios
`Python` · `pandas` · `ReportLab` · `Power BI` · `PostgreSQL` · `DAX`
Geração automática de relatórios em PDF (desempenho de equipe, vendas por cadastrador, apuração de premiações, controle de ponto com regras de atraso) e dashboards dinâmicos com integração direta ao banco e automação de ETL.

### 🟦 Análise de Fluxo de Clientes com Visão Computacional
`Python` · `YOLO` · `OpenCV` · `Power BI`
Detecção de clientes e análise de tempo de fila em rede de postos de combustível, com exportação para dashboards — subsidiando decisões de **jornada, dimensionamento e contratação baseadas em dados reais**.

### 📚 Conversão Automática de Artigos Científicos (PDF → XML JATS)
`Python` · `PyMuPDF` · `lxml` · `BeautifulSoup` · `Regex`
Automação da conversão de artigos científicos para o padrão **JATS** exigido pelo SciELO Brasil: extração e normalização de metadados, conversão estruturada de seções, tabelas e referências, e validação automática contra o schema.

### 💸 Aplicação Desktop com Validador de Cédulas (ID003)
`Node.js` · `React` · `Electron`
Sistema para máquinas de autoatendimento financeiro: cadastro de usuários, registro de cédulas depositadas, impressão de comprovantes térmicos (ESC/POS) e suporte multilíngue.

### 🧰 Sistema Web para Armário Automatizado
`Django` · `JavaScript` · `APIs REST`
Almoxarifado inteligente integrado a armário automatizado, com controle de estoque, registro de movimentações e comunicação direta com microcontroladores via API.

### ⚓ Aplicativo Mobile de Monitoramento
`React Native` · `Expo` · `API REST`
Monitoramento em tempo real do fluxo de entrada de terminal, com interface que se adapta automaticamente ao status operacional da via.

### ✏️ Prototipagem e Design de Interface
`Figma` · `UX/UI`
Protótipos interativos para sistemas internos de versionamento de planilhas e dashboards de planejamento estratégico.

---

## 🧠 Como eu trabalho

- **Problema antes de tecnologia** — quase todo projeto meu resolve uma dor que eu vi acontecer na operação
- **Automação de ponta a ponta** — do coletor de dados ao dashboard que a diretoria abre
- **Robustez em produção** — checkpoint/resume, rate limit, retry e observabilidade em qualquer job que rode por horas
- **Interface importa** — sistema interno também merece design decente

---

## 📫 Contato

📧 **E-mail:** [gabrielbaptista096@gmail.com](mailto:gabrielbaptista096@gmail.com)
💼 **LinkedIn:** [gabrielbap96](https://www.linkedin.com/in/gabrielbap96/)
💻 **GitHub:** [BaptistaGab](https://github.com/BaptistaGab)
📱 **WhatsApp:** [Fale comigo](https://api.whatsapp.com/send?phone=41997526613)
