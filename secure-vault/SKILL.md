---
name: secure-vault
description: Criptografa e descriptografa notas sensíveis localmente.
metadata:
  require-secret: true
  require-secret-description: Digite sua senha mestre para acessar o cofre.
---

# Secure Vault

## Instructions

Call the `run_js` tool with the following parameters:
- script name: index.html
- data: A JSON string with:
  - action: "encrypt" or "decrypt"
  - text: o texto para processar
