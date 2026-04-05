---
name: bill-splitter
description: Divide contas de restaurantes de forma justa e interativa.
---

# Bill Splitter

## Contexto
O usuário acaba de sair de um jantar ou evento e tem uma conta confusa para dividir.

## Instructions
Quando o usuário fornecer os itens da conta (via texto, voz ou imagem OCR):
1. **Extraia**:
   - Uma lista de itens com o nome do item e o valor unitário.
   - O subtotal da conta.
   - (Opcional) Itens específicos atribuídos a pessoas específicas.
2. **Execute**: Chame a ferramenta `run_js` com os seguintes parâmetros:
   - script name: index.html
   - data: Um JSON string contendo:
     - `items`: Array de objetos `{ "name": string, "price": number, "person": string | null }`.
     - `subtotal`: Number.
     - `tax`: Number (se houver).
     - `tip_percent`: Number (default para 10 se não mencionado).

## Exemplo de JSON:
```json
{
  "items": [
    { "name": "Pizza", "price": 50.0, "person": "João" },
    { "name": "Cerveja", "price": 15.0, "person": null }
  ],
  "subtotal": 65.0,
  "tip_percent": 12
}
```
Represente itens sem dono (`person: null`) como itens a serem divididos igualmente por todos os participantes mencionados.
