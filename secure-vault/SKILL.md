---
name: secure-vault
description: Criptografa e descriptografa notas sensíveis usando a Web Crypto API.
metadata:
  require-secret: true
  require-secret-description: "Sua senha mestra nunca sai do dispositivo e é usada para gerar a chave de criptografia."
---

# Secure Vault

## Contexto
O usuário precisa guardar informações ultra-sensíveis (senhas, segredos corporativos, diário) que não devem estar em texto simples nem na memória do modelo.

## Instructions
Quando o usuário quiser criptografar ou descriptografar um texto:
1. **Identifique a Ação**: "encrypt" (proteger) ou "decrypt" (revelar).
2. **Execute**: Chame a ferramenta `run_js` com os seguintes parâmetros:
   - script name: index.html
   - data: Um JSON string contendo:
     - `action`: "encrypt" ou "decrypt".
     - `text`: O conteúdo a ser processado.

## Segurança
- Esta skill requer uma "Secret" (senha mestra).
- O processo é 100% local. O modelo Gemma apenas recebe o resultado final processado (o texto cifrado ou o texto revelado).
