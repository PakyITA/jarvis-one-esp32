# 🎙️ Jarvis-One ESP32

**Jarvis-One** è un assistente vocale Open Source basato su **ESPHome** e **Home Assistant**.
Utilizza un **ESP32** e un microfono **I2S (INMP441)** per offrire controllo vocale **completamente locale**, con elevata affidabilità, privacy totale e bassa latenza.

Il progetto è ottimizzato per ESPHome **2026.x** e include meccanismi di stabilità per l’uso continuo e gli aggiornamenti OTA.

---

## ✨ Caratteristiche

- ✅ **Wake Word Locale**
  Attivazione tramite *"Hey Jarvis"* elaborata direttamente sull’ESP32.

- 🔐 **Privacy First**
  Nessun audio inviato al cloud. Tutta l’elaborazione avviene in Home Assistant.

- 💡 **Feedback Visivo**
  LED di stato (GPIO2) per indicare ascolto ed elaborazione.

- 📝 **Trascrizione in Tempo Reale**
  Sensori testuali per STT e TTS nella dashboard di Home Assistant.

- 📡 **OTA Affidabile**
  Supporto aggiornamenti wireless con fallback Wi-Fi di emergenza.

- 🛟 **Recovery Mode**
  Access Point automatico in caso di problemi di rete.

- ⚙️ **Audio Ottimizzato**
  Parametri calibrati per INMP441 (gain, noise suppression, volume).

- 🧠 **Gestione Intelligente del Timeout**
  Utilizzo del controllo interno ESPHome (senza timer manuali instabili).

---

## 🛠️ Hardware Necessario

| Componente | Modello Consigliato |
|-----------|---------------------|
| Microcontrollore | ESP32 DevKit V1 |
| Microfono | INMP441 (I2S) |
| LED | Integrato (GPIO2) |
| Pulsante | Integrato (GPIO0, opzionale) |
| Case 3D | Design di @ImpatientMake_218274 |

---

## 🔌 Schema di Collegamento (I2S)

| INMP441 Pin | ESP32 Pin | Descrizione |
|------------|-----------|-------------|
| VCC | 3V3 | Alimentazione |
| GND | GND | Massa |
| L/R | GND | Canale Sinistro |
| SD | GPIO33 | Serial Data |
| WS | GPIO27 | Word Select |
| SCK | GPIO14 | Serial Clock |

> ⚠️ Usare cavi corti (<10 cm) per ridurre interferenze.

---

## 🚀 Installazione

### 1️⃣ Prerequisiti

- Home Assistant aggiornato
- Add-on ESPHome
- Whisper (STT) configurato
- Piper (TTS) configurato
- Assist Pipeline attiva

---

### 2️⃣ Creazione Dispositivo

1. Apri ESPHome
2. Crea un nuovo dispositivo
3. Seleziona ESP32 DevKit

---

### 3️⃣ Configurazione Secrets

Nel file `secrets.yaml`:

```yaml
wifi_ssid: "NomeRete"
wifi_password: "PasswordRete"

api_encryption_key: "CHIAVE_API"

ota_password: "PASSWORD_OTA"

fallback_password: "PASSWORD_RECOVERY"
