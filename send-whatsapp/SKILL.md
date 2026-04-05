---
name: send-whatsapp
description: Envia uma mensagem via WhatsApp para um contato.
---

# Send WhatsApp Message

## Instructions

Call the `run_intent` tool with the following exact parameters:

- intent: send_whatsapp
- parameters: A JSON string with the following fields:
  - phone_number: the contact's phone number including country code. String.
  - message: the text message to send. String.
