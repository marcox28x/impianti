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

## [2026-06-12] ingest | Elementi di progettazione (§4.1)
- Riempita la pagina vuota `Elementi di progettazione.md` dal PDF `Impianti_2026 - 04`
  (pp.3-7): §4.1 definizione (composizione mezzi, scatola nera, funzione immanente),
  §4.1.1 occasioni (ex-novo/conversione/riconversione/ammodernamento/ampliamento
  orizz.-vert./sicurezza + marginalità), §4.1.2 le 5 dimensioni/sotto-progetti
  (finanziario, prodotto, processo, architettonico, commerciale; ciclo iterativo),
  §4.1.3 articolazione (studio di fattibilità 11 fasi + massima/definitivo/esecutivo +
  trade-off investimento↔produzione, Fig.1).
- Impostata come pagina-HUB §4.1: linka [[Occasioni di progettazione]] e
  [[Studio di fattibilità]] (già esistenti) invece di duplicarne il contenuto.
- Index aggiornato (nuova voce sotto Cap4).

## [2026-06-12] lint | Revisione Distinta base (BOM) vs PDF Cap4 §4.2.1
- Integrato dal PDF: n. livelli a scelta dell'azienda; simbologia natura item; scarto di processo vs sfridi tecnologici (doppia motivazione del c_imp netto); doppia utilità della validità; usi gestionali della DB; usi completi di esplosione/implosione; cenno a "provenienza"; esempio Figura 3 (parte a → 40 in riepilogata).
- Formattazione: callout §7 e finale portati a sintassi multilinea Obsidian.
- Link: rimossi self-link via alias (Archivi tecnici, Codifica item, MRP, Concurrent Engineering); [[Make or Buy]]→[[Make or buy]]; linkati [[Bilancio di massa]], [[Classificazione dei prodotti]], [[Numero di risorse|K1]]; corretto "Cap6-7"→Cap6.

## [2026-06-12] lint | Riscrittura pagina indice Cap5 (v1 → v2)
- La pagina `05 Cap5` era rimasta alla v1: notazione vecchia (N_j=⌈Q/P⌉), formula (8) errata (1−ΣTPi/(M·TCL)), Elmaghraby assente, **WIP/Little/Vladzyevsky/curve logistiche mancanti**, sezione "bilanciamento multiprodotto" inesistente nel PDF 2026.
- Riscritta seguendo la numerazione PDF: §5.2 numero risorse (η=K1–K4, M′ij/Mj/uj/U, dente di sega) · §5.3.1 bilanciamento monoprodotto (Salveson + Elmaghraby) · §5.3.2–5.3.3 Vladzyevsky · §5.3.4 WIP, Little, curve.
- Confermato all'utente: il **multiprodotto non è nel programma 2026** (solo linea monoprodotto); Kilbridge-Wester/Hoffmann/COMSOAL rimossi anche come menzioni barrate.
- Le pagine concetto (Numero di risorse, Bilanciamento delle linee, Little/WIP, Vladzyevsky, Curve, Collo di bottiglia) erano già v2 e coprono i vecchi wikilink tramite aliases — nessun link rotto.

## [2026-06-12] lint | Riscrittura pagina indice Cap2 (v1 → v2)
- Numerazione corretta sui PDF 2026: la pagina usava 2.0/2.1.1=CODP; ora §2.1.1 prodotti · §2.1.2 CODP · §2.1.3 processi+soluzioni impiantistiche · §2.1.4 lavoro · §2.1.5 volumi · §2.2 Matrice P-P.
- Matrice P-P spostata dalla sottosezione "layout logico" (terminologia non del PDF) alla sua sezione §2.2 di sintesi.
- De-duplicati i link verso alias della stessa pagina (Produzione di processo/parti/Reversibilità → Classificazione per processi tecnologici; Specializzazione manodopera/Job enrichment/rotation → Ritmi di avanzamento; Leve di riduzione → CODP).
- Aggiunti: indice di programmazione, postponement come 3ª leva, congruenze §2.1.5 (cemento/cantieri/auto/tessile + incongruenza ETO∧processo∧continua), trappole carta e celle vs isole, "volumi = unico profilo discrezionale".
- Nuovo candidato: [[Modalità di realizzazione dei volumi]] (pagina da creare).
- index.md: [[Postponement e Commonality]] spostato da Cap1 a Cap2 (il PDF 2026 lo formalizza in §2.1.2).

