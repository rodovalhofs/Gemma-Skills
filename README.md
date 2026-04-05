# Gemma 4 Agent Skills for AI Edge Gallery (Android)

Uma coleção de habilidades práticas e focadas em produtividade para o modo agente do Gemma 4 no Android. Projetadas para durabilidade offline, privacidade e automação de tarefas reais.

---

## 🛠 Skills Categorizadas

### 1. Focus Optimizer
*   **Tipo**: Text-Only (Persona)
*   **Propósito**: Transformar caos em cronogramas Pomodoro estruturados.
*   **Dados e Segurança**: Processa agendas e prioridades. Execução 100% via LLM local. Nenhuma permissão extra necessária.
*   **Status Pública**: Pronta para distribuição.

### 2. Bill Splitter
*   **Tipo**: JavaScript + Interactive WebView
*   **Propósito**: Rateio inteligente de contas com UI ajustável para gorjetas.
*   **Dados e Segurança**: Processa gastos e nomes de contatos. Execução local via WebView. Não acessa rede.
*   **Status Pública**: Pronta.

### 3. Flashcard Generator
*   **Tipo**: JavaScript + 3D WebView
*   **Propósito**: Estudo interativo (Spaced Repetition) a partir de qualquer texto.
*   **Dados e Segurança**: Processa materiais de estudo. Sem coleta de telemetria.
*   **Status Pública**: Pronta.

### 4. Habit Tracker
*   **Tipo**: JavaScript + WebView (Persistence)
*   **Propósito**: Quadro Kanban de hábitos com progresso salvo localmente.
*   **Dados e Segurança**: Rastreia comportamentos diários. Os dados são salvos no `localStorage` isolado da WebView do Android.
*   **Status Pública**: Pronta.

### 5. Secure Vault
*   **Tipo**: JavaScript (Encryption)
*   **Propósito**: Cofre forte local usando AES-GCM (Web Crypto API).
*   **Dados e Segurança**: Criptografa senhas e notas. Requer senha mestra que **nunca** sai do dispositivo nem é lida pelo modelo.
*   **Status Pública**: Pronta (altíssima segurança).

### 6. WhatsApp Messenger
*   **Tipo**: Native Intent (`run_intent`)
*   **Propósito**: Envio rápido de mensagens.
*   **Dados e Segurança**: Acessa números de telefone e textos de mensagem. Requer integração manual no código-fonte (`IntentHandler.kt`).
*   **Status Pública**: Requer ressalva sobre a necessidade de recompilar o app.

### 7. Smart Alarm
*   **Tipo**: Native Intent (`run_intent`)
*   **Propósito**: Gestão de alarmes e cronômetros via voz/texto.
*   **Dados e Segurança**: Acessa rotinas de sono. Requer modificação nativa.
*   **Status Pública**: Requer ressalva técnica.

---

## 🚀 Como Instalar e Usar

1.  **Clone este Repositório** diretamente no seu dispositivo Android (ex: na pasta `Downloads`).
2.  **Abra o AI Edge Gallery** -> Vá em **Skill Manager**.
3.  **Importar localmente**: Toque no **(+)** e selecione a pasta da skill desejada (ex: `bill-splitter`).
4.  **Skills Nativas**: Para "WhatsApp" e "Alarm", siga o guia em [NATIVE_INTEGRATION.md](./NATIVE_INTEGRATION.md) para atualizar o código-fonte Kotlin do seu app.

---

## 🔒 Segurança e Privacidade

-   **Zero Nuvem**: Todas as lógicas JavaScript (`run_js`) e prompts são processados no chip do aparelho.
-   **Secret Handling**: Usamos o campo `require-secret` para tokens e senhas, garantindo que nada sensível seja enviado para a janela de contexto da IA.
-   **Isolamento**: Cada WebView é sandboxed pelo Android, impedindo que uma skill acesse dados de outra.

---

## 📝 Licença e Contribuição

Este projeto está sob a licença MIT. Para reportar falhas de segurança ou propor melhorias:
1.  Abra uma Issue no GitHub.
2.  Descreva o comportamento esperado vs. o encontrado.

---
**Desenvolvido para Máxima Performance em AI Edge.**
