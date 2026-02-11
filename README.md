# 🎙️ Jarvis-One ESP32
Assistente vocale Open Source basato su **ESPHome** e **Home Assistant**. Utilizza un ESP32 e un microfono I2S per il controllo vocale locale e privato.

## 🛠️ Hardware Necessario
* **Microcontrollore:** ESP32 DevKit V1
* **Microfono:** INMP441 (I2S)
* **LED & Button:** Integrati nella scheda (GPIO2 e GPIO0)

## 🔌 Schema di Collegamento
| INMP441 | ESP32 Pin |
| :--- | :--- |
| **VCC** | 3V3 |
| **GND** | GND |
| **L/R** | GND |
| **SD** | GPIO 33 |
| **WS** | GPIO 27 |
| **SCK** | GPIO 14 |

## 🚀 Installazione
1.  Assicurati di avere **ESPHome** installato nel tuo Home Assistant.
2.  Crea un file `secrets.yaml` nel tuo ESPHome con le tue credenziali (SSID, password, api_key).
3.  Copia il contenuto di `jarvis-one.yaml` in un nuovo dispositivo.
4.  Installa e goditi il tuo Jarvis!

## ✨ Caratteristiche
- Wake Word locale: "Hey Jarvis"
- Feedback visivo tramite LED di bordo.
- Sensori di testo per visualizzare la trascrizione (STT) e la risposta (TTS) sulla dashboard di HA.
- Timer di sicurezza per evitare blocchi dell'ascolto.
