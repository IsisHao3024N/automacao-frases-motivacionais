# 💬 Automação de Frases Motivacionais com n8n

Uma automação desenvolvida no **n8n** que busca frases motivacionais em inglês, traduz o conteúdo para português e envia o resultado por e-mail. O projeto também possui um workflow separado para notificar falhas não tratadas.

## 🎯 Objetivo

Automatizar o envio de mensagens motivacionais por e-mail, praticando integração de APIs, agendamento, validação de dados e tratamento de erros.

## ⚙️ Como funciona

O workflow principal executa estas etapas:

1. **Agendamento:** o Schedule Trigger inicia a automação todos os dias às **8h** (horário configurado no workflow).
2. **Busca da frase:** o HTTP Request consulta a **ZenQuotes API** para obter uma frase motivacional.
3. **Tradução:** outro HTTP Request utiliza a **MyMemory API** para traduzir a frase para português brasileiro.
4. **Validação:** o nó IF verifica se o campo de texto traduzido não está vazio.
5. **Envio:** quando a condição é verdadeira, o Gmail envia a frase por e-mail.

## 🔁 Confiabilidade e tratamento de erros

- **Retry On Fail:** está ativado nos dois nós HTTP Request para permitir novas tentativas em caso de falhas temporárias nas APIs.
- **IF:** evita o envio do e-mail quando o campo de tradução está vazio.
- **Error Workflow:** um workflow separado utiliza Error Trigger para receber falhas não tratadas do workflow principal e enviar uma notificação por e-mail.

## 🧰 Tecnologias e serviços

- **n8n** — criação e execução dos workflows.
- **ZenQuotes API** — obtenção das frases motivacionais.
- **MyMemory API** — tradução de textos.
- **Gmail** — envio das mensagens e notificações.
- **HTTP Request, IF e Error Trigger** — integração, validação e tratamento de falhas.

## 🗂️ Estrutura do repositório

```text
automacao-frases-motivacionais/
├── README.md
└── workflows/
    ├── FrasesMotivacionais.json
    └── TratamentoDeErrosFrasesMotivacionais.json
```

## 🚀 Como importar no n8n

1. Baixe os arquivos JSON da pasta `workflows`.
2. No n8n, importe `FrasesMotivacionais.json` usando a opção **Import from File**.
3. Importe também `TratamentoDeErrosFrasesMotivacionais.json`.
4. Configure suas próprias credenciais do Gmail nos nós correspondentes.
5. No workflow principal, confira em **Settings → Error Workflow** se o workflow de tratamento de erros está selecionado.
6. Ajuste o destinatário do e-mail e teste os workflows antes de ativá-los.

> **Importante:** credenciais pessoais e tokens não são incluídos nos arquivos. Configure suas próprias credenciais no n8n. O horário de 8h segue o fuso horário configurado na sua instância do n8n.

## 📚 Aprendizados

- Consumo e integração de APIs REST.
- Agendamento de tarefas automatizadas.
- Manipulação e validação de dados retornados por APIs.
- Integração com o Gmail.
- Configuração de novas tentativas em requisições HTTP.
- Tratamento e notificação de falhas em workflows.

## 👩‍💻 Desenvolvido por

**Izadora Vitória**  
Estudante de Análise e Desenvolvimento de Sistemas | Desenvolvedora em formação | Interessada em Inteligência Artificial e automações.