## [2026-06-12] lint | Riscrittura pagine indice Cap3 e Cap4 (v1 → v2)
- **Cap3**: numerazione corretta sui PDF (la pagina inventava 3.1–3.5; ora §3.1, 3.1.1, 3.1.2, 3.2.1–3.2.5). Aggiunti: livello di servizio e flessibilità/versatilità come sezioni proprie, IF con valori di riferimento, trappola doppio simbolo TA/TS, incertezza sulle rilavorazioni (Ep*·Q*=Ep·Q → OEE invariato), esempi nylon/Gragnano, sezione ⚠️ Affidabilità assente dal PDF 2026 (con MTBF/MTTR mantenuti per Ap). Link normalizzati sugli alias reali (Potenzialità produttiva, CP, indice di flusso via Tempo di attraversamento, Livello di servizio via qualità e servizio).
- **Cap4**: numerazione corretta (la pagina usava 4.1–4.5; ora §4.1.1–4.1.3, §4.2.1–4.2.2, §4.3: bilancio di massa rientra in §4.2.2, ingegnerizzazione è §4.3). Aggiunte le sezioni mancanti §4.1.2 (5 sotto-progetti) e §4.1.3 (studio di fattibilità 11 fasi + massima/definitivo/esecutivo + trade-off); linkati [[Processo produttivo]] e [[Studio di fattibilità]] (esistevano ma non erano nella pagina). De-linkato [[Perdite e rifiuti]] (contenuto in Bilancio di massa); compattati i link che risolvevano via alias (coefficienti DB, concurrent engineering, foglio di lavoro, parti unificate/catalogo/normazione).
- Punti chiave estesi con le domande ricorrenti di `domande_impianti` (8 voci in uscita, ABC ×4, occasioni, articolazione).

## [2026-06-12] lint | Riscrittura pagine indice Cap1 e Cap6 (v1 → v2)
- **Cap1**: numerazione corretta sui PDF (la pagina usava 1.1–1.4 con Ubicazione infilata nel "contesto"; ora §1.1, §1.2 con 1.2.1–1.2.2, §1.3 con 1.3.1–1.3.2). Aggiunti: VRP con le 4 azioni, PLC a 5 fasi (⚠️ con "Sviluppo") + ciclo fisico + ciclo del processo, metodo del punteggio §1.3.2 (alias di Ubicazione impianto), Rolling planning e Servitization linkati. [[Valore]]/[[Mercato]] → [[Mercato e valore]].
- **Cap6**: la pagina copriva solo metà capitolo (tipologie, CVP, flussi, aree). Aggiunte le sezioni mancanti: §6.1 impostazione, §6.3.1 **Buff + combinabilità** (domande ×3), §6.3.2 postazioni, §6.4 **material handling** (UdC, mezzi), §6.5 **magazzini** (6 indici ×4 in domande, tipologie, progettazione col rischio, allocazione), §6.6 espansione/piano regolatore. ⚠️ Corretto CVP: **4 zone**, non 3 (trappola n.18). Rimosso il collegamento →Cap7 (fuori programma 2026).
- Pulizia alias: la pagina Cap6 fungeva da alias-contenitore per concetti con pagina propria → frontmatter ridotto agli alias di capitolo; "Layout a postazioni fisse" spostato su [[Layout a posizione fissa]] (+ frontmatter creato), "Sistemi di movimentazione"/"Unità di carico (UdC)" su [[Material handling]], "Layout per processo vs per prodotto" resta su [[Analisi CVP]].
- Nuovo candidato: [[Layout per prodotto]] (linkato da Flow shop, Layout a celle, Ritmi di avanzamento; coprirà anche varianti serie/parallelo/misto e geometrie).

## [2026-06-12] lint | Riscrittura Layout per processo e Layout per prodotto
- Le due pagine erano dump grezzi del PDF Cap6 (refusi "ciascunamacchina", marcatori "Figura 2", "4/37"; quella per processo troncata ai soli vantaggi). Riscritte come pagine concetto: frontmatter con alias ("Layout a reparti"/"Configurazione per processo"; "Layout in linea"/"Configurazione per prodotto"), definizione, vantaggi/svantaggi, trappole, collegamenti (← / →).
- **Layout per processo** (§6.2.2): integrati gli svantaggi mancanti dall'equivalenza col [[Job shop]] (flussi complessi, ↓saturazione, ↑TA, ↑WIP); trappola nuova: "per processo" (layout ≡ reparti) ≠ "produzione per processo" (Cap2, ciclo obbligato → linea) — quasi antonimi; doppia faccia della bassa saturazione.
- **Layout per prodotto** (§6.2.3): strutturate le varianti serie (parcellizzazione) / parallelo (stazione) / misto e le geometrie rettilineo / U / zig-zag (tabella: posizione MP-PF distingue U da zig-zag); mini-esempio numerico sul parallelo (TCL 2', fase 6' → 3 macchine, link a [[Numero di risorse]]); trappole su parallelo vs serie e CVP a 4 zone.
- index.md: aggiunte al Cap6 le tre tipologie mancanti (posizione fissa, processo, prodotto).

## [2026-06-13] lint | Riscrittura Analisi CVP (era una risposta di chat, non la pagina concetto)
La pagina conteneva una risposta Q&A sul confronto robot/operatore (matematica corretta,
q* ≈ 111.000 pz/anno verificato) ma nulla del contenuto canonico §6.2.5 che 10 pagine
linkano: 4 zone, 2 BEP, retta dei ricavi, q*. Affermava inoltre "il prezzo non entra mai
nel conto" — vero per q* (intersezione dei costi) ma fuorviante per l'analisi CVP completa,
che usa R = p·q per definire le zone. Riscritta come pagina concetto da PDF Cap6 pp. 6–7;
esempio robot/operatore conservato come analogia. Nota: il PDF dice "tre zone" ma ne
descrive quattro → mantenuta la forma a 4 zone del KG v2.
