<p align="center">
  <img src="images/logo.png" alt="Jarvis One Logo" width="200">
</p>

# 🎙️ Jarvis-One ESP32

**Jarvis-One** è un assistente vocale Open Source basato su **ESPHome** e **Home Assistant**.  
Utilizza un **ESP32** e un microfono **I2S (INMP441)** per offrire un sistema di controllo vocale **completamente locale**, stabile, veloce e rispettoso della privacy.

Il progetto è ottimizzato per **ESPHome 2026.x** e include meccanismi avanzati per stabilità, aggiornamenti OTA e recovery.

---

## ✨ Caratteristiche

- ✅ **Wake Word Locale**: Attivazione tramite *"Hey Jarvis"* elaborata direttamente sull’ESP32.
- 🔐 **Privacy First**: Nessun audio inviato al cloud. Tutto viene gestito in Home Assistant.
- 💡 **Feedback Visivo**: LED di stato per indicare ascolto ed elaborazione.
- 📝 **Trascrizione in Tempo Reale**: Visualizzazione STT e TTS nella dashboard.
- 📡 **OTA Stabile**: Aggiornamenti wireless affidabili.
- 🛟 **Recovery Mode Wi-Fi**: Access point automatico in caso di problemi di rete.
- ⚙️ **Audio Ottimizzato**: Parametri calibrati per INMP441.
- 🧠 **Gestione Intelligente Timeout**: Basata sul sistema interno ESPHome.

---

## 🖥️ Dashboard & Interfaccia
Ecco come si presenta l'interfaccia di controllo di Jarvis One in Home Assistant:

<p align="center">
  <img src="images/dashboard.png" alt="Dashboard Jarvis One" width="600">
</p>

---

## 🛠️ Hardware Necessario

| Componente | Modello |
| :--- | :--- |
| **Microcontrollore** | ESP32 DevKit V1 |
| **Microfono** | INMP441 (I2S) |
| **LED** | GPIO2 (integrato) |
| **Pulsante** | GPIO0 (opzionale) |
| **Case** | 3D Print |

---

## 🔌 Schema di Collegamento (INMP441 → ESP32)

| INMP441 | ESP32 | Funzione |
| :--- | :--- | :--- |
| **VCC** | 3V3 | Alimentazione |
| **GND** | GND | Massa |
| **L/R** | GND | Canale Sinistro |
| **SD** | GPIO33 | Dati |
| **WS** | GPIO27 | Word Select |
| **SCK** | GPIO14 | Clock |

> ⚠️ **Attenzione:** Usare cavi corti (<10 cm) per ridurre i disturbi audio.

---

## 🚀 Installazione

### 1️⃣ Prerequisiti
- Home Assistant aggiornato
- Add-on ESPHome
- Whisper (STT)
- Piper (TTS)
- Assist Pipeline configurata

### 2️⃣ Creazione Dispositivo
1. Apri la dashboard di ESPHome.
2. Crea un nuovo dispositivo.
3. Seleziona **ESP32 DevKit**.

### 3️⃣ Configurazione `secrets.yaml`
Nel file `secrets.yaml` aggiungi le tue credenziali:
```yaml
wifi_ssid: "NomeRete"
wifi_password: "PasswordRete"
api_encryption_key: "TUA_CHIAVE_API"
ota_password: "TUA_PASSWORD_OTA"
fallback_password: "TUA_PASSWORD_RECOVERY".
```
### 4️⃣ Codice

Copia il contenuto del file `voice-assistant-esp32.yaml` all'interno dell'editor ESPHome.

### 5️⃣ Primo Flash

Collega l’ESP32 via USB e clicca **Install** → **Plug into this computer**.

----------

## 📡 Aggiornamenti OTA

-   **Wireless:** `ESPHome` → `Install` → `Wireless OTA`.
    
-   **Manuale:** `Install` → `Enter IP manually`.
    

### 🛟 Recovery Mode

Se il Wi-Fi fallisce, cerca la rete: `ESP32-Voice-Recovery`.

----------

## 📊 Monitoraggio e Debug

Entità disponibili in Home Assistant:

-   `text_sensor.esp32_ip_address`
    
-   `text_sensor.voice_assistant_state`
    
-   `text_sensor.jarvis_user_text`
    

----------

## 📦 Case 3D

-   📁 **Cartella:** `/stampa case 3D`
    
-   🌐 **Link:** [Printables](https://www.printables.com/@ImpatientMake_218274)
    

----------

## 🧪 Parametri Audio Consigliati

**Parametro**

**Valore**

**Gain**

3

**Auto Gain**

15 dBFS

**Noise Suppression**

1

**Volume**

2.5

----------

## 🛠️ Troubleshooting

-   **OTA fallisce:** Prova `ping jarvis-one.local`.
    
-   **Microfono sordo:** Controlla il pin **L/R** su **GND**.
    
-   **Alimentazione:** Usa un caricabatterie da almeno 1A (no porte USB del PC vecchie).
    

----------

## 🙏 Crediti

-   🔧 **ESPHome** & **Home Assistant**
    
-   🖨️ **@ImpatientMake_218274** per il case.
    

----------

**Sviluppato con ❤️ per la community.**





