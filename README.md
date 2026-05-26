# MarsLink 🚀

**Plataforma integrada de comunicação e coordenação para missões em ambiente de latência extrema**

> Projetada para Marte. Aplicada na Terra.

---

## Sobre o projeto

MarsLink é uma plataforma de comunicação e coordenação desenvolvida para a **Missão Ares-1** — uma tripulação de 4 pessoas na primeira missão humana a Marte. O sinal entre os planetas leva de 3 a 22 minutos, o que torna impossível qualquer comunicação em tempo real com a Terra.

O diferencial do MarsLink é tratar o **delay como uma feature de design**, não como um bug a corrigir. Toda a arquitetura foi pensada para funcionar de forma robusta com conectividade intermitente — o mesmo desafio enfrentado por equipes humanitárias, regiões remotas e zonas de desastre aqui na Terra.

---

## Plataformas

| Plataforma | Descrição | Usuários |
|---|---|---|
| **App Mobile** | Comunicação, tarefas, log de missão e saúde | Tripulação na nave |
| **Dashboard Web** | Monitoramento, instruções e histórico | Controle Terra |

---

## Funcionalidades principais

### App Mobile (Tripulação)
- Login com e-mail, código de missão e senha
- Mapa orbital animado em tempo real
- Mensagens assíncronas com **Message Journey** (status de entrega visível)
- Fila offline — mensagens armazenadas localmente até a janela de comunicação abrir
- Gestão de tarefas com prioridade, animação de poeira marciana ao concluir
- Diário de bordo com estado emocional, fotos e vídeos
- Monitoramento de sinais vitais da tripulação
- Fluxo pós-envio: Tarefas → Log → Mapa orbital (distração produtiva sem countdown)

### Dashboard Web (Controle Terra)
- Login com código de missão
- Visão geral com mapa orbital, stats da missão e alertas
- Central de comunicações com fila de saída e chegada
- Monitoramento médico e psicológico da tripulação
- Gestão de tarefas por tripulante com delegação remota
- Log histórico com busca e filtros por tripulante, dia e humor
- Sidebar colapsável com navegação por hover
- Logout com fade de sessão

---

## Stack técnica

### Frontend
- **App Mobile**: HTML5 + CSS3 + JavaScript (PWA-ready)
- **Dashboard Web**: HTML5 + CSS3 + JavaScript
- **Tipografia**: Space Grotesk (texto) + Space Mono (dados técnicos)
- **Visualizações**: Canvas API (orbital, ECG, vitais, temperatura)

### Backend (a implementar)
- **Runtime**: Node.js + Express
- **Banco de dados**: PostgreSQL
- **Autenticação**: JWT
- **Padrão de mensagens**: Outbox Pattern (store-and-forward)

### Deploy (a implementar)
- **Backend**: Railway ou Render
- **Frontend Web**: Vercel
- **App Mobile**: PWA ou Expo

---

## Estrutura do repositório

```
marslink/
├── app/                    # App mobile da tripulação
│   └── index.html
├── dashboard/              # Dashboard web do Controle Terra
│   └── index.html
├── backend/                # API REST (a implementar)
│   ├── src/
│   │   ├── routes/
│   │   │   ├── auth.js
│   │   │   ├── messages.js
│   │   │   ├── tasks.js
│   │   │   ├── logs.js
│   │   │   ├── vitals.js
│   │   │   └── windows.js
│   │   ├── models/
│   │   ├── middleware/
│   │   └── index.js
│   ├── prisma/
│   │   └── schema.prisma
│   └── package.json
├── docs/                   # Documentação técnica
│   └── DOCUMENTATION.md
└── README.md
```

---

## Modelo de dados

O banco possui 8 tabelas principais:

| Tabela | Descrição |
|---|---|
| `users` | Tripulantes e operadores de controle |
| `missions` | Missões ativas (Ares-1) |
| `mission_members` | Vínculo usuário ↔ missão com papel |
| `messages` | Mensagens com status de entrega e delay |
| `tasks` | Tarefas por turno, prioridade e responsável |
| `mission_logs` | Diários de bordo com estado emocional |
| `vitals` | Sinais vitais simulados por tripulante |
| `communication_windows` | Janelas de transmissão com sinal e delay |

---

## Rotas da API (a implementar)

```
POST   /api/auth/login
POST   /api/auth/logout

GET    /api/messages?mission_id=
POST   /api/messages
PATCH  /api/messages/:id/ack

GET    /api/tasks?mission_id=&assigned_to=
POST   /api/tasks
PATCH  /api/tasks/:id/status

GET    /api/logs?mission_id=&crew=&day=&mood=
POST   /api/logs

GET    /api/vitals?mission_id=
POST   /api/vitals

GET    /api/windows/current?mission_id=
```

---

## Como acessar os protótipos

### App Mobile
Abra `app/index.html` em qualquer navegador moderno.

**Credenciais de demonstração:**
- E-mail: qualquer e-mail válido (ex: `cmdt.silva@ares1.nasa.gov`)
- Código de missão: qualquer sequência de 6+ números (ex: `200731`)
- Senha: qualquer senha com 6+ caracteres (ex: `nasa2031`)

### Dashboard Web
Abra `dashboard/index.html` em qualquer navegador moderno.

**Credenciais de demonstração:**
- Mesmas regras de formato acima

#### Link App: https://nataliaguaita.github.io/mars-link/app
#### Link Web: https://nataliaguaita.github.io/mars-link/web

---

## ODS da ONU

| ODS | Conexão |
|---|---|
| **ODS 9** — Indústria, inovação e infraestrutura | Arquitetura offline-first que conecta regiões sem infraestrutura |
| **ODS 11** — Cidades e comunidades sustentáveis | Aplicação em zonas de desastre e operações humanitárias |
| **ODS 3** — Saúde e bem-estar | Monitoramento psicológico e físico da tripulação em isolamento |

---

## Referências

- [NASA — nasa.gov](https://www.nasa.gov)
- [ESA — esa.int](https://www.esa.int)
- [Carta Internacional Space and Major Disasters](https://disasterscharter.org)
- NASA Playbook (ferramenta de missões análogas HERA, NEEMO, HI-SEAS)
- NASA DTN — Delay Tolerant Networking / ION

---

## Global Solution — FIAP 2TWDOR · 2º Semestre de 2026

Projeto desenvolvido para o desafio **Indústria Espacial** do Global Solution FIAP.
