# 🤖 Chatbot WhatsApp com N8N + Evolution API + Gemini

Este projeto implementa um **chatbot inteligente para WhatsApp**, utilizando **N8N** como orquestrador, integrado à **Evolution API** para comunicação com o WhatsApp e ao **Google Gemini** como modelo de IA.  
O fluxo também conta com um módulo de memória simples para manter contexto das conversas.

---

## 🚀 Tecnologias Utilizadas
- [N8N](https://n8n.io) – Automação de fluxos
- [Evolution API](https://evolution-api.com) – Integração com WhatsApp
- [Google Gemini](https://deepmind.google/technologies/gemini/) – IA para geração de respostas
- **Memória simples (N8N)** – Retenção de contexto entre mensagens
- Webhooks + HTTP Requests

---

## 📌 Estrutura do Workflow

1. **Webhook**  
   - Recebe mensagens enviadas ao número conectado via **Evolution API**.  

2. **Edit Fields (Set Node)**  
   - Extrai e organiza os principais dados recebidos no Webhook:  
     - 📱 **Quem mandou** → `{{ $json.body.sender }}`  
     - 🏷 **Instância** → `{{ $json.body.data.instanceId }}`  
     - 💬 **Mensagem** → `{{ $json.body.data.message.conversation }}`  
     - 🆔 **ID da Mensagem** → `{{ $json.body.data.key.id }}`  
     - 👤 **Nome da Pessoa** → `{{ $json.body.data.pushName }}`  

3. **AI Agent (Gemini)**  
   - Recebe a mensagem filtrada e gera uma resposta inteligente.  
   - Utiliza **memória simples** do N8N para manter contexto.  

4. **HTTP Request (Evolution API)**  
   - Envia a resposta do **Gemini** de volta ao usuário no WhatsApp.  

---

## 📷 Captura do Workflow  

![chatbotwtpp](https://github.com/user-attachments/assets/a20143f7-8ff9-47f8-b5bf-edccaa843069)
