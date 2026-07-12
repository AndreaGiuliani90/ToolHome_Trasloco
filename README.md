# 📦 Registro Scatoloni — ToolHome Trasloco

Web app per tenere sotto controllo il trasloco: fotografi le etichette degli
scatoloni, costruisci il registro e assegni ogni scatola al piano di
destinazione della casa nuova.

## Come si usa

Apri `index.html` in un browser (funziona anche sul telefono). Non serve
alcun server né installazione: i dati restano salvati nel browser del
dispositivo (localStorage).

### Registro
- **＋ Scatola** — scatta o carica la foto dell'etichetta, poi compila
  indice/codice, nome e contenuto (oppure lascia fare all'AI, vedi sotto).
- **✨ Lettura AI dell'etichetta** — con una chiave API di Claude
  (Anthropic) l'app invia la foto dell'etichetta al modello, che compila
  automaticamente codice, nome, contenuto, flag fragile e destinazione
  (se scritta sull'etichetta). Funziona anche con la scrittura a mano.
  Setup: crea un account su [console.anthropic.com](https://console.anthropic.com),
  aggiungi un piccolo credito, genera una chiave in **API Keys** e
  incollala nel pulsante **🔑 Chiave AI** dell'app. La chiave resta
  salvata solo sul dispositivo; ogni lettura costa circa 1 centesimo.
  In alternativa il pulsante **OCR di base** prova a leggere il testo
  senza AI (gratis ma molto meno preciso, specie a mano libera).
- **🥃 Fragile** — attiva l'interruttore per le scatole delicate: la
  scatola viene marcata con il badge FRAGILE ovunque compaia.
- **Ricerca** — il campo in alto cerca in tempo reale tra codici, nomi e
  contenuti: scrivi «scolapasta» e trovi subito quale scatola lo contiene
  e a che piano è destinata.
- **Filtri** — per piano, solo fragili o ancora da assegnare.

### Destinazioni
Ogni scatola può essere assegnata a uno dei cinque livelli della casa nuova:

| Piano | Livello |
|---|---|
| 🍷 Taverna | piano semi-interrato |
| 🛋️ Piano Living | primo piano |
| 🛏️ Piano Camere | secondo piano |
| 🖥️ Piano Studio | terzo piano |
| 🪜 Sottotetto | mansarda |

### Vista Casa 🏠
La scheda **Casa** mostra la sezione della casa con i cinque piani: ogni
piano riporta il numero di scatole destinate (e quante fragili). Toccando
un piano si apre l'elenco delle sue scatole — perfetto il giorno del
trasloco per dirottare al volo ogni scatolone che arriva.

### Backup
I pulsanti **Esporta / Importa backup** salvano e ripristinano l'intero
registro (foto comprese) come file JSON: utile per passare i dati da un
dispositivo all'altro o per sicurezza.

## Pubblicazione (opzionale)

Il progetto è un singolo file statico: abilitando **GitHub Pages** sul
repository (Settings → Pages → deploy dal branch) l'app diventa
raggiungibile da qualsiasi dispositivo via URL. Ricorda che i dati restano
comunque locali a ciascun browser: usa il backup JSON per trasferirli.
