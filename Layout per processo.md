---
aliases:
  - "Layout a reparti"
  - "Configurazione per processo"
---
> **In 10 secondi:** l'area di produzione è divisa in **reparti per affinità tecnologica** (verniciatura, saldatura, lavorazioni meccaniche…): è la traduzione fisica del [[Job shop]]. Minimo investimento e massima flessibilità, al prezzo di flussi caotici, bassa saturazione, ↑TA e ↑WIP. [§6.2.2]

## Definizione
Configurazione in cui le unità produttive sono **raggruppate per tecnologia di processo**: ogni reparto realizza una sola tipologia di lavorazione con più macchine (general purpose, con diversi livelli di qualità e produttività) e personale specializzato su quella tecnologia.

## Come funziona
- Ogni ordine richiede operazioni presso **diversi centri di lavoro** → viene seguito individualmente e si muove in modo **non ripetitivo** tra i reparti (routing per prodotto, anche alternativi).
- Al crescere del numero di ordini, la mancanza di una sequenza tipica → **notevole complessità nella movimentazione** dei semilavorati (vedi [[Matrice origine-destinazione]] per l'analisi dei flussi).

## Vantaggi
- **Minor investimento complessivo**: le stesse macchine general purpose servono prodotti/processi diversi → meno macchinari dedicati.
- **Flessibilità** elevata (mix, prodotto, volume — vedi [[Job shop]] e [[Flessibilità]]).
- **Robustezza ai guasti**: la saturazione nei reparti non è elevata → spesso c'è una macchina libera che sostituisce quella ferma per guasto/manutenzione.

## Svantaggi
(≡ limiti del [[Job shop]], §2.1.3; ripresi nel confronto [[Analisi CVP]])
- Flussi complessi → ↑costi di trasporto interno (cv unitario maggiore nel CVP).
- ↓saturazione media, ↑[[Tempo di attraversamento]], ↑WIP ([[Legge di Little e WIP]]).
- Programmazione difficilissima, consegne imprevedibili, qualità meno costante.

## ⚠️ Trappole d'esame
- **"Per processo" (layout) ≠ "produzione per processo" (Cap2)**: il layout per processo è il job shop manifatturiero a reparti; la *produzione* per processo ([[Classificazione per processi tecnologici]]) ha ciclo obbligato e impone semmai il layout **in linea**. Quasi antonimi.
- La **bassa saturazione** è al tempo stesso svantaggio (inefficienza) e fonte del vantaggio di robustezza ai guasti — citare entrambe le facce.
- Nel CVP: CF minori e pendenza maggiore; tra BEP_linea e q* il processo genera **più** utili della linea (zona 3 delle 4).

## Collegamenti
- ← [[06 Cap6 - Layout e flussi di materiali]] §6.2.2 · equivalente impiantistico del [[Job shop]] ([[Matrice Prodotto-Processo]]: specialty + flusso frammentario)
- → confronto economico con [[Layout per prodotto]] via [[Analisi CVP]] (volume critico q*)
- → evoluzione naturale verso [[Layout a celle]] / [[Group technology]] quando emergono famiglie
- → analisi dei flussi: [[Matrice origine-destinazione]], [[Material handling]]
- Altre tipologie: [[Layout a posizione fissa]], [[Layout per prodotto]], [[Layout a celle]]
