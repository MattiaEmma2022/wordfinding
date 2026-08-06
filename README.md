# Nomi, Cose e Città — Multiplayer online

Versione online del gioco: crea una stanza, condividi il codice a 4 caratteri
con altri giocatori, e giocate tutti insieme con la stessa lettera e lo stesso
timer di 60 secondi, ognuno dal proprio telefono/computer.

## Come funziona

- **Crea stanza**: genera un codice (es. `AB3F`) e ti metti in attesa in una lobby.
- **Entra con un codice**: gli altri giocatori inseriscono nome + codice per entrare nella stessa stanza.
- **Host**: chi crea la stanza è l'host e può premere "Inizia round" / "Prossimo round". Gli altri vedono "in attesa".
- **Round**: a tutti viene mostrata la stessa lettera e lo stesso countdown di 60 secondi (sincronizzato tramite Firebase). Ognuno scrive le proprie 6 risposte sul proprio schermo — non si vedono le risposte degli altri finché il round non finisce.
- **STOP**: chiunque può premere "STOP! Ho finito" per terminare il round in anticipo per tutti (come nel gioco da tavolo).
- **Punteggio**: a fine round si vede una tabella con le risposte di tutti. Regola: risposta assente o che non inizia con la lettera giusta = 0 punti; risposta valida e unica = 10 punti; risposta valida ma scritta anche da un altro giocatore = 5 punti (regola classica di "Nomi Cose e Città"). La classifica è cumulativa round dopo round.

## Passo 1 — Crea un progetto Firebase (gratis, 5 minuti)

Serve per sincronizzare in tempo reale lettera, timer e risposte tra i giocatori.

1. Vai su https://console.firebase.google.com e accedi con un account Google.
2. Clicca **"Aggiungi progetto"**, dagli un nome (es. "nomi-cose-citta"), continua senza attivare Google Analytics (non serve).
3. Nel menu a sinistra vai su **Build → Realtime Database**.
4. Clicca **"Crea database"**. Scegli una posizione (va bene quella predefinita) e **"Avvia in modalità test"** (permette letture/scritture per 30 giorni: per la v1 va bene, vedi nota sicurezza sotto).
5. Vai su **Impostazioni progetto** (icona ingranaggio in alto a sinistra) → scheda **"Generali"** → sezione **"Le tue app"** → clicca l'icona **`</>`** (Web) per registrare una nuova app web.
6. Dagli un nome (es. "gioco-web") e clicca **"Registra app"**. Non serve configurare Firebase Hosting.
7. Copia i valori mostrati nell'oggetto `firebaseConfig` (apiKey, authDomain, databaseURL, projectId, storageBucket, messagingSenderId, appId).
8. Apri il file **`firebase-config.js`** di questo progetto e sostituisci ogni `"INSERISCI_QUI"` con il valore corrispondente copiato da Firebase. Salva.

### Nota sicurezza (importante ma non urgente per giocare con amici)

La modalità test lascia il database aperto in lettura/scrittura a chiunque conosca l'URL per 30 giorni, poi si blocca automaticamente. Per un gioco casual va benissimo. Se vuoi regole più permanenti e leggermente più sicure, vai su **Realtime Database → Regole** e incolla il contenuto del file `database.rules.json` incluso in questo progetto, poi clicca **"Pubblica"**.

## Passo 2 — Metti il progetto online con GitHub Pages (gratis)

1. Vai su https://github.com e crea un account se non ne hai già uno.
2. Clicca **"New repository"**, dagli un nome (es. `nomi-cose-citta`), lascialo **pubblico**, poi **"Create repository"**.
3. Nella pagina del repository clicca **"uploading an existing file"** (o "Add file → Upload files") e carica questi 3 file: `index.html`, `firebase-config.js` (già con i tuoi dati Firebase inseriti), `database.rules.json`. Poi **"Commit changes"**.
4. Vai su **Settings → Pages** (menu a sinistra del repository).
5. In **"Build and deployment" → Source** scegli **"Deploy from a branch"**, poi in **Branch** scegli `main` e cartella `/ (root)`, clicca **Save**.
6. Dopo 1-2 minuti la pagina mostrerà un link tipo `https://tuonomeutente.github.io/nomi-cose-citta/` — quello è il link pubblico da condividere con chi vuole giocare!

## Come testare con più giocatori

- Apri il link su due dispositivi diversi (o due schede del browser in incognito, per simulare due persone).
- Sulla prima crea una stanza e nota il codice.
- Sulla seconda inserisci un nome ed entra con quel codice.
- L'host preme "Inizia round" e da quel momento entrambi vedono la stessa lettera e lo stesso timer.

## Limiti noti di questa v1 (miglioramenti futuri possibili)

- Le stanze non vengono mai eliminate automaticamente (restano nel database). Per un uso intenso si potrebbe aggiungere una pulizia periodica.
- Non c'è un controllo che la parola scritta esista davvero (es. potresti scrivere una città inventata) — la validazione è solo "inizia con la lettera giusta".
- Se un giocatore chiude la pagina a metà round, il suo nome resta nella stanza (non c'è ancora rilevamento di disconnessione).
- Le regole del database in modalità test scadono dopo 30 giorni: dopo quella data smetterà di funzionare finché non aggiorni le regole (vedi nota sicurezza sopra).
-Rendere visuals piu efficaci
-Assicurarsi che funzioni
