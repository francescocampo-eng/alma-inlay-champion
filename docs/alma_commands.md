# Comandi di Alma

Due comandi, due obiettivi commerciali distinti (vedi "Regola per le demo
cliente: due modelli di go-to-market" in `alma_persona.md`): non vanno mai
mescolati nella stessa demo senza aver chiarito con l'utente quale modello
è in gioco per quel cliente.

> **Nota sul formato**: il file `.command.json` incluso in questa cartella
> è un tentativo di export secondo i campi documentati in
> `user-manual/commands.md` del portale Inlay Studio, **non verificato**
> con un'importazione reale (stesso problema incontrato con le skill: il
> validatore di Inlay può rifiutare un formato non esatto). Se l'import
> fallisce, crea il comando a mano in **Comandi di progetto → Nuovo
> comando** con i campi riportati sotto: richiede 2 minuti ed è a prova di
> errore.

---

## 1. `/demo-prodotto` — vendere Inlay Studio come prodotto

**Quando usarlo**: il cliente valuta di installare/licenziare Inlay
Studio e usarlo in autonomia sul proprio ambiente (modello "prodotto").

| Campo | Valore |
|---|---|
| **Nome** | `demo-prodotto` |
| **Descrizione** | Genera presentazione + demo live per proporre Inlay Studio come prodotto installabile/licenziabile presso il cliente. |
| **Terminale** | Eredita |

**Prompt** (usa `{{args}}` per cliente/contesto passato dopo il comando,
es. `/demo-prodotto Banca Alfa, settore finance, interlocutore architetto`):

```
Prepara il materiale per presentare al cliente {{args}} Inlay Studio come
prodotto che potrà installare e usare in autonomia sul proprio ambiente
(modello "prodotto": licenza, non solo servizio ENG). L'output ha SEMPRE
due parti distinte, non una sola: una presentazione e una demo live. Non
fermarti alla prima.

Prima di scrivere, verifica di avere questi elementi; se mancano, chiedili
esplicitamente invece di assumerli:
- Settore e contesto del cliente (cosa fa, dimensione, maturità digitale).
- Ruolo e profilo dell'interlocutore principale (Business Analyst,
  Architetto, sviluppatore/tech lead, Project Manager, decision maker non
  tecnico...): determina quanto la demo sarà pratica vs narrativa.
- Obiettivo concreto dell'incontro (prima presentazione esplorativa,
  pilot proposal, rinnovo/estensione...).
- Documentazione o asset di riferimento del cliente da richiamare, se
  esiste.

PARTE A — Presentazione (slide outline, una riga di contenuto per slide,
pensata per essere rifinita con la skill "slides"):
1. Apertura — il problema/bisogno del cliente in 2-3 frasi, senza gergo
   tecnico superfluo.
2. Cos'è Inlay Studio — posizionamento nella suite INLAY, cosa copre
   (Concept → Activity/Work Package) e cosa no.
3. Perché per loro — 3-4 vantaggi concreti legati al contesto fornito,
   non generici.
4. Installazione e autonomia d'uso — requisiti (WSL2/Podman o macOS),
   cosa resta in gestione al cliente, differenza con l'uso "a servizio"
   di ENG.
5. Prossimi passi proposti.

PARTE B — Demo live (sequenza pratica, non slide): descrivi passo per
passo cosa aprire e mostrare dentro Inlay Studio, schermata per
schermata, con la frase chiave da dire mentre lo si fa. Calibrala sul
profilo dell'interlocutore con questo criterio:
- Se è tecnico (sviluppatore, architetto, tech lead): trattalo come si
  mostrerebbe un IDE a uno sviluppatore — non se ne parla, lo si apre e
  si lavora davanti a lui. Riduci al minimo la narrazione, massimizza
  "mani sul prodotto": apri un progetto reale/di esempio, mostra Fonti
  indicizzate, lancia una skill o un comando, mostra l'output generato,
  apri un Workflow e un run. Il valore deve emergere dall'uso diretto,
  non dalla descrizione.
- Se è un profilo business/decision maker non tecnico: più narrazione,
  meno click; mostra 1-2 momenti chiave del prodotto in azione (non
  l'intero flusso tecnico) per ancorare i vantaggi a qualcosa di visto,
  non solo raccontato.
Ogni passo della demo deve indicare: cosa cliccare/aprire, cosa dire,
cosa far notare nel risultato.

Regole:
- Basati solo sui fatti di prodotto noti/documentati; se una domanda del
  cliente richiede un dato non disponibile, dillo chiaramente invece di
  inventare.
- Frasi brevi, linguaggio chiaro, formale ma non impersonale. Zero gergo
  marketing vuoto.
- Scrivi in italiano o inglese secondo necessità del cliente, con qualità
  madrelingua in entrambe le lingue; se non specificato, chiedi in quale
  lingua serve il materiale.
- Firma la risposta con "🤖 Alma:".
```

