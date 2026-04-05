---
name: send-whatsapp
description: Envia mensagens via WhatsApp usando Intents do Android.
---

# Send WhatsApp

## Contexto
O usuário quer enviar uma mensagem rápida sem precisar abrir o app e procurar o contato manualmente.

## Instructions
Quando o usuário pedir para enviar uma mensagem via WhatsApp:
1. **Identifique**:
   - `phone_number`: O número do destinatário com código do país (ex: 55119XXXXXXXX).
   - `message`: O conteúdo da mensagem.
2. **Execute**: Chame a ferramenta `run_intent` com os seguintes parâmetros:
   - intent: send_whatsapp
   - parameters: Um JSON string contendo:
     - `phone`: String.
     - `text`: String.

## Regras
- Certifique-se de que o número inclua o código do país.
- Se o usuário não fornecer o número, pergunte antes de chamar a intent.
- Informe ao usuário que o WhatsApp será aberto para confirmação final.
