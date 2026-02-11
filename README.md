# 🎙️ Jarvis-One ESP32

**Jarvis-One** è un assistente vocale Open Source basato su **ESPHome** e **Home Assistant**.
Utilizza un **ESP32** e un microfono **I2S (INMP441)** per offrire un sistema di controllo vocale **completamente locale**, stabile, veloce e rispettoso della privacy.

Il progetto è ottimizzato per **ESPHome 2026.x** e include meccanismi avanzati per stabilità, aggiornamenti OTA e recovery.

---

## ✨ Caratteristiche

- ✅ **Wake Word Locale**  
  Attivazione tramite *"Hey Jarvis"* elaborata direttamente sull’ESP32.

- 🔐 **Privacy First**  
  Nessun audio inviato al cloud. Tutto viene gestito in Home Assistant.

- 💡 **Feedback Visivo**  
  LED di stato per indicare ascolto ed elaborazione.

- 📝 **Trascrizione in Tempo Reale**  
  Visualizzazione STT e TTS nella dashboard.

- 📡 **OTA Stabile**  
  Aggiornamenti wireless affidabili.

- 🛟 **Recovery Mode Wi-Fi**  
  Access point automatico in caso di problemi di rete.

- ⚙️ **Audio Ottimizzato**  
  Parametri calibrati per INMP441.

- 🧠 **Gestione Intelligente Timeout**  
  Basata sul sistema interno ESPHome (senza timer manuali instabili).

---

## 🛠️ Hardware Necessario

| Componente | Modello |
|------------|----------|
| Microcontrollore | ESP32 DevKit V1 |
| Microfono | INMP441 (I2S) |
| LED | GPIO2 (integrato) |
| Pulsante | GPIO0 (opzionale) |
| Case | 3D Print |

---

## 🔌 Schema di Collegamento (INMP441 → ESP32)

| INMP441 | ESP32 | Funzione |
|---------|--------|----------|
| VCC | 3V3 | Alimentazione |
| GND | GND | Massa |
| L/R | GND | Canale Sinistro |
| SD | GPIO33 | Dati |
| WS | GPIO27 | Word Select |
| SCK | GPIO14 | Clock |

> ⚠️ Usare cavi corti (<10 cm) per ridurre disturbi.

---

## 🚀 Installazione

### 1️⃣ Prerequisiti

- Home Assistant aggiornato
- Add-on ESPHome
- Whisper (STT)
- Piper (TTS)
- Assist Pipeline configurata

---

### 2️⃣ Creazione Dispositivo

1. Apri ESPHome
2. Crea nuovo dispositivo
3. Seleziona ESP32 DevKit

---

### 3️⃣ Configurazione `secrets.yaml`

Nel file `secrets.yaml`:

```yaml
wifi_ssid: "NomeRete"
wifi_password: "PasswordRete"

api_encryption_key: "CHIAVE_API"

ota_password: "PASSWORD_OTA"

fallback_password: "PASSWORD_RECOVERY"
---

### 4️⃣ Codice

Copia il contenuto del file:

voice-assistant-esp32.yaml


all’interno dell’editor ESPHome per il dispositivo creato.

Assicurati di aver configurato correttamente il file `secrets.yaml` prima della compilazione.

---

### 5️⃣ Primo Flash

Collega l’ESP32 al computer tramite USB e seleziona:

Install → Plug into this computer


Questo primo flash è fondamentale per inizializzare correttamente il dispositivo.

Dopo il completamento, l’ESP32 si connetterà automaticamente alla rete Wi-Fi.

---

## 📡 Aggiornamenti OTA

Dopo l’installazione iniziale, il dispositivo supporta aggiornamenti wireless (OTA).

Per aggiornare:

ESPHome → Install → Wireless OTA


Oppure:

Install → Enter IP manually


inserendo l’indirizzo IP corrente.

---

### 🛟 Recovery Mode

In caso di problemi di rete, l’ESP32 attiva automaticamente un Access Point:

SSID: ESP32-Voice-Recovery


Connettendoti a questa rete potrai riconfigurare il dispositivo.

---

## 📊 Monitoraggio e Debug

Il sistema espone automaticamente diverse entità in Home Assistant per il debug:

text_sensor.esp32_ip_address
text_sensor.voice_assistant_state
text_sensor.jarvis_user_text
text_sensor.jarvis_ai_text


Queste permettono di:

- verificare lo stato dell’assistente
- controllare l’indirizzo IP
- monitorare STT e TTS
- analizzare eventuali problemi

---

## 📦 Case 3D

I file per la stampa del case sono inclusi nel repository.

- 📁 Cartella: `/stampa case 3D`
- 👤 Designer: @ImpatientMake_218274
- 🌐 Link: https://www.printables.com/@ImpatientMake_218274

Si consiglia di stampare con PLA+ o PETG per una maggiore stabilità.

> 💡 Posizionare il foro del microfono verso l’esterno per migliorare la qualità audio.

---

## 🧪 Parametri Audio Consigliati

Configurazione testata per INMP441:

| Parametro | Valore |
|-----------|---------|
| Gain | 3 |
| Auto Gain | 15 dBFS |
| Noise Suppression | 1 |
| Volume | 2.5 |

Questi valori garantiscono:

- buona sensibilità
- basso rumore
- assenza di clipping
- riconoscimento stabile

---

## 🛠️ Troubleshooting

### ❌ OTA non funziona

Verifica la connessione:

```bash
ping jarvis-one.local
Oppure usa l’IP diretto:
Install → Enter IP manually
❌ Frasi tagliate
Verifica che non siano presenti timer manuali

Riduci noise_suppression

Aumenta volume_multiplier

❌ Microfono poco sensibile
Controlla l’orientamento del microfono

Verifica L/R su GND

Aumenta mic_gain_factor

❌ Boot instabile
Usa alimentatori affidabili

Evita cavi USB lunghi

Non sovraccaricare GPIO0/GPIO2

🤝 Contribuire
Contributi, segnalazioni e miglioramenti sono benvenuti.

Linee guida:

Testare su ESPHome 2026.x

Documentare le modifiche

Allegare log di debug

Mantenere compatibilità hardware

🙏 Crediti & Ringraziamenti
Un ringraziamento speciale a:

🔧 ESPHome

🏠 Home Assistant

🧠 Whisper (OpenAI)

🔊 Piper TTS

🖨️ @ImpatientMake_218274
Creatore dei file STL del case 3D
https://www.printables.com/@ImpatientMake_218274

Grazie a tutti per il contributo alla community Open Source 💙