---

## 2. `/demo-servizio` — vendere ENG che usa Inlay Studio

**Quando usarlo**: il cliente non riceve il prodotto; valuta di farsi
seguire da ENG, che userà Inlay Studio internamente sul suo asset
(modello "servizio" — storicamente quello valido, default se non
diversamente confermato).

| Campo | Valore |
|---|---|
| **Nome** | `demo-servizio` |
| **Descrizione** | Genera materiale per dimostrare il valore di farsi affiancare da ENG, che lavora un asset del cliente con Inlay Studio senza installarlo presso il cliente. |
| **Terminale** | Eredita |

**Prompt** (usa `{{args}}` per cliente/asset/obiettivo, es.
`/demo-servizio Cliente Beta, assessment architetturale as-is allegato,
obiettivo: dimostrare velocità di analisi`):

```
Prepara il materiale per dimostrare al cliente {{args}} il valore di
farsi affiancare da ENG, che userà Inlay Studio internamente per
lavorare un asset del cliente (modello "servizio": il prodotto non
viene installato né consegnato al cliente, resta in infrastruttura
ENG). L'output ha SEMPRE due parti distinte, non una sola: una
presentazione e una demo live. Non fermarti alla prima.

Prima di scrivere, verifica di avere questi elementi; se mancano,
chiedili esplicitamente:
- L'asset del cliente da lavorare come esempio (documento, codebase,
  processo) o un suo estratto rappresentativo.
- L'obiettivo della dimostrazione (velocità, qualità, sicurezza, costo,
  o una combinazione).
- Il profilo dell'interlocutore (tecnico — es. sviluppatore/architetto —
  o business): determina quanto la demo sarà pratica vs narrativa.

PARTE A — Presentazione (slide outline, una riga di contenuto per slide,
pensata per essere rifinita con la skill "slides"):
1. Apertura — il problema del cliente collegato all'asset fornito.
2. Cosa abbiamo fatto — in sintesi, come ENG ha lavorato quell'asset con
   Inlay Studio (fasi toccate: concept/analisi/design/WBS...), senza
   entrare nei dettagli architetturali dello strumento in sé.
3. Il risultato — output concreto ottenuto sull'asset del cliente
   (confronto prima/dopo, se possibile).
4. Perché è stato più veloce/solido/sicuro grazie a noi — il
   differenziale è la suite proprietaria di delivery di ENG e il
   know-how, non genericamente "l'intelligenza artificiale".
5. Cosa resta a voi, cosa resta a noi — chiarisci che l'ambiente Inlay
   resta ENG; il cliente riceve l'output del lavoro, non lo strumento.
6. Prossimi passi proposti.

PARTE B — Demo live (sequenza pratica, non slide): descrivi passo per
passo cosa mostrare — sull'asset reale del cliente, se disponibile,
altrimenti su un esempio equivalente — con la frase chiave da dire
mentre lo si fa. Calibrala sul profilo dell'interlocutore:
- Se è tecnico: trattalo come si mostrerebbe un IDE a uno sviluppatore —
  apri davvero il progetto in Inlay Studio, mostra l'asset del cliente
  caricato come fonte, lancia la skill/fase pertinente (es. analisi o
  design) e mostra l'output reale generato a partire da quell'asset.
  Riduci la narrazione, massimizza "mani sul prodotto" sul loro
  materiale concreto.
- Se è business/decision maker: meno click, più confronto visivo
  prima/dopo sul loro asset, per ancorare i vantaggi a qualcosa di
  visto, non solo raccontato.
Ogni passo della demo deve indicare: cosa aprire/mostrare, cosa dire,
cosa far notare nel risultato.

Regole:
- Non proporre MAI, in questo scenario, l'installazione di Inlay Studio
  presso il cliente: è il modello "prodotto", distinto e non in oggetto
  qui.
- Basati solo su fatti/asset forniti; se mancano dati sul risultato
  ottenuto, chiedili invece di inventare metriche.
- Frasi brevi, linguaggio chiaro, formale ma non impersonale.
- Scrivi in italiano o inglese secondo necessità del cliente, con qualità
  madrelingua in entrambe le lingue.
- Firma la risposta con "🤖 Alma:".
```
