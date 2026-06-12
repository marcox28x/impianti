---
tags: [impianti, cap4, esame]
tipo: atomic-note
capitolo: "[[04 Cap4 - Progettazione dei sistemi di produzione]]"
aliases:
  - "Costi della complessità"
---
# Costo della complessità

> [!tldr] In 10 secondi
> Costi che variano con la **diversità e complessità dei prodotti, non coi volumi** (§4.3). Si articolano su 4 livelli (unit, batch, product, facility). L'[[ingegnerizzazione]] esiste proprio per minimizzarli: adattare le specifiche di prodotto al processo.

## Contesto
I costi **indiretti** (progettazione, manutenzione, logistica, scorte) crescono rispetto ai diretti → il driver dei costi non sono più solo i volumi ma la **varietà**.

## I 4 livelli
```
unit level     : costi a livello di singola unità   [controlli, supervisione MOD, energia]
batch level    : a livello di lotto                  [attrezzaggi, ordini approvv.,
                                                      movimentazione, programmazione]
product level  : a livello di famiglia               [progettazione prodotto,
                                                      componentistica, attività tecniche]
facility level : a livello di azienda                [direzione, amministrazione personale,
                                                      pulizia, luce]
```
⚠️ Solo i costi *unit level* scalano coi volumi: batch/product/facility scalano con il numero di **lotti, famiglie, strutture** → un mix ampio a parità di volume totale costa di più.

## Come si riduce
È l'obiettivo dell'**[[ingegnerizzazione]]** (§4.3): raggruppamento per similitudine tecnologica in famiglie → [[Analisi ABC (Pareto 80-20)]] (fascia C → candidata all'eliminazione) → [[Make or buy]] guidato dalla standardizzazione (parti unificate, da catalogo, da normazione aziendale). A monte, il [[VRP - Variety Reduction Program]] riduce varietà e numerosità dei componenti già in progettazione.

## Collegamenti
- PRIMA: [[Classificazione dei prodotti]] (complessità gestionale dalla distinta base)
- DENTRO: [[ingegnerizzazione]] · [[Analisi ABC (Pareto 80-20)]] · [[Make or buy]]
- CORRELATO: [[VRP - Variety Reduction Program]] · [[Postponement e Commonality]]
- [[04 Cap4 - Progettazione dei sistemi di produzione]] · [[_Knowledge Graph v2]] §4.3
