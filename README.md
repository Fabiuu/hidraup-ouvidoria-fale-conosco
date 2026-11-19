<p align="center">
  <img src="imagens/banner.png" alt="Ouvidoria: Fale Conosco · Hidraup" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white">
  <img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white">
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black">
  <img src="https://img.shields.io/badge/Google%20Apps%20Script-4285F4?style=for-the-badge&logo=google&logoColor=white">
  <img src="https://img.shields.io/badge/Google%20Sheets-34A853?style=for-the-badge&logo=googlesheets&logoColor=white">
  <img src="https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white">
  <img src="https://img.shields.io/badge/Bash-4EAA25?style=for-the-badge&logo=gnubash&logoColor=white">
</p>
<p align="center">
  <img src="https://img.shields.io/badge/OWASP%20ZAP-0%20falhas%20altas-00549E?style=for-the-badge&logo=owasp&logoColor=white">
  <img src="https://img.shields.io/badge/Mozilla%20Observatory-A%2B-brightgreen?style=for-the-badge&logo=mozilla&logoColor=white">
  <img src="https://img.shields.io/badge/SSL%20Labs-A%2B-brightgreen?style=for-the-badge&logo=letsencrypt&logoColor=white">
  <img src="https://img.shields.io/badge/custo-R%24%200-success?style=for-the-badge">
</p>

<p align="center">
  <b>Canal digital de ouvidoria da Hidraup Serviços Hidráulicos e Pneumáticos (Betim/MG).</b><br>
  Funcionários e clientes apontam a câmera para um QR code e, em menos de 1 minuto, enviam uma <b>Melhoria</b>, <b>Reclamação</b> ou <b>Denúncia</b> direto para a direção, com anonimato opcional.
</p>

> 🔐 **Repositório vitrine.** Ele só apresenta o projeto. Não tem código-fonte, link do sistema nem arquivos para download.

---

## 📊 Números

| ⚡ Envio | 💸 Custo | 🛡️ Segurança | 🐞 Vulnerabilidades altas | 📱 Telas |
|:---:|:---:|:---:|:---:|:---:|
| **< 1 min** | **R$ 0** | **A+** | **0** | **320px → desktop** |

---

## 🎯 O problema

Sugestões, reclamações e denúncias se perdiam no caminho ou nem eram feitas. Faltava um canal **simples, rápido e seguro** pra qualquer pessoa falar com a direção **sem medo de ser exposta**.

## 🚀 A solução

| | Destaque |
|:---:|---|
| 📷 | **QR code → página no celular.** Sem app, sem login, sem cadastro |
| 🗂️ | **3 categorias:** Melhoria, Reclamação e Denúncia |
| 🕶️ | **Anonimato opcional:** se identificar não é obrigatório |
| 🔖 | **Protocolo único e aleatório**, com botão de copiar e **consulta da resposta** da direção |
| 📨 | **Entrega imediata:** e-mail anti-spam na caixa da ouvidoria e registro numa planilha privada |
| 📅 | **Resumo mensal automático** todo dia 1º |
| ⚖️ | **Aviso de LGPD** e **compromisso de não retaliação** |
| 💬 | Atalhos flutuantes para **WhatsApp**, **telefone** e **site** da empresa |

<p align="center">
  <img src="imagens/pagina-celular.jpg" alt="Página da ouvidoria no celular" width="300">
</p>

---

## 🧠 Como funciona por trás

```mermaid
flowchart LR
    A[📱 Celular] -->|aponta a câmera| B[🔳 QR code]
    B --> C[🌐 Página estática<br/>Vercel + CSP rígida]
    C -->|POST HTTPS| D[⚙️ Google Apps Script<br/>conta exclusiva da ouvidoria]
    D --> E{🛡️ Validação<br/>honeypot · limite 10k · rate limit}
    E -->|recusado| X[⛔ Bloqueado]
    E -->|ok| F[🔖 Protocolo aleatório]
    F --> G[(📊 Google Sheets<br/>privada)]
    F --> H[📨 E-mail anti-spam<br/>para a ouvidoria]
    F --> I[✅ Tela de Obrigado<br/>com o protocolo]
    J[⏰ Gatilho mensal] -->|todo dia 1º| K[📈 Resumo do mês]
    G --> K
```

