# 🎙️ Jarvis-One ESP32

**Jarvis-One** è un assistente vocale Open Source basato su **ESPHome** e **Home Assistant**. Grazie all'utilizzo di un ESP32 e un microfono I2S, permette di avere un controllo vocale completamente locale, garantendo privacy assoluta e tempi di risposta rapidi.

---

## ✨ Caratteristiche
* **Wake Word Locale:** Attivazione immediata tramite "Hey Jarvis" (elaborata direttamente sull'ESP32).
* **Privacy First:** Nessun audio viene inviato al cloud; tutto viene gestito dalla tua istanza di Home Assistant.
* **Feedback Visivo:** Utilizzo del LED di bordo (GPIO2) per indicare lo stato di ascolto e processamento.
* **Trascrizione in Tempo Reale:** Sensori di testo per visualizzare STT (Speech-to-Text) e TTS (Text-to-Speech) sulla dashboard di HA.
* **Stabilità:** Timer di sicurezza integrato per evitare il blocco del microfono.

---

## 🛠️ Hardware Necessario

| Componente | Modello Consigliato |
| :--- | :--- |
| **Microcontrollore** | ESP32 DevKit V1 |
| **Microfono** | INMP441 (I2S) |
| **LED & Button** | Integrati (GPIO2 e GPIO0) |
| **Case 3D** | Design di [@ImpatientMake_218274](https://www.printables.com/@ImpatientMake_218274) |

---

## 🔌 Schema di Collegamento (I2S)

| INMP441 Pin | ESP32 Pin | Descrizione |
| :--- | :--- | :--- |
| **VCC** | 3V3 | Alimentazione |
| **GND** | GND | Massa |
| **L/R** | GND | Selezione Canale (Sinistro) |
| **SD** | GPIO 33 | Serial Data |
| **WS** | GPIO 27 | Word Select |
| **SCK** | GPIO 14 | Serial Clock |

---

## 🚀 Installazione

1.  **Prerequisiti:** Assicurati di avere l'add-on **ESPHome** installato su Home Assistant e di aver configurato **Piper** (TTS) e **Whisper** (STT).
2.  **Configurazione:** Crea un nuovo dispositivo in ESPHome.
3.  **Secrets:** Compila il tuo file `secrets.yaml` con le credenziali della tua rete:
    ```yaml
    wifi_ssid: "TuaReteWiFi"
    wifi_password: "TuaPassword"
    ```
4.  **Codice:** Copia il contenuto del file `jarvis-one.yaml` nell'editor di ESPHome.
5.  **Flash:** Collega l'ESP32 al PC e clicca su **Install**.

---

## 📦 Case 3D
Il design estetico di Jarvis-One è fondamentale. I file STL per la stampa 3D sono stati realizzati da **@ImpatientMake_218274**. 
> [!TIP]
> Si consiglia di stampare in PETG o PLA con un riempimento del 15% per una protezione ottimale dei componenti.

---

## 🤝 Crediti & Ringraziamenti
* [ESPHome](https://esphome.io/) per il framework.
* [Home Assistant](https://www.home-assistant.io/) per l'ecosistema domotico.
* **@ImpatientMake_218274** per i modelli 3D del case.

---

## 📄 Licenza
Questo progetto è rilasciato sotto licenza MIT. Senti libero di modificarlo e migliorarlo!
