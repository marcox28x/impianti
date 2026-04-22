# 05 Cap5 — Configurazione 

## Domanda del capitolo
**Quante macchine servono per soddisfare la domanda, e come suddivido il lavoro tra le stazioni di una linea perché tutte lavorino allo stesso ritmo?**

## Mini-riassunto
Due problemi gemelli: **saturazione** (N_j = ⌈Q/P_j⌉ macchine per tipo, con U_j che segue un andamento a dente-di-sega rispetto a Q) e **bilanciamento di linea** (dividere n elementi minimi in M stazioni con TOP_j ≤ TCL). Il bilanciamento ha obiettivo minimizzare il Balance Delay (BD = Σ δ_j) → equivalente a minimizzare M. Il numero minimo di stazioni si stima come max(M', M") con M' = ⌊ΣTP/TCL⌋+1 e M" = |{TP_i > TCL/2}|. Quando i vincoli di precedenza sono complessi si ricorre ad euristiche (Salveson, Kilbridge-Wester, Hoffmann) o alla simulazione COMSOAL. Per linee multiprodotto, il problema diventa combinatorio e si usano buffer interoperazionali.

## Concetti trattati

### 5.1 Saturazione delle macchine
- [[Numero di macchine (Nj)]]
- [[Coefficiente di utilizzazione (Uj)]]
- [[Saturazione di linea]]
- [[Andamento dente di sega della saturazione]]

### 5.2 Bilanciamento monoprodotto
- [[Elemento minimo di lavoro]]
- [[Tempo di ciclo linea (TCL)]]
- [[Tempo operazione stazione (TOPj)]]
- [[Vincoli di precedenza]]
- [[Tempo di inattività stazione]]
- [[Balance Delay (BD)]]
- [[Coefficiente di inattività (i)]]
- [[Numero minimo stazioni M']]
- [[Numero minimo stazioni M'']]
- [[M_min = max(M', M'')]]

### 5.3 Euristiche di bilanciamento
- [[Metodo di Salveson]]
- [[Metodo Kilbridge-Wester]]
- [[Metodo di Hoffmann]]
- [[COMSOAL]]

### 5.4 Bilanciamento multiprodotto
- [[Bilanciamento multiprodotto]]
- [[Buffer interoperazionali]]
- [[Colli di bottiglia]]

## Formule da ricordare a memoria
- $N_j = \lceil Q / P_j \rceil$
- $U_j = Q / (N_j \cdot P_j)$
- $TCL = T_{prod} / Q^* = \Delta T / v$
- $BD = \sum_j (TCL - TOP_j)$
- $i = 1 - \dfrac{\sum TP_i}{M \cdot TCL}$
- $M_{min} = \max(M', M'')$

## Punti chiave per l'esame
- Saper calcolare **N_j e U_j** per più macchine in sequenza.
- Capire perché minimizzare **i** equivale a minimizzare **M** (una sola leva, a TCL fissato).
- Saper applicare **Salveson a mano** su un piccolo grafo di precedenze (5-7 elementi).
- Riconoscere quando serve un **buffer** (asincronia, guasti, variabilità).

## Collegamenti
- ← [[04 Cap4 — Progettazione]]: ciclo e tempi arrivano da qui
- ← [[03 Cap3 — Prestazioni]]: P_j e OEE sono input al calcolo N_j
- → [[06 Cap6 — Layout e flussi]]: N_j e la disposizione delle stazioni definiscono il layout fisico