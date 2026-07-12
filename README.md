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

### Sincronizzazione tra dispositivi ☁️
Con il pulsante **☁️ Sync** il registro (foto comprese) viene salvato in
un repository GitHub privato e condiviso tra telefono, laptop e qualsiasi
altro dispositivo. Setup una tantum:

1. Crea un repository **privato** su [github.com/new](https://github.com/new),
   es. `trasloco-dati`
2. Genera un token: GitHub → Settings → Developer settings →
   **Fine-grained tokens** → Generate new token, con accesso al solo
   repository `trasloco-dati` e permesso **Contents: Read and write**
3. Nell'app, tocca **☁️ Sync** e incolla repository e token
   (su ogni dispositivo da collegare)

Da quel momento ogni modifica viene caricata automaticamente (pochi
secondi dopo) e scaricata all'apertura dell'app o al ritorno in primo
piano. Se modifichi da due dispositivi, vince la modifica più recente
per ciascuna scatola. Il chip ☁️ in alto mostra lo stato (✓ sincronizzato,
… in corso, ⚠️ errore).

### Condividi accesso con un link 📲
Per non riconfigurare ogni dispositivo a mano (e per farlo usare a
familiari senza competenze tecniche), il pulsante **📲 Condividi accesso**
genera un **link d'invito**: chi lo apre si ritrova l'app già configurata
(sincronizzazione + chiave AI), senza inserire nulla.

- Configura una volta il tuo dispositivo (Sync e, se vuoi, Chiave AI),
  poi tocca **Condividi accesso** → **Crea link d'invito** e mandalo
  (WhatsApp, ecc.) alle persone di fiducia.
- Il link contiene le credenziali codificate nella parte dopo `#`, che
  **non viene inviata ai server** e non finisce mai nel codice pubblico
  dell'app. All'apertura, il ricevente conferma e le credenziali vengono
  salvate solo sul suo dispositivo; l'indirizzo viene poi ripulito.
- **Attenzione**: chiunque abbia il link accede allo stesso registro e
  può modificarlo — condividilo solo con persone fidate e non pubblicarlo.
  Per revocare l'accesso, rigenera il token su GitHub (Settings →
  Developer settings) e ricondividi un nuovo link.

### Backup
I pulsanti **Esporta / Importa backup** salvano e ripristinano l'intero
registro (foto comprese) come file JSON: utile come copia di sicurezza
in aggiunta alla sincronizzazione.

## Pubblicazione (opzionale)

Il progetto è un singolo file statico: abilitando **GitHub Pages** sul
repository (Settings → Pages → deploy dal branch) l'app diventa
raggiungibile da qualsiasi dispositivo via URL. Ricorda che i dati restano
comunque locali a ciascun browser: usa il backup JSON per trasferirli.
