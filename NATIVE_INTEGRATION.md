# Guia de Integração Nativa (Android)

Para que as novas skills nativas (`send-whatsapp` e `smart-alarm`) funcionem, você deve modificar o código-fonte do aplicativo **AI Edge Gallery** no Android Studio.

## Arquivo Alvo
Localize o seguinte arquivo no projeto:
`Android/src/app/src/main/java/com/google/ai/edge/gallery/customtasks/agentchat/IntentHandler.kt`

## Instruções de Modificação

### 1. Adicionar os casos ao `when`
Dentro do método `handleIntent`, adicione os novos blocos para tratar `send_whatsapp` e `set_alarm`.

```kotlin
// ... importações originais ...
import android.content.Intent
import android.provider.AlarmClock
import android.net.Uri

// Localize o bloco 'when (intentName)' e adicione:

"send_whatsapp" -> {
    val phone = params.optString("phone")
    val text = params.optString("text")
    val intent = Intent(Intent.ACTION_VIEW).apply {
        data = Uri.parse("https://api.whatsapp.com/send?phone=$phone&text=$text")
        addFlags(Intent.FLAG_ACTIVITY_NEW_TASK)
    }
    context.startActivity(intent)
    "WhatsApp opened for $phone"
}

"set_alarm" -> {
    val hour = params.optInt("hour")
    val minutes = params.optInt("minutes")
    val message = params.optString("message")
    val skipUi = params.optBoolean("skip_ui", true)

    val intent = Intent(AlarmClock.ACTION_SET_ALARM).apply {
        putExtra(AlarmClock.EXTRA_HOUR, hour)
        putExtra(AlarmClock.EXTRA_MINUTES, minutes)
        putExtra(AlarmClock.EXTRA_MESSAGE, message)
        putExtra(AlarmClock.EXTRA_SKIP_UI, skipUi)
        addFlags(Intent.FLAG_ACTIVITY_NEW_TASK)
    }
    context.startActivity(intent)
    "Alarm set for $hour:$minutes"
}

"set_timer" -> {
    val seconds = params.optInt("seconds")
    val message = params.optString("message")
    val skipUi = params.optBoolean("skip_ui", true)

    val intent = Intent(AlarmClock.ACTION_SET_TIMER).apply {
        putExtra(AlarmClock.EXTRA_LENGTH, seconds)
        putExtra(AlarmClock.EXTRA_MESSAGE, message)
        putExtra(AlarmClock.EXTRA_SKIP_UI, skipUi)
        addFlags(Intent.FLAG_ACTIVITY_NEW_TASK)
    }
    context.startActivity(intent)
    "Timer set for $seconds seconds"
}
```

### 2. Verificar Permissões
Certifique-se de que o seu `AndroidManifest.xml` possui as permissões necessárias:

```xml
<uses-permission android:name="com.android.alarm.permission.SET_ALARM" />
```

## Resumo dos Parâmetros (Gemma 4 -> Native)
| Skill | Intent Name | Campo JSON | Tipo |
|---|---|---|---|
| WhatsApp | `send_whatsapp` | `phone` | String (E.164) |
| WhatsApp | `send_whatsapp` | `text` | String |
| Alarm | `set_alarm` | `hour` | Int (0-23) |
| Alarm | `set_alarm` | `minutes` | Int (0-59) |
| Timer | `set_timer` | `seconds` | Int |
