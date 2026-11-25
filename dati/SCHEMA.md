# Scheda Dati — Festival Segnale

## 1. Entità
Il modello dati del progetto è composto da due entità principali:
* **Evento**: rappresenta i singoli appuntamenti in programma durante il festival (incontri, laboratori e mostre).
* **Sede**: rappresenta i luoghi fisici della città di Torino che ospitano gli appuntamenti.

---

## 2. Campi delle entità

### Entità `Evento` (`eventi.json`)
| Campo | Tipo | Descrizione | Esempio |
| :--- | :--- | :--- | :--- |
| `id` | `number` (intero) | Identificativo univoco dell'evento | `1` |
| `titolo` | `string` | Titolo dell'appuntamento | `"Lettere in movimento"` |
| `data` | `string` (ISO 8601) | Data di svolgimento (`YYYY-MM-DD`) | `"2026-06-12"` |
| `orario` | `string` | Orario di inizio (`HH:MM`) | `"10:00"` |
| `categoria` | `string` | Tipologia di attività | `"Incontro"` |
| `descrizione` | `string` | Breve testo descrittivo dell'evento | `"Come cambia un messaggio quando cambiano le lettere? Un incontro su tipografia, ritmo e comunicazione visiva."` |
| `immagine` | `string` | Percorso relativo dell'illustrazione | `"assets/lettere-in-movimento.svg"` |
| `immagine_alt` | `string` | Testo alternativo per l'accessibilità | `"Lettere geometriche disposte su una griglia"` |
| `sede_id` | `number` (intero) | Chiave esterna che richiama `Sede.id` | `1` |

### Entità `Sede` (`sedi.json`)
| Campo | Tipo | Descrizione | Esempio |
| :--- | :--- | :--- | :--- |
| `id` | `number` (intero) | Identificativo univoco della sede | `1` |
| `nome` | `string` | Nome della sede del festival e riferimento reale | `"Officina Nord — Sede centrale"` |
| `indirizzo` | `string` | Indirizzo stradale completo | `"Corso Duca degli Abruzzi 24, Torino"` |

---

## 3. Chiavi primarie
* **`Evento.id`**: chiave primaria numerica, univoca all'interno di `eventi.json` e stabile nel tempo.
* **`Sede.id`**: chiave primaria numerica, univoca all'interno di `sedi.json` e stabile nel tempo.

---

## 4. Relazione
Tra **Sede** ed **Evento** intercorre una relazione **uno-a-molti (`1:N`)**:
* Una **Sede** può ospitare più eventi (nel progetto corrente, ogni sede ospita due appuntamenti).
* Ogni **Evento** si svolge in una sola sede.
* Il collegamento avviene tramite il campo **`Evento.sede_id`**, che fa riferimento alla chiave primaria **`Sede.id`**, evitando di duplicare nome e indirizzo della sede all'interno dei singoli record degli eventi.

---

## 5. Quantità
* **6 eventi** complessivi in `eventi.json` (`id` da `1` a `6`).
* **3 sedi** complessive in `sedi.json` (`id` da `1` a `3`).

---

## 6. Gestione e aggiornamento dei dati
* **Responsabile:** lo studente **Cristian**, autore del progetto didattico.
* **Modalità:** i dati vengono aggiornati modificando direttamente i file `eventi.json` e `sedi.json` nella repository GitHub; ad ogni commit e push sul branch principale, le modifiche vengono pubblicate automaticamente online tramite GitHub Pages.

---

## 7. Che cosa mostra la pagina
La pagina **`programma.html`** mostra l'elenco completo dei sei appuntamenti del festival organizzati in una griglia di schede (*card*). Per ciascun evento vengono visualizzati:
* l'illustrazione dedicata (con relativo testo alternativo);
* la data, l'orario e la categoria dell'appuntamento;
* il titolo e la descrizione dell'attività;
* il nome e i riferimenti della sede in cui si svolge l'evento, recuperati associando `Evento.sede_id` con `Sede.id`.

---

## Schema entità-relazione (Mermaid)

```mermaid
erDiagram
    SEDE ||--o{ EVENTO : "ospita"

    SEDE {
        number id PK "Chiave primaria"
        string nome