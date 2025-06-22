# Secretaria IA - Automação de Atendimento via WhatsApp com n8n e OpenAI

Este repositório contém um projeto completo de automação inteligente de atendimentos clínicos via WhatsApp, utilizando o **n8n**, **OpenAI (GPT-4)**, **Google Calendar**, **Google Drive**, **PostgreSQL** e **Chatwoot**.

A assistente virtual se chama **Marlene**, e sua função é atuar como secretária digital, oferecendo um atendimento humano e eficiente automatizado via WhatsApp.

---

## \:star2: Funcionalidades

* **Atendimento inteligente** por texto e áudio via WhatsApp
* **Agendamento, reagendamento e cancelamento** de consultas via Google Calendar
* **Confirmação automática de consultas** com envio programado diário
* **Transcrição de áudio com IA** e formatação natural com SSML
* **Envio automático de arquivos** do Google Drive sob demanda
* **Escalonamento para atendimento humano** via etiqueta no Chatwoot
* **Memória de conversas** persistente com PostgreSQL

---

## \:gear: Tecnologias utilizadas

* [x] n8n (ambiente low-code para automações)
* [x] OpenAI GPT-4 / GPT-3.5 (respostas e classificação de intenção)
* [x] PostgreSQL (memória e fila de mensagens)
* [x] Chatwoot (gestão de conversas via WhatsApp)
* [x] Google Calendar (controle de agenda médica)
* [x] Google Drive (envio de arquivos)
* [x] ElevenLabs (síntese de voz)

---

## \:file\_folder: Estrutura dos Fluxos

| Nº | Nome do Fluxo                                     | Função Principal                                                                  |
| -- | ------------------------------------------------- | --------------------------------------------------------------------------------- |
| 1  | `Secretaria_IA.json`                              | Fluxo principal de atendimento da Marlene via WhatsApp                            |
| 2  | `2__MCP_Google_Calendar.json`                     | Conjunto de ações com Google Calendar: buscar, criar, atualizar e deletar eventos |
| 3  | `3__Baixar_e_enviar_arquivo_do_Google_Drive.json` | Busca e envia arquivos sob demanda                                                |
| 4  | `4__Escalar_humano.json`                          | Etiqueta e alerta de escalonamento de conversa para atendente humano              |
| 5  | `5__Enviar_agendamento.json`                      | Envia mensagem personalizada de confirmação de consulta                           |
| 6  | `6__Assistente_interno.json`                      | Assistente interno via Telegram para reagendamento e tarefas administrativas      |

---

## \:rocket: Como usar

1. Clone o repositório:

   ```bash
   git clone https://github.com/seuusuario/secretaria-ia-n8n.git
   ```
2. Importe os fluxos `.json` no seu ambiente n8n.
3. Configure as credenciais necessárias para:

   * OpenAI
   * PostgreSQL
   * Google Calendar
   * Google Drive
   * Chatwoot
   * ElevenLabs (opcional, para áudio)
4. Execute os testes com Webhooks e Simuladores de Conversa.

> **Importante:** certifique-se de que as ferramentas de IA estejam conectadas corretamente e que o banco de dados esteja sincronizado para manter a memória das conversas.

---

## \:bookmark: Exemplos de uso

### Agendamento

Usuário envia: *"Gostaria de marcar consulta com o Dr. João Paulo semana que vem"*
Marlene responde solicitando nome completo, data de nascimento e preferência de horário. Após receber os dados, consulta a agenda via Google Calendar e finaliza o agendamento com confirmação no WhatsApp.

### Confirmação de Consulta

Todos os dias úteis, às 08h, o fluxo executa e envia mensagens perguntando:
*"Olá \[nome]! Você confirma sua consulta com \[profissional] amanhã às \[hora]?"*

### Reagendamento via Telegram

Profissional envia comando no Telegram:
*"Reagendar todos os pacientes de hoje"*
O fluxo acessa os eventos do dia, extrai telefone e ID da conversa, e envia mensagens de reagendamento automatizadas.

---

## \:closed\_lock\_with\_key: Observações

* O projeto utiliza etiquetas como `agente-off` para desativar respostas automáticas em casos especiais.
* Toda conversa é salva no banco de dados com histórico e status.
* O envio de áudio utiliza SSML para melhorar a naturalidade da fala.

---

## \:bulb: Possíveis extensões futuras

* Dashboard com status dos atendimentos (Power BI ou Retool)
* Suporte multilíngue com seleção automática por idioma
* API externa REST para integração com sistemas legados

---

## \:handshake: Contato

Desenvolvido por \[Seu Nome].
Para dúvidas técnicas ou colaboração, envie uma mensagem via [LinkedIn](https://linkedin.com/in/seunome) ou abra uma issue aqui no repositório.

---

> Este projeto é uma demonstração técnica de integração entre inteligência artificial e automações de atendimento em saúde. Ele não substitui supervisão médica real.
