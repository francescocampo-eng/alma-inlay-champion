# Alma — esperta Inlay Studio

Repo dedicato alla persona **Alma**, agente Inlay Studio esperto di
prodotto, demo e posizionamento commerciale. Nessun contenuto presales
o di opportunità cliente: per quello vedi `Ciro` (locale, CLI, repo
`teams-channel-agent`, non importato in Inlay).

- `docs/alma_persona.md` — fonte canonica.
- `.atlas/alma_persona.md` — copia indicizzata da Atlas/Inlay Studio
  (Fonti). Rigenerare manualmente con:
  `cp docs/alma_persona.md .atlas/alma_persona.md`
  dopo ogni modifica a `docs/alma_persona.md`, poi commit+push.

## Setup in Inlay Studio

1. "Importa da GitHub" → `francescocampo-eng/alma-inlay-champion`.
2. Verifica che `.atlas/alma_persona.md` compaia in **Fonti**.
3. Rimuovi il vecchio progetto Inlay collegato a `teams-channel-agent`
   (quello precedentemente chiamato "Ciro"): da lì in poi Ciro resta
   solo locale via Copilot CLI.
4. Comandi e workflow (vedi `docs/alma_commands.md` e
   `docs/alma_workflow.md`): prova a importare i file in `exports/`
   (`.command.json` / `.workflow.json`); se Inlay rifiuta il formato,
   crealo a mano in UI seguendo i campi riportati nei due file markdown.

## Comandi e workflow di Alma

- **`/demo-prodotto`** — script di demo per vendere Inlay Studio come
  prodotto installabile presso il cliente.
- **`/demo-servizio`** — materiale per vendere la delivery ENG che usa
  Inlay Studio internamente sull'asset del cliente (nessuna
  installazione presso il cliente).
- **Workflow "Alma — aggiornamento competenza Inlay Studio"** — pull
  del repo docs sorgente, riepilogo novità, approvazione utente,
  aggiornamento mirato di `alma_persona.md` + commit/push.
