# D&D Calendar

[![license](https://img.shields.io/badge/license-MIT-orange.svg)](LICENSE)

[English]
A lightweight web app to coordinate Dungeons & Dragons sessions: players share their availability by week or by month, the Master finds the common slots.

[Italiano]
*Web app leggera per coordinare le sessioni di Dungeons & Dragons: i giocatori condividono le disponibilità per settimana o per mese, il Master trova gli orari in comune.*

---

## Features / Funzionalità

- **Weekly availability** · *Disponibilità settimanale*
  Hour grid for the next week; one range can be copied to several weekdays at once.
  *Griglia oraria per la settimana successiva; una fascia si può copiare su più giorni in un colpo solo.*

- **Monthly availability** · *Disponibilità mensile*
  Day calendar for any upcoming month: several ranges per day, a shortcut for "every same weekday of the month", and removal of single ranges from the day dialog. It works alongside the weekly mode.
  *Calendario per qualsiasi mese futuro: più fasce per giorno, scorciatoia "tutti i [giorno] del mese" e rimozione delle singole fasce dalla finestra del giorno. Convive con la modalità settimanale.*

- **Bilingual interface** · *Interfaccia bilingue*
  Italian and English, switchable at runtime with the IT/EN selector (top right). The choice is remembered; the first time the browser language is used. Share codes do not depend on the language, so players can mix languages in the same group.
  *Italiano e inglese, con cambio lingua immediato dal selettore IT/EN in alto a destra. La scelta viene ricordata; la prima volta si usa la lingua del browser. I codici non dipendono dalla lingua, quindi i giocatori di uno stesso gruppo possono usare lingue diverse.*

- **No server, no account** · *Nessun server, nessun account*
  Availability travels as a share link or a text code; everything is stored in the browser.
  *La disponibilità viaggia come link o codice di testo; tutto è salvato nel browser.*

- **Master view** · *Vista del Master*
  Overlap of all codes with automatic time-zone conversion, partial matches and per-player details.
  *Incrocio di tutti i codici con conversione automatica dei fusi orari, incroci parziali e dettaglio per giocatore.*

- **PNG export** · *Esportazione PNG*
  The results (calendar included) can be downloaded as an image to share with the group.
  *I risultati (calendario incluso) si scaricano come immagine da condividere con il gruppo.*

- **Week code converter** · *Convertitore di codici settimanali*
  Reuse an old weekly code on a new week.
  *Riutilizza un vecchio codice settimanale su una nuova settimana.*

### Modes / Modalità

| Mode · *Modalità* | Player · *Giocatore* | Master |
|---|---|---|
| Weekly · *Settimanale* | Hour grid, multi-day copy · *Griglia oraria, copia su più giorni* | One expandable card per day · *Una scheda espandibile per giorno* |
| Monthly · *Mensile* | Day calendar, several ranges per day, same-weekday shortcut · *Calendario, più fasce per giorno, scorciatoia stesso giorno* | Summary, heat calendar and day details (below) · *Riepilogo, calendario a mappa di calore e dettaglio del giorno (sotto)* |

### Monthly results for the Master / Risultati mensili per il Master

- **Summary** · *Riepilogo*: full-group days grouped by identical time range (longest first), shown as clickable chips; if no day works for everyone, the best alternative (most players free at the same time).
  *Giorni con gruppo completo raggruppati per fascia identica (la più lunga per prima), mostrati come chip cliccabili; se nessun giorno va bene a tutti, la miglior alternativa (più giocatori liberi nello stesso momento).*
- **Heat calendar** · *Calendario a mappa di calore*: each day shows players free together / total; the more players, the stronger the colour; a green border marks the full group.
  *Ogni giorno mostra i giocatori liberi insieme sul totale; più giocatori, colore più intenso; il bordo verde indica il gruppo completo.*
- **Day details** · *Dettaglio del giorno*: tap a day or a chip to see common slots, best partial overlap and each player's ranges.
  *Tocca un giorno o un chip per vedere gli orari comuni, il miglior incrocio parziale e le fasce di ogni giocatore.*

---

## Usage / Utilizzo

0. **Language** · *Lingua*: pick **IT** or **EN** at the top right of the page. · *scegli **IT** o **EN** in alto a destra.*
1. **Players** · *Giocatori*: open the page, type a name, choose **Settimanale** or **Mensile**, click a day to add time ranges, then press **Invia Disponibilità** and send the link (or the text code) to the Master.
   *apri la pagina, scrivi un nome, scegli la modalità, clicca un giorno per aggiungere le fasce, poi premi **Invia Disponibilità** e manda il link (o il codice) al Master.*
2. **Master**: open the shared links, or paste the codes (one per line) in the Master screen and press **Incrocia Orari**. The Master view opens by tapping the title 7 times, with `Ctrl+Shift+M`, or by opening a shared link.
   *apri i link ricevuti, oppure incolla i codici (uno per riga) nello schermo del Master e premi **Incrocia Orari**. La vista del Master si apre toccando il titolo 7 volte, con `Ctrl+Shift+M`, oppure aprendo un link condiviso.*

Weekly and monthly codes cannot be mixed in the same calculation, and all monthly codes must refer to the same month.
*I codici settimanali e mensili non si possono mescolare nello stesso calcolo, e i codici mensili devono riferirsi allo stesso mese.*

## Tech Stack / Tecnologie

| Area | Technology · *Tecnologia* |
|---|---|
| App | Single-file HTML + CSS + vanilla JavaScript (no build step) |
| Image export | [html2canvas](https://html2canvas.hertzen.com/) 1.4.1 from cdnjs |
| Storage | Browser `localStorage` only |
| Hosting | Any static host, e.g. GitHub Pages |

## Architecture / Architettura

```
DnD_Calendar/
├── index.html     UI, styles and the whole application logic
├── Dnd_Logo.png   Logo and favicon
├── README.md
└── LICENSE
```

The script of `index.html` is documented with JSDoc and organised in 10 sections · *Lo script di `index.html` è documentato con JSDoc e organizzato in 10 sezioni*:

| # | Section · *Sezione* |
|---|---|
| 1 | Constants, state, localization and generic helpers · *Costanti, stato, localizzazione e utilità* |
| 2 | Startup and Master view switching · *Avvio e cambio vista Master* |
| 3 | Persistence · *Salvataggio* |
| 4 | Weekly calendar · *Calendario settimanale* |
| 5 | Event modal and time selectors · *Finestra eventi e selettori orari* |
| 6 | Monthly calendar · *Calendario mensile* |
| 7 | Export of player data · *Esportazione dei dati del giocatore* |
| 8 | Master: availability computation and results · *Master: calcolo e risultati* |
| 9 | Master: image export · *Master: esportazione immagine* |
| 10 | Week code converter · *Convertitore codici settimanali* |

### Share code format / Formato del codice

`Base64( encodeURIComponent( JSON ) )`, where the JSON is · *dove il JSON è*:

| Field · *Campo* | Mode · *Modalità* | Meaning · *Significato* |
|---|---|---|
| `n` | both | Player name · *Nome del giocatore* |
| `e` | both | Availability: 7 arrays (week) or a `{ "YYYY-MM-DD": ranges }` map (month) · *Disponibilità* |
| `d` | week | Localized dates of the week · *Date della settimana* |
| `m` | month | Month, `YYYY-MM` · *Mese* |
| `tz` | both | Player's `getTimezoneOffset()` in minutes · *Fuso orario del giocatore* |

A range is `{ start, end }` in minutes from midnight (0–1440). Codes generated by earlier versions keep working.
*Una fascia è `{ start, end }` in minuti da mezzanotte (0–1440). I codici generati dalle versioni precedenti continuano a funzionare.*

## Deployment / Pubblicazione

The app is static: open `index.html` locally or publish the repository with **GitHub Pages** (Settings → Pages → branch `main`, folder `/ (root)`).
*L'app è statica: apri `index.html` in locale oppure pubblica la repository con **GitHub Pages** (Settings → Pages → branch `main`, cartella `/ (root)`).*

## Privacy & Security / Privacy e sicurezza

- Everything runs in the browser; there is no backend and no tracking. Data lives in `localStorage` and inside the codes players choose to share.
  *Tutto gira nel browser; non c'è backend né tracciamento. I dati stanno in `localStorage` e nei codici che i giocatori scelgono di condividere.*
- No secrets, keys or credentials are present in the code.
  *Nel codice non ci sono segreti, chiavi o credenziali.*
- Player names and dates read from pasted codes are HTML-escaped before being displayed, so a crafted code cannot inject markup into the Master view.
  *I nomi e le date letti dai codici incollati vengono protetti prima di essere mostrati, così un codice costruito ad arte non può iniettare HTML nella vista del Master.*

## License / Licenza

Source code released under the [MIT License](LICENSE).
*Codice sorgente rilasciato sotto licenza [MIT](LICENSE).*