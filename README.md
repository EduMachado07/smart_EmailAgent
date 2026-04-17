# Smart Email Agent (Automação Inteligente de Emails)

Ideia do projeto:

_"Um assistente automatizado que analisa, classifica e toma decisões sobre seus emails utilizando inteligência artificial."_

## Sobre o Projeto

Este projeto automatiza a triagem de emails, utilizando IA para interpretar o conteúdo das mensagens e decidir automaticamente qual ação deve ser tomada.

A automação roda com n8n e integra múltiplos serviços, funcionando como um assistente pessoal de produtividade.

## Problema

Gerenciar emails diariamente é uma tarefa repetitiva e ineficiente:

* Caixa de entrada lotada
* Muitas mensagens irrelevantes
* Dificuldade em identificar o que realmente importa
* Risco de perder emails importantes
* Tempo desperdiçado abrindo mensagens desnecessárias

## Solução

A automação resolve isso ao:

* Ler emails automaticamente
* Interpretar conteúdo com IA
* Gerar resumos inteligentes
* Classificar ações necessárias
* Executar ações automaticamente ou assistidas

## 🚀 Funcionalidades

* Leitura automática de emails (Gmail)
* Análise com IA (Groq / LLM)
* Geração de resumo inteligente
* Classificação por ação:

  * **Responder** → emails que exigem resposta
  * **Agendar** → eventos, reuniões, compromissos
  * **Notificar** → informações importantes
  * **Deletar** → conteúdos irrelevantes
* Notificação via Telegram
* Criação automática de eventos no Google Calendar
* Marcação de emails processados (evita duplicação)
* Execução automática com cron

## Fluxo da Automação

```text
Cron (execução diária)
   ↓
Gmail (buscar emails)
   ↓
Filtro (remover emails já processados)
   ↓
IA (resumo + classificação + ação)
   ↓
Switch (decisão)
   ↓
├── responder → Telegram
├── agendar → Google Calendar + Telegram
├── notificar → Telegram
└── deletar → marcar / ignorar
   ↓
Gmail (adicionar label PROCESSED_AI)
```

## Tecnologias Utilizadas

* n8n (automação)
* Docker (execução)
* Groq API (IA)
* Gmail API
* Telegram Bot API
* Google Calendar API

## Como Executar

### 1. Rodar n8n com Docker

```bash
docker compose up -d
```

### 2. Acessar o painel

```
http://localhost:5678
```

### 3. Importar workflow

* Import → selecionar arquivo JSON

### 4. Configurar credenciais

* Gmail (OAuth2)
* Google Calendar (OAuth2)
* Telegram Bot
* Groq API Key

### 5. Criar label no Gmail

```
PROCESSED_AI
```

### 6. Ativar automação

* Configurar cron
* Ativar workflow

## Exemplo de Saída da IA

```json
{
  "id": "123",
  "subject": "Entrevista",
  "from": "Empresa X",
  "resumo": "Convite para entrevista técnica.",
  "acao": "agendar",
  "data": "2026-04-22",
  "hora": "15:30",
  "titulo_evento": "Entrevista Desenvolvedor"
}
```

## Demonstração

> Fluxo no n8n

![Preview-Screens](https://github.com/EduMachado07/smart_EmailAgent/blob/main/assets/exampleN8N.png)

> Mensagem no Telegram

![Preview-Screens](https://github.com/EduMachado07/smart_EmailAgent/blob/main/assets/exampleTelegram.png)

> Evento criado no Google Calendar

![Preview-Screens](https://github.com/EduMachado07/smart_EmailAgent/blob/main/assets/exampleCalendar.png)

## 📌 Conclusão

Este projeto demonstra como aplicar inteligência artificial para automatizar tarefas reais do dia a dia, criando um sistema que analisa, decide e executa ações de forma autônoma.



_**Desenvolvido por Eduardo Machado**_

