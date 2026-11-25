## Sessione 1

### 1. Completamento dei file dati JSON (`sedi.json` ed `eventi.json`)
* **Che cosa ho chiesto:** Come strutturare e completare i file `sedi.json` ed `eventi.json` con le altre due sedi e i quattro eventi mancanti presi da `programma.html` e `info.html`, collegandoli tramite la chiave esterna `sede_id`.
* **Che cosa mi hai proposto:** Le istruzioni su come associare gli identificativi tra i due file e gli esempi completi per strutturare 3 sedi (`id` 1–3 in `sedi.json`) e 6 eventi (`id` 1–6 in `eventi.json`), mantenendo nome e indirizzo delle sedi solo in `sedi.json`.
* **Che cosa ho usato, modificato o scartato:** Ho seguito le indicazioni per completare i due file JSON e li ho salvati all'interno di una sottocartella dedicata chiamata `dati/` (`dati/sedi.json` e `dati/eventi.json`).
* **Come ho verificato:** Controllo visivo della sintassi e della coerenza tra gli `id` delle sedi e i campi `sede_id` degli eventi.

--- 

### 2. Redazione della scheda dati e diagramma ER in `SCHEMA.md`
* **Che cosa ho chiesto:** Come impostare il file `SCHEMA.md` con entità, campi, chiavi primarie, relazione 1:N, quantità, modalità di aggiornamento, funzionamento della pagina e uno schema grafico in Mermaid.
* **Che cosa mi hai proposto:** Dopo aver chiesto conferma su chi aggiorna i dati (lo studente Cristian) e quale pagina descrivere (`programma.html`), mi hai spiegato come organizzare la documentazione in Markdown e come funziona la sintassi `erDiagram` di Mermaid per rappresentare la relazione uno-a-molti.
* **Che cosa ho usato, modificato o scartato:** Ho redatto la scheda e inserito il diagramma Mermaid nel file `SCHEMA.md` della repository.
* **Come ho verificato:** Verifica della leggibilità del file Markdown e del rendering automatico del grafico entità-relazione su GitHub.

---

### 3. Caricamento dinamico del programma tramite `fetch` (`programma.html`)
* **Che cosa ho chiesto:** Come sostituire le sei schede evento statiche in `programma.html` con il caricamento dinamico via `fetch` dai due JSON, gestendo messaggio di caricamento, elenco vuoto, errori di lettura e fallback «Sede da definire» per `sede_id` errati.
* **Che cosa mi hai proposto:** Le istruzioni su come rimuovere le `<article>` scritte a mano in `programma.html` e come implementare uno script asincrono con `Promise.all` che legge i due file JSON, incrocia i dati delle sedi tramite `Map` e costruisce dinamicamente le card nel DOM conservando le classi CSS esistenti.
* **Che cosa ho usato, modificato o scartato:** Ho implementato la struttura HTML e lo script JavaScript seguendo le tue indicazioni, adattando i percorsi delle chiamate `fetch` per puntare alla cartella `dati/` (`dati/eventi.json` e `dati/sedi.json`).
* **Come ho verificato:** Test nel browser tramite server locale controllando la comparsa delle 6 schede evento, l'associazione corretta con le sedi e i messaggi di stato.

---

### 4. Integrazione API meteo Open-Meteo (`info.html`)
* **Che cosa ho chiesto:** Come integrare in `info.html` la sezione «Meteo a Torino adesso» interrogando via `fetch` l'API pubblica di Open-Meteo per mostrare temperatura, vento e ora del rilevamento, con attribuzione della fonte e gestione non bloccante degli errori.
* **Che cosa mi hai proposto:** Le istruzioni su come strutturare il blocco HTML nello stile del sito e come implementare la funzione `fetch` per leggere i campi `current` e `current_units` del JSON restituito dall'API, formattare data e ora, chiarire che non si tratta delle previsioni per il festival e citare Open-Meteo con licenza CC BY 4.0.
* **Che cosa ho usato, modificato o scartato:** Ho implementato la sezione e lo script in `info.html` utilizzando il contenitore `.event-card` e mantenendo il doppio collegamento alla fonte (`Open-Meteo` e `CC BY 4.0`). Ho chiesto conferma sul funzionamento del link alla licenza Creative Commons, mantenendo il collegamento diretto al testo ufficiale `https://creativecommons.org/licenses/by/4.0/`[cite: 12].
* **Come ho verificato:** Apertura di `info.html` nel browser per verificare il caricamento in tempo reale di temperatura, vento e ora di rilevamento, oltre al funzionamento dei link esterni[cite: 12].

---

### Problemi riscontrati e soluzioni
* **Errore di caricamento degli appuntamenti (`Impossibile caricare il programma` / caricamento bloccato):**
  * *Causa:* Lo script cercava `eventi.json` e `sedi.json` nella cartella principale allo stesso livello di `programma.html`, mentre i file erano stati salvati nella sottocartella `dati/`.
  * *Soluzione:* Seguendo le tue indicazioni, ho aggiornato gli URL nelle chiamate `fetch` in `fetch('dati/eventi.json')` e `fetch('dati/sedi.json')`, mantenendo invariati i percorsi relativi delle immagini verso `assets/`.
* **Dubbio sul link alla licenza Creative Commons nell'attribuzione meteo:**
  * *Causa:* Incertezza se collegare la licenza CC BY 4.0 a una pagina interna di Open-Meteo o al sito Creative Commons.
  * *Soluzione:* Chiarito che mantenere due link distinti (uno verso `https://open-meteo.com/` per la fonte e uno verso `https://creativecommons.org/licenses/by/4.0/` per il testo legale della licenza) è la pratica standard più corretta[cite: 12].