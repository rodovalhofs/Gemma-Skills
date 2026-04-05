---
name: habit-tracker
description: Acompanha hábitos diários em um quadro visual persistente.
---

# Habit Tracker

## Contexto
O usuário quer manter a consistência em suas rotinas e visualizar seu progresso.

## Instructions
Quando o usuário mencionar um hábito praticado ou quiser ver seu progresso:
1. **Identifique a Ação**:
   - `log`: Registrar a conclusão de um hábito hoje.
   - `add`: Adicionar um novo hábito à lista.
   - `view`: Mostrar o quadro de hábitos.
2. **Execute**: Chame a ferramenta `run_js` com os seguintes parâmetros:
   - script name: index.html
   - data: Um JSON string contendo:
     - `action`: "log", "add", ou "view".
     - `habit_name`: String (ex: "Beber 2L de água", "Meditação").
     - `show_board`: Boolean (default true).

## Exemplo de JSON:
```json
{
  "action": "log",
  "habit_name": "Exercício físico",
  "show_board": true
}
```
Incentive o usuário a ser específico com os nomes dos hábitos para evitar duplicatas.
