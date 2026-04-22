## Domanda del capitolo
**Come dispongo nello spazio le macchine e i reparti calcolati al Cap 5 per minimizzare i trasporti interni e massimizzare l'efficienza del flusso?**

## Mini-riassunto
Quattro tipologie di layout: **posizione fissa** (prodotto ingombrante, risorse vanno al prodotto — es. cantieri), **per processo** (≡ job shop, flessibile ma flussi complessi), **per prodotto** (≡ flow shop, in linea secondo il ciclo; varianti serie/parallelo/misto e geometrie rettilineo/U/zig-zag), **a celle** (group technology applicata al layout). La scelta tra processo e prodotto si fa con l'**analisi CVP**: il layout per processo ha costo fisso più basso ma costo variabile più alto, viceversa per il layout per prodotto — il volume critico Q* determina quale è più conveniente. L'analisi dei flussi minimizza il costo totale dei trasporti interni Σ q_ij·c_ij·d_ij usando diagrammi multiprodotto e matrici origine-destinazione, applicando i principi di **centralità** (alto traffico al centro) e **vicinanza** (coppie ad alta intensità accostate).

## Concetti trattati

### 6.1 Tipologie di layout
- [[Layout a posizione fissa]]
- [[Layout per processo]]
- [[Layout per prodotto]]
- [[Varianti del layout per prodotto]] (serie, parallelo, misto)
- [[Geometrie di linea]] (rettilineo, U, zig-zag)
- [[Layout a celle]]
- [[Confronto tra layout]] (pro/contro)

### 6.2 Scelta del layout — Analisi CVP
- [[Analisi CVP]] (Cost-Volume-Profit)
- [[Break Even Point]]
- [[Volume critico Q*]]
- [[Regola volume-varietà]]

### 6.3 Analisi dei flussi di materiali
- [[Costo totale di trasporto interno]]
- [[Diagramma multiprodotto]]
- [[Matrice origine-destinazione]]
- [[Intensità di traffico]]
- [[Principio di centralità]]
- [[Principio di vicinanza]]

### 6.4 Dimensionamento delle aree
- [[Area totale macchina]] (ingombro + operatore + manutenzione + MP/PF locali + corridoi)
- [[Corridoi e normativa]]
- [[Sistemi di movimentazione]]
- [[Flusso monodirezionale vs bidirezionale]]

## Formula chiave
$$ CT_{trasp} = \sum_i \sum_j q_{ij} \cdot c_{ij} \cdot d_{ij} $$

## Punti chiave per l'esame
- Saper disegnare il **diagramma CVP** e leggere i 3 zone (entrambi in perdita / solo processo in utile / prodotto più redditizio).
- Regola empirica: **alti volumi + bassa varietà → linea**; **bassi volumi + alta varietà → reparti**.
- Saper costruire una **matrice origine-destinazione** e identificare i centri critici dalla diagonale.
- Conoscere pro/contro di ciascun layout (tabella mentale).

## Collegamenti
- ← [[05 Cap5 — Configurazione]]: N_j e TCL definiscono cosa si posiziona
- ← [[04 Cap4 — Progettazione]]: il bilancio di massa alimenta l'analisi dei flussi
- ← [[02 Cap2 — Classificazione]]: job shop ↔ layout per processo, flow shop ↔ layout per prodotto
- → [[07 Cap7 — Impianti di servizio]]: le utenze da servire sono quelle posizionate qui