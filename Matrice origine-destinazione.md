---
aliases:
  - "Diagramma multiprodotto"
  - "Intensità di traffico"
  - "Costo totale di trasporto interno"
  - "Principio di centralità"
  - "Principio di vicinanza"
---
# Matrice origine-destinazione

> [!summary] In 10 secondi
> La **matrice origine-destinazione** (O-D, §6.3) è la matrice delle **intensità di traffico** fra i centri produttivi: righe = flussi in **uscita**, colonne = flussi in **ingresso**, diagonale = **criticità** del centro. È lo strumento base per la disposizione di primo tentativo del layout.

## §1 Obiettivo dei flussi (§6.3)
Minimizzare il costo di trasporto totale:
$$\min\; CT = \sum_i \sum_j q_{ij} \cdot c_{ij} \cdot d_{ij}$$
$q_{ij}$ quantità movimentata (udc) da $i$ a $j$ · $c_{ij}$ costo per udc·lunghezza · $d_{ij}$ distanza.

## §2 La matrice O-D
- **righe** = flussi in **uscita** dal centro · **colonne** = flussi in **ingresso**;
- la **diagonale** = somma di riga + colonna = **criticità** (traffico totale che attraversa il centro);
- le celle possono essere espresse come **rapporto** (es. n. udc / peso) e corrette coi $c_{ij}$ per costi diversi.

## §3 Diagrammi correlati
- **Diagramma multiprodotto**: per ogni prodotto la sequenza di attraversamento sui macchinari → evidenzia i centri più movimentati e le **sequenze ripetute** → suggerisce **celle** ([[Layout a celle]]).

## §4 Disposizione di primo tentativo
Su spazio libero, due principi:
- **centralità**: i centri ad alto traffico (alta diagonale) in zona **centrale**;
- **vicinanza**: le coppie ad alta intensità reciproca tenute **vicine**.
→ poi **configurazione effettiva**: aree per reparto, corridoi da normativa, vincoli strutturali. Ogni macchina ha un **poligono d'ingombro funzionale** (ingombro + operatore + manutenzione + depositi).

## §5 Collegamenti
- [[Diagramma di Buff]] — quando il flusso non è l'unico criterio (disturbi, sicurezza)
- [[Layout a celle]] — le sequenze ripetute suggeriscono celle
- [[Analisi CVP]] — la scelta processo vs prodotto a monte del layout
- §6.3 di `Impianti_2026 - 06` · [[06 Cap6 - Layout e flussi di materiali]] · [[_Knowledge Graph v2]] §6.3
