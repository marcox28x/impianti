---
aliases:
  - "Colli di bottiglia"
  - "Bottleneck"
---
# Collo di bottiglia

> [!summary] In 10 secondi
> Il **collo di bottiglia** è la stazione con la **potenzialità minima** della linea: determina il ritmo massimo ($P_b$) dell'intero sistema. ⚠️ Non è necessariamente la stazione con meno macchine né quella col tempo di lavorazione maggiore: è quella col rapporto **n. macchine / tempo** più basso.

## §1 Definizione
$$P_b = \min_j P_j \qquad P_j = \frac{\text{n. macchine}_j}{\text{tempo}_j}$$

Il collo fissa: la **potenzialità della linea**, il **tempo di ciclo** $TCL$, e il $WIP_c = P_b \cdot TVA$ (vedi [[Legge di Little e WIP]]).

## §2 Esempio (linea non bilanciata) ⚠️
4 stazioni / 11 macchine: A (1 macch, 2h → 0,50) · B (2 macch, 5h → **0,40 = $P_b$**) · C (6 macch, 10h → 0,60) · D (2 macch, 3h → 0,67).
→ il collo è **B**, **non** A (meno macchine) né C (tempo maggiore).

## §3 Potenziarlo
- **↑$P_b$** (macchina in parallelo/sostituzione): alza tutte le curve, WIP invariato, ma costoso.
- Potenziare i **non-colli** non cambia $P_b$ ma riduce $TVA$ → ↓$WIP_c$ (vedi [[Curve logistiche operative]]).

## §4 Collegamenti
- [[Numero di risorse]] · [[Bilanciamento delle linee]] — dove il collo emerge
- [[Legge di Little e WIP]] · [[Curve logistiche operative]] — $P_b$ nelle formule
- [[Group technology]] — collo identificabile e stabile (vs job shop, collo "mobile")
- [[_Knowledge Graph v2]] §5.3.4.5
