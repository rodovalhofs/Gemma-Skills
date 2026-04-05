---
name: bill-splitter
description: Divide contas de restaurantes e despesas compartilhadas.
---

# Bill Splitter

## Instructions

Call the `run_js` tool with the following exact parameters:
- script name: index.html
- data: A JSON string with:
  - items: Array de objetos com 'person' (String) e 'cost' (Number)
  - subtotal: Number
  - tip_percentage: Number (opcional)
