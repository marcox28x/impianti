# Log — Impianti Industriali

Registro cronologico append-only. Ogni entry: `## [AAAA-MM-GG] tipo | Titolo`.
Ultime operazioni: `grep "^## \[" log.md | tail -5`.

## [2026-06-11] setup | Istanziato pattern LLM Wiki
Creati i file di infrastruttura: `CLAUDE.md` (schema), `index.md` (catalogo), `log.md`,
`_Knowledge Graph v2.md` (sintesi maestra). Il MOC esisteva già ed è stato collegato ai nuovi file.

## [2026-06-11] lint | Primo health-check del vault
- 13 file vuoti (0 byte), diversi sono concetti d'esame importanti (Matrice P-P, Potenzialità produttiva, Ep).
- Cap7 ancora citato nel MOC ma RIMOSSO dal materiale 2026 → depennato.
- Cap5/Cap6 con pagina indice ma molte sottopagine concetto mancanti.
- Affidabilità: domande in `domande_impianti` senza copertura nei PDF 2026 → chiarire col docente.
- Note grezze da archiviare: 9 aprile, Untitled, Esempio. Possibili duplicati produttività.md.

## [2026-06-11] ingest | PDF dei 6 capitoli aggiunti al vault
Aggiunta la cartella `pdf impianti/` con i 6 PDF `Impianti_2026 - 01…06`: completato il primo
livello (fonti grezze) dell'architettura LLM Wiki. Le pagine attingono ai PDF per esempi e figure.

## [2026-06-11] ingest | Compilati 16 stub ad alto rendimento d'esame
Scritte le pagine concetto (PDF + KG v2), copertura completa dei 6 capitoli:
- Cap1: [[Mass customization]], [[Servitization]]
- Cap2: [[Matrice Prodotto-Processo]]
- Cap3: [[Potenzialità produttiva]], [[Efficienza prestazioni (Ep)]], [[Tempo di attraversamento]]
- Cap4: [[Occasioni di progettazione]]
- Cap5: [[Numero di risorse]], [[Bilanciamento delle linee]], [[Legge di Little e WIP]], [[Criterio di Vladzyevsky]], [[Curve logistiche operative]]
- Cap6: [[Diagramma di Buff]], [[Matrice origine-destinazione]], [[Material handling]], [[Magazzini]]
Index aggiornato (voci 🔴→🟢 per ogni stub compilato).

## [2026-06-11] lint | Secondo health-check + fix sincronizzazione
Rilevato che alcune scritture (stub 0 byte pre-esistenti) e append non erano atterrati subito
sul disco → riscritti via shell. Verificato: nessun file prioritario resta a 0 byte.
Restano vuoti per scelta gli stub a bassa priorità: Contesto Competitivo, Leve competitive,
Mercato e valore, MTBF e MTTR, TPM, Rolling planning.

## [2026-06-11] lint | Pulizia link-variante + pagine trasversali
- Aggiunti **alias** (frontmatter YAML) a ~30 pagine bersaglio per risolvere i link a nomi-variante
  (Job Shop/Job shop, Group Technology, Postponement, Concurrent engineering, Bilanciamento di linea,
  Diagramma multiprodotto, Riprogettazione, ecc.).
- Create 5 pagine molto citate: [[Ciclo di lavorazione]], [[Collo di bottiglia]], [[Make or buy]],
  [[Just-in-time]]; riempito lo stub [[MTBF e MTTR]].
- Link rotti: da ~270 → 94 (tutti ≤2 occorrenze, concetti minori = pagine candidate, non errori).
- Index aggiornato con le nuove voci.

## [2026-06-11] lint | De-link dei concetti superflui (policy a tre vie)
Applicata la politica dei wikilink (ora documentata nello schema):
- DE-LINKATI ~60 target superflui in 21 file: perifrasi/confronti già trattati (es. "Macchine
  general purpose vs specializzate", "Discreta vs continua", "Cliente interno vs esterno") e
  sotto-concetti assorbiti altrove (Boccami/Cascami/diagrammi/level activity/esempi svolti).
- DE-LINKATI i FUORI-PROGRAMMA 2026: Hoffmann, Kilbridge-Wester, COMSOAL, frazionamento, Cap7.
- ALIAS per le ultime varianti (Lead Time, Misura delle prestazioni, TPM…, Distinta base di ordinazione).
- TENUTI come link-candidato 4 concetti veri da scrivere: [[Bilancio di massa]],
  [[Studio di fattibilità]], [[Costo della complessità]], [[Ubicazione impianto]].
RISULTATO: link rotti da ~270 → 4 candidati reali (+ falsi positivi in code-block). Grafo pulito.

## [2026-06-11] lint | Pulizia duplicati Unicode + cruft + stub vuoti
- DUPLICATI UNICODE (NFC vs NFD della "à"): `produttività.md` e `produttività globale.md`
  esistevano ciascuno in due copie fisiche distinte. Rimosse le versioni NFD obsolete
  (stub `produttività.md` da 161 b e copia di `globale`); tenute le NFC (nota completa 11257 b).
- RIMOSSO cruft: `Untitled.md` (conteneva il template di prompt incollato per errore),
  `Untitled.base`, `Untitled 1.base`, `Untitled 2.base`, `Untitled.canvas`.
- RIEMPITI 3 stub a 0 byte dal KG: [[Leve competitive]], [[Mercato e valore]], [[Rolling planning]].
- Verificato: MOC tratta già il Cap7 come ~~rimosso~~; i "broken link" residui (Nome nota, link, …)
  provengono solo dagli esempi in CLAUDE.md, non da note reali.

## [2026-06-12] lint | Chiusura candidati + promozione esercizio OEE
- CREATE le 4 pagine-candidato rimaste (tutte temi d'esame): [[Ubicazione impianto]]
  (principi + metodo del punteggio §1.3.2), [[Bilancio di massa]] (le 8 voci in uscita),
  [[Studio di fattibilità]] (11 fasi + massima/definitivo/esecutivo), [[Costo della complessità]]
  (4 level activities). → Zero link-candidato residui nel grafo.
- RIEMPITI gli ultimi 2 stub solo-frontmatter: [[TPM]] e [[Contesto Competitivo]].
- PROMOSSO `Esempio.md` → [[Esercizio svolto - OEE linea di stampaggio]]: risolto
  l'esercizio narrativo (L=80% · Ap=87,5% · Ep=83,3% · Q=95% → OEE=69,3%, TEEP=55,4%;
  il "55%" del collega = TEEP; tabella pezzi persi per coefficiente). Vecchio file rimosso.
- `9 aprile.md` marcato come fonte grezza INTEGRATA (banner verso Occasioni di
  progettazione / Studio di fattibilità / Make or buy).
- Index aggiornato: nuove voci Cap1/Cap3/Cap4, rimossi i riferimenti a Untitled/Esempio,
  sezione "Note di lavoro" → "fonti grezze".
