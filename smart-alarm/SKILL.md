---
name: smart-alarm
description: Cria alarmes e cronômetros via Intents do Android.
---

# Smart Alarm

## Contexto
O usuário quer definir um lembrete rápido em voz alta ou via texto para gerenciar o tempo.

## Instructions
Quando o usuário pedir para criar um alarme:
1. **Identifique**:
   - `action`: "set_alarm" ou "set_timer".
   - `minutes`: Number (duração ou tempo até o alarme).
   - `label`: String (opcional, nome do alarme).
2. **Calcule**: Se o usuário disser "em 5 horas", calcule a hora específica.
3. **Execute**: Chame a ferramenta `run_intent` com os seguintes parâmetros:
   - intent: set_alarm
   - parameters: Um JSON string contendo:
     - `hour`: Number (24h).
     - `minutes`: Number.
     - `message`: String.
     - `skip_ui`: Boolean (true para ação direta).

## Regras
- Se o tempo não for fornecido, pergunte.
- Use `set_timer` se for um período curto (ex: "5 minutos").
- Use `set_alarm` se o usuário especificar um horário.
