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
| **Descrizione** | Genera uno script di demo per proporre Inlay Studio come prodotto installabile/licenziabile presso il cliente. |
| **Terminale** | Eredita |

**Prompt** (usa `{{args}}` per cliente/contesto passato dopo il comando,
es. `/demo-prodotto Banca Alfa, settore finance, interlocutore architetto`):

```
Prepara uno script di presentazione per il cliente {{args}} con l'obiettivo
di proporre Inlay Studio come prodotto che il cliente potrà installare e
usare in autonomia sul proprio ambiente (modello "prodotto": licenza, non
solo servizio ENG).

Prima di scrivere, verifica di avere questi elementi; se mancano, chiedili
esplicitamente invece di assumerli:
- Settore e contesto del cliente (cosa fa, dimensione, maturità digitale).
- Ruolo e profilo dell'interlocutore principale in demo (Business Analyst,
  Architetto, Project Manager, decision maker non tecnico...).
- Obiettivo concreto della demo (prima presentazione esplorativa, pilot
  proposal, rinnovo/estensione...).
- Documentazione o asset di riferimento del cliente da richiamare nella
  demo, se esiste.

Struttura l'output così:
1. Apertura — il problema/bisogno del cliente in 2-3 frasi, senza gergo
   tecnico superfluo.
2. Cos'è Inlay Studio — posizionamento nella suite INLAY, cosa copre
   (Concept → Activity/Work Package) e cosa no, tarato sul livello
   tecnico dell'interlocutore.
3. Perché per loro — 3-4 vantaggi concreti legati al contesto fornito,
   non generici.
4. Come funziona in pratica — fonti, chat RAG, skill di fase, workflow,
   in un linguaggio adeguato al pubblico (meno architetturale per un
   decision maker, più dettagliato per un architetto).
5. Installazione e autonomia d'uso — requisiti (WSL2/Podman o macOS),
   cosa resta in gestione al cliente, differenza con l'uso "a servizio"
   di ENG.
6. Prossimi passi proposti.

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
Prepara materiale di presentazione per il cliente {{args}} con l'obiettivo
di dimostrare il valore di farsi affiancare da ENG, che userà Inlay
Studio internamente per lavorare un asset del cliente (modello
"servizio": il prodotto non viene installato né consegnato al cliente,
resta in infrastruttura ENG).

Prima di scrivere, verifica di avere questi elementi; se mancano,
chiedili esplicitamente:
- L'asset del cliente da lavorare come esempio (documento, codebase,
  processo) o un suo estratto rappresentativo.
- L'obiettivo della dimostrazione (velocità, qualità, sicurezza, costo,
  o una combinazione).
- Il profilo dell'interlocutore (tecnico o business).

Struttura l'output così:
1. Apertura — il problema del cliente collegato all'asset fornito.
2. Cosa abbiamo fatto — in sintesi, come ENG ha lavorato quell'asset con
   Inlay Studio (fasi toccate: concept/analisi/design/WBS...), senza
   entrare nei dettagli architetturali dello strumento in sé.
3. Il risultato — output concreto ottenuto sull'asset del cliente
   (confronto prima/dopo, se possibile).
4. Perché è stato più veloce/solido/sicuro grazie a noi — il
   differenziale è la suite proprietaria di delivery di ENG e il
   know-how, non genericamente "l'intelligenza artificiale" (che ha già
   chiunque).
5. Cosa resta a voi, cosa resta a noi — chiarisci che l'ambiente Inlay
   resta ENG; il cliente riceve l'output del lavoro, non lo strumento.
6. Prossimi passi proposti.

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
