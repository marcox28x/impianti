# CLAUDE.md — Schema del vault "Impianti Industriali"

> Questo file istruisce l'agente LLM su **come** mantenere questo vault come una *LLM Wiki*:
> una base di conoscenza markdown interlinkata, costruita e tenuta aggiornata in modo
> incrementale. L'utente cura le fonti e fa le domande; l'LLM scrive e mantiene la wiki.
> Co-evolvere questo file quando emergono convenzioni nuove.

## Cos'è questo vault
Note di studio per l'esame di **Impianti Industriali** (6 capitoli, materiale PDF
`Impianti_2026__01…06` + `domande_impianti`). Vault Obsidian, repo git di file markdown.
Obiettivo del corso: *guardare un processo produttivo e dire cosa non va, dove si perde
tempo/denaro, e come sistemarlo.*

## I tre livelli (architettura LLM Wiki)
1. **Fonti grezze** — PDF dei capitoli, `domande_impianti`, immagini incollate
   (`Pasted image *.png`), svg. Immutabili: si leggono, non si modificano.
2. **La wiki** — tutte le note `.md`. Di proprietà dell'LLM: crea/aggiorna pagine,
   mantiene i cross-reference, tiene tutto coerente. L'utente legge, l'LLM scrive.
3. **Lo schema** — questo file + `_Knowledge Graph v2.md` (la sintesi densa già compilata,
   con notazione logica e numerazione che segue ESATTAMENTE i PDF). Il KG v2 è la mappa
   maestra: consultalo per individuare capitolo/sezione e per le formule canoniche.

## Struttura delle pagine e convenzioni
- **Wikilink Obsidian**: `[[Nome nota]]` o `[[Nome nota|alias]]`. Sempre, mai link markdown.
- **Pagine indice di capitolo**: prefisso numerico `00`–`06` (es. `03 Cap3 - …`).
  Formato: *Domanda del capitolo · Mini-riassunto · Concetti trattati (per sezione, con
  link) · Punti chiave per l'esame · Collegamenti (← / →)*.
- **Pagine concetto/entità**: una nota per concetto, titolo = termine del glossario
  (es. `OEE.md`, `Potenzialità di mix.md`). Includere: definizione, formule, esempio
  numerico, trappole d'esame, collegamenti.
- **Notazione formule**: coerente col KG v2 (`→` causa · `⊂` sottoinsieme · `⚠️` trappola).
- **Numerazione**: rispecchia i PDF (es. §5.3.4.2). Non inventare numeri di sezione.

## File speciali di navigazione
- `00 Impianti - MOC.md` — Map of Content: porta d'ingresso, capitoli + trade-off trasversali.
- `index.md` — catalogo orientato al contenuto: ogni pagina con link + riassunto di una riga,
  per categoria. **Aggiornalo a ogni ingest.** In query: leggi prima l'index, poi le pagine.
- `log.md` — cronologico, append-only. Ogni entry inizia con `## [AAAA-MM-GG] tipo | Titolo`
  così `grep "^## \[" log.md | tail -5` dà le ultime operazioni. Tipi: `ingest`, `query`,
  `lint`, `setup`.
- `_Knowledge Graph v2.md` — sintesi maestra compressa (non sostituisce i PDF per esempi/figure).

## Operazioni

### Ingest (nuova fonte: appunti di lezione, paragrafo PDF, domanda d'esame)
1. Leggi la fonte; discuti i takeaway con l'utente.
2. Aggiorna/crea le pagine concetto toccate (definizioni, formule, esempi, trappole).
3. Aggiorna la pagina indice del capitolo pertinente e i cross-reference (← / →).
4. Aggiorna `index.md`.
5. Appendi una entry a `log.md`.
Una fonte può toccare 10–15 pagine. Segnala dove i dati nuovi contraddicono i vecchi
(es. divergenze PDF 2026 vs `domande_impianti`).

### Query (domanda d'esame / dubbio)
1. Leggi `index.md` e `_Knowledge Graph v2.md` per individuare le pagine rilevanti.
2. Leggi le pagine, sintetizza con citazioni `[[…]]`.
3. **Le risposte buone si rifilano nella wiki** come nuove pagine (confronti, esempi svolti,
   collegamenti scoperti) così le esplorazioni si accumulano. Poi appendi a `log.md`.

### Lint (health-check periodico)
Cerca: file vuoti (0 byte) da riempire o rimuovere, note orfane senza link entranti,
concetti citati ma senza pagina, cross-reference mancanti, contraddizioni tra pagine,
claim superati dal materiale 2026. Proponi domande nuove da investigare.

## Politica dei wikilink (quando linkare)
Un `[[link]]` segnala un **concetto che merita una pagina** (anche futura). Tre vie:
- **alias** (frontmatter `aliases:`) → se è solo un nome-variante di una pagina esistente;
- **tenere il link** → concetto vero senza pagina = "candidato" (es. `[[Bilancio di massa]]`, `[[Studio di fattibilità]]`, `[[Costo della complessità]]`, `[[Ubicazione impianto]]`);
- **de-linkare** (testo semplice) → perifrasi/confronti già trattati altrove, o argomenti FUORI programma 2026 (Hoffmann, Kilbridge-Wester, COMSOAL, frazionamento, Cap7).

## ⚠️ Specificità di questo corso (dal KG v2)
- **Cap7 (impianti di servizio) è RIMOSSO** dal materiale 2026. Il MOC lo cita ancora →
  va depennato/segnalato. Niente centralizzato/decentralizzato, frazionamento, accumulatori.
- **AFFIDABILITÀ** (R(t), λ, MTTF/MTBF/MRL, Weibull, vasca da bagno, RBD, FTA/MOCUS):
  presente in `domande_impianti` ma ASSENTE dal PDF Cap3 2026 → segnalare sempre prima
  di usare fonti esterne.
- Doppio uso dei simboli: `TA` = attraversamento (§3.2.2) vs apertura (§3.2.4);
  `TS` = standard 1/P vs solare 8760 h. Dichiarare sempre quale.
- Vedi `_Knowledge Graph v2.md` §TRAPPOLE per l'elenco completo degli errori ad alto rendimento.
