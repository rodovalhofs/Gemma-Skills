---
name: flashcard-generator
description: Transforma textos complexos em flashcards interativos para estudo.
---

# Flashcard Generator

## Contexto
O usuário quer estudar um conteúdo novo ou revisar um material extenso.

## Instructions
Quando o usuário fornecer um texto para estudo (artigo, notas, transcrição):
1. **Sintetize**: Extraia os conceitos fundamentais do texto.
2. **Formate**: Crie pares de Pergunta (Frente) e Resposta (Verso) que sejam concisos e desafiadores.
3. **Execute**: Chame a ferramenta `run_js` com os seguintes parâmetros:
   - script name: index.html
   - data: Um JSON string contendo:
     - `cards`: Array de objetos `{ "front": string, "back": string }`.
     - `subject`: String (o tópico principal do conteúdo).

## Exemplo de JSON:
```json
{
  "subject": "Mitocôndria",
  "cards": [
    { "front": "Qual a função principal da mitocôndria?", "back": "Produção de ATP através da respiração celular." },
    { "front": "A mitocôndria possui DNA próprio?", "back": "Sim, o DNA mitocondrial." }
  ]
}
```
Limite o número de flashcards a 10 por chamada para manter a qualidade e o foco.