```mermaid
sequenceDiagram
    autonumber
    actor P as Pessoa
    participant W as Página (Vercel)
    participant S as Apps Script
    participant DB as Planilha privada
    participant M as E-mail da ouvidoria
    P->>W: Escaneia o QR e escreve a mensagem
    W->>S: Envia (HTTPS)
    S->>S: Valida honeypot, tamanho e limite de envios
    S->>DB: Grava com protocolo aleatório
    S->>M: Notifica a direção
    S-->>W: Confirma o envio
    W-->>P: Obrigado! Seu protocolo é HDP-...
    P->>W: Depois, consulta o protocolo
    W->>S: Consulta (com limite de tentativas)
    S-->>W: Só a resposta da direção, nunca a mensagem
```

---

## 🛠️ Linguagens e tecnologias

| Camada | Tecnologia |
|---|---|
| 🎨 **Front-end** | HTML5, CSS3 e JavaScript puro (sem frameworks), visual **Liquid Glass** |
| ⚙️ **Back-end** | Google Apps Script (JavaScript) em conta exclusiva da ouvidoria |
| 🗄️ **Dados** | Google Sheets privada, com protocolo e coluna de resposta |
| ☁️ **Hospedagem** | Vercel, com cabeçalhos de segurança (CSP, HSTS preload, Permissions-Policy) |
| 🖨️ **Cartaz** | Python + Pillow (PIL) para gerar o A4 em 300 dpi e pyzbar para validar o QR |
| 🔍 **Segurança** | Bash + OWASP ZAP, Mozilla Observatory, SSL Labs e testes com Playwright |

## 🎨 Design

- Cores da marca Hidraup (azul-marinho, azul e vermelho)
- **Raup**, o mascote da Hidraup, e os selos **ISO 9001** e **ISO 14001** no topo
- Contraste medido de **4,5:1 ou mais** em todos os textos (padrão WCAG AA)
- Mobile-first, testado de 320px até desktop

---

## 🔒 Segurança (testes reais, 19/11/2026)

| Verificação | Resultado |
|---|:---:|
| Mozilla Observatory | 🟢 **A+** (120 pontos, 12/12) |
| SSL Labs (TLS) | 🟢 **A+ / A** |
| OWASP ZAP 2.17 (varredura passiva) | 🟢 **0 falhas altas** |
| Injeção de código (XSS) no formulário | 🟢 Virou texto inerte |
| Mensagem gigante (10.001 caracteres) | 🟢 Recusada no servidor |
| Robôs de spam (honeypot) | 🟢 Recusados |
| Consulta de protocolo | 🟢 Limite de tentativas contra força bruta |

<p align="center">
  <img src="imagens/varredura-seguranca.png" alt="Resumo da varredura de segurança" width="850">
</p>

---

## 📦 Entregas

1. 🌐 **Página da ouvidoria** no ar e funcionando
2. 🖨️ **Cartaz A4** para impressão, com QR code (oculto nesta vitrine)
3. 📽️ **Apresentação** para os sócios e gerentes da empresa

<p align="center">
  <img src="imagens/cartaz.png" alt="Cartaz A4 (QR code oculto)" width="400">
  &nbsp;&nbsp;
  <img src="imagens/apresentacao-capa.jpg" alt="Capa da apresentação" width="520">
</p>

---

## 👤 Autor

<p align="center">
  <b>Idealizado e desenvolvido por Fábio Henrique Corrêa (Fabin)</b><br>
  Proprietário e analista de TI · Hidraup<br>
  Desenvolvimento assistido por inteligência artificial<br>
  <sub>Betim/MG · 2026</sub>
</p>
