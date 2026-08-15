# 🎲 Nomi, Cose e Città

La versione online del classico gioco da tavolo: stessa lettera, stesso
countdown di 60 secondi per tutti, ognuno risponde dal proprio telefono o
computer.

## Gioca subito

👉 **https://mattiaemma2022.github.io/wordfinding/**

1. Una persona apre il link, sceglie il proprio nome e clicca **"Crea una
   nuova stanza"**: ottiene un codice a 4 caratteri (es. `AB3F`).
2. Le altre aprono lo stesso link, inseriscono il proprio nome ed entrano
   con quel codice.
3. L'host preme **"Inizia round"**: a tutti compare la stessa lettera e lo
   stesso countdown, sincronizzati in tempo reale.

## Come funziona

- **Round**: 60 secondi per scrivere una risposta a testa per ogni
  categoria, tutte con la stessa lettera. Le risposte degli altri restano
  nascoste finché il round non finisce.
- **STOP**: chiunque può premere "STOP! Ho finito" per chiudere il round in
  anticipo per tutti, come nel gioco da tavolo.
- **Revisione categoria per categoria**: a fine round le risposte si
  rivelano una categoria alla volta, non tutte insieme — come quando si
  legge ad alta voce intorno al tavolo. L'host passa alla categoria
  successiva quando è pronto e può tornare indietro se serve.
- **Punteggio**: risposta assente o che non inizia con la lettera giusta =
  0 punti; valida e unica = 10 punti; valida ma scritta anche da un altro
  giocatore = 5 punti (regola classica). Non c'è un dizionario automatico:
  è l'host a giudicare — toccando una risposta durante la revisione la si
  forza valida o non valida per i casi dubbi. Il punteggio si blocca
  quando l'host passa al round successivo.
- **Lingua**: Italiano o Inglese, si sceglie in home prima di creare la
  stanza. Chi entra con un codice vede automaticamente la lingua scelta
  dall'host.
- **Categorie personalizzate**: l'host può modificare, aggiungere (fino a
  10) o togliere (minimo 2) le categorie prima di creare la stanza. Di
  base sono Nome, Città, Paese, Cosa, Animale, Fiume (o l'equivalente
  inglese).
- **Classifica**: cumulativa, round dopo round, finché la stanza resta
  aperta.

## Da sapere

- Le stanze non vengono mai eliminate automaticamente: se una resta
  inutilizzata semplicemente non la userà più nessuno.
- Se un giocatore chiude la pagina a metà round, il suo nome resta nella
  lista finché non si aggiorna la pagina (non c'è ancora rilevamento
  automatico di disconnessione).
- Se il gioco smette improvvisamente di sincronizzarsi tra i giocatori
  (lettera/timer/risposte che non si aggiornano per nessuno), il motivo
  più probabile sono le regole del database Firebase in modalità test, che
  scadono periodicamente: vai su Firebase → Realtime Database → Regole e
  incolla di nuovo il contenuto di `database.rules.json`, poi pubblica.
