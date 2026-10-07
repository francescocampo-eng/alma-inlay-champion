# Workflow di Alma: aggiornamento competenza Inlay Studio

**Perché serve**: la persona di Alma si basa su
`DevExpPlatform/project-am-inlay-docs-portal`, che cambia nel tempo
(nuove skill, fasi, MCP server, aggiornamenti al go-to-market). Senza un
processo esplicito, Alma rischia di rispondere con informazioni
superate. Questo workflow automatizza il controllo e propone
l'aggiornamento della persona, **con approvazione dell'utente prima di
scrivere** (nessuna modifica silenziosa alla propria identità).

> **Nota sul formato**: come per i comandi, il file `.workflow.json`
> incluso è un tentativo di export basato sui campi documentati in
> `user-manual/workflows.md`, **non verificato** con un'importazione
> reale. Se fallisce, crea il workflow a mano in **Workflow di progetto →
> Nuovo workflow** seguendo gli step sotto — più lento ma garantito.

## Nome

`Alma — aggiornamento competenza Inlay Studio`

## Step 1 — Agente: sincronizza la fonte

**Esecuzione codice**: attiva.

```
Verifica se la cartella locale del repository
DevExpPlatform/project-am-inlay-docs-portal esiste nell'ambiente
corrente. Se non esiste, clonala con:
  gh repo clone DevExpPlatform/project-am-inlay-docs-portal
Se esiste, esegui `git pull` dopo aver registrato l'hash del commit
corrente con `git log -1 --format=%H` (hash "prima"). Dopo il pull,
registra di nuovo l'hash con lo stesso comando (hash "dopo"). Se i due
hash coincidono, segnala esplicitamente "nessun aggiornamento
disponibile" e termina qui senza eseguire gli step successivi.
```

## Step 2 — Agente: riassumi le novità rilevanti

**Esecuzione codice**: attiva.

```
Confronta i file cambiati tra l'hash "prima" e l'hash "dopo" con:
  git diff --name-only <hash_prima> <hash_dopo> -- docs/
Per ciascun file modificato dentro docs/inlay-studio/ o docs/intro.md,
produci un riassunto puntuale delle novità rilevanti per demo e
posizionamento prodotto: nuove skill, nuove fasi della pipeline,
modifiche architetturali, nuovi MCP server, cambi nel modello di
go-to-market (servizio/prodotto). Se le modifiche sono solo
cosmetiche/non rilevanti per una demo cliente (refusi, screenshot,
riordino), dillo esplicitamente e segnala che non serve aggiornare la
persona di Alma.
```

## Step 3 — Approvazione

```
Mostra all'utente il riepilogo delle novità rilevanti prodotto allo
step precedente e chiedi conferma esplicita prima di modificare
docs/alma_persona.md.
```

## Step 4 — Agente: aggiorna la persona

**Esecuzione codice**: attiva.

```
Aggiorna docs/alma_persona.md solo nelle sezioni toccate dalle novità
confermate dall'utente (es. tabella prodotti INLAY, sezione
Architettura, sezione go-to-market) — non riscrivere il resto del
file. Copia il file aggiornato anche in .atlas/alma_persona.md
(identico, è l'unica copia indicizzata da Fonti). Poi esegui:
  git add -A && git commit -m "docs: aggiornamento competenza Alma da
  project-am-inlay-docs-portal@<hash_dopo>" && git push
Conferma all'utente l'hash del commit e ricorda che per vedere la
modifica sul proprio PC serve un git pull locale del repo
alma-inlay-champion.
```

## Pianificazione (cron): sconsigliata

Lo Step 3 è un punto di approvazione: un'esecuzione schedulata (es.
lunedì mattina) senza nessuno collegato resta bloccata su "In attesa di
approvazione" finché l'utente non la apre e approva/rifiuta a mano —
stesso limite già incontrato con i workflow di Ciro. Due opzioni:

- **Consigliata**: nessuna pianificazione; eseguire il workflow a mano
  quando si sa che il portale docs è stato aggiornato (es. dopo una
  nuova release Inlay).
- **Alternativa**: pianificare comunque (es. settimanale) accettando che
  il run resti "in attesa" come promemoria silenzioso da approvare al
  primo accesso successivo — utile solo se si controlla Inlay Studio con
  regolarità.
