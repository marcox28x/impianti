---
aliases:
  - "Bilanciamento di linea"
  - "Bilanciamento di linea monoprodotto"
  - "Bilanciamento linea monoprodotto"
  - "Bilanciamento multiprodotto"
  - "Bilanciamento linea multiprodotto"
  - "Metodo di Salveson"
  - "Vincoli di precedenza"
  - "Balance Delay (BD)"
  - "Elemento minimo di lavoro"
  - "Stazioni e fasi"
---
# Bilanciamento delle linee

> [!summary] In 10 secondi
> Il **bilanciamento** (§5.3) consiste nel **ridurre i tempi di inattività e le differenze di velocità** fra le operazioni, aggregandole in **stazioni** in modo che ognuna lavori vicino allo stesso ritmo ($TCL$). Obiettivo: flusso organico, massima saturazione, minime scorte. Due metodi: **Salveson** (per tentativi, senza precedenze) ed **Elmaghraby** (euristico, con precedenze).




## §1 Parametri e formule (§5.3.1)
| Simbolo | Formula | Significato |
|---|---|---|
| $TCL$ | $TP/Q^*$ = $DT/v$ | tempo di ciclo della linea (ritmo richiesto) |
| $TP_i$ | — | tempo dell'**elemento minimo** $i$ |
| $TVA$ | $\sum_i TP_i$ | contenuto di lavoro totale |
| $TOP_j$ | $\sum_{i \in j} TP_i \leq TCL$ | tempo della stazione $j$ (vincolo di congruenza) |
| $TI_j$ | $TCL - TOP_j$ | inattività della stazione $j$ |
| $BD$ | $\sum_j TI_j$ | *balance delay* (ritardo di bilanciamento) |
| $i$ | $M - \dfrac{\sum TP_i}{TCL}$ (8) | coefficiente di inattività |

**Numero minimo di stazioni**:
$$M' = \left\lfloor \tfrac{\sum TP_i}{TCL} \right\rfloor + 1 \quad;\quad M'' = \#\{i : TP_i > TCL/2\} \quad;\quad M = \max\{M', M''\}$$

> [!warning] ⚠️ Formula (8) del PDF
> $i = M - \sum TP_i/TCL$ (può **superare 1**), non $1 - \sum TP_i/(M \cdot TCL)$. Poiché $\sum TP_i/TCL$ è costante per un dato problema → **min $i$ ⇔ min $M$**.

## §2 Criterio di Salveson (§5.3.1.1)
**Senza** vincoli di precedenza: per **tentativi**, cerca la partizione degli $n$ elementi in $M$ stazioni che rispetti $TOP_j \leq TCL$ col $M$ più piccolo.
- Limiti: ① enumerazione di tutte le partizioni (esplode con $n$); ② soluzioni **incongruenti** se esistono vincoli di sequenza.

> [!example] Esempio
> $TP_i = \{0{,}50; 1{,}00; 0{,}20; 0{,}85; 0{,}80; 0{,}10\}$, $TCL=1{,}00$. $M=4$. Soluzione libera $\{1\}\{2\}\{3,5\}\{4,6\}$ → $BD=0{,}55$ (ottima). Con sequenza obbligata 1→…→6: $\{1\}\{2\}\{3\}\{4\}\{5,6\}$ → $BD=1{,}55$, $M=5$. ⚠️ la soluzione sub-ottima diventa **l'unica feasible**.

## §3 Criterio di Elmaghraby (§5.3.1.2)
Euristico **con precedenze** (rappresentate alla PERT in matrice $P$, **transitivi inclusi**).
1. **Coefficiente di posizione**: $KP = (P + I_n) \cdot TP = TP_i + \sum$ (TP di tutti i successori).
2. Ordina $KP$ **decrescente**.
3. Assegna alla stazione $j$ l'operazione $k$ se: **(i)** $TP_k \leq TR_j$ (tempo residuo) **e (ii)** tutti i predecessori di $k$ sono già assegnati a stazioni $g \leq j$.

> [!example] Esempio 9 operazioni, $TCL=12$
> $KP_1=38 \ldots KP_9=3$ → ordine 1,2,3,4,6,5,7,8,9. Assegnazione → 4 stazioni, $BD=10$. Verifica con (8): $i = 4 - 38/12 = 0{,}83 = 10/12$ ✓.

## §4 Collegamenti
- [[Legge di Little e WIP]] — dopo il bilanciamento, il dimensionamento delle scorte interoperazionali
- [[Flow shop]] · [[Layout a celle]] — dove il bilanciamento è rilevante
- [[Potenzialità di mix]] — il collo determina la potenzialità della linea
- §5.3.1 di `Impianti_2026 - 05` · [[05 Cap5 - Configurazione dei sistemi di produzione]] · [[_Knowledge Graph v2]] §5.3.1



Per il bilanciamento si parte dal tempo ciclo

formula tempo ciclo
formula tempo ciclo per trasporto continuo

viene definita il tempo di operazione della postazione j TOPj
poi si nota che il TOP <= TCL
poiche ovviamente il TCL è il tick, le operazioni della postazione devono finire entro quel tempo in modo che possa passare alla prossima, se non succede cala la produttivita
bene ora si definisce il tempo di inattività della postazione formula.
poi si definisce il balance delay che è la somma dei tempi di inattività delle macchine
questi ci mostrano che il BD è quello che voglio minimizzare, ora dalle formule trovo che il BD minimo coincide col minimo numero di stazioni.
ora parliamo di salveson
salveson ci dice che dobbiamo calcolare il minimo facendo prima il calcolo dei tempi diviso il TCL prendiamo il suo intero inferiore e aggiungiamo 1
poi prendiamo i tempi che impiegano piu della metà del tempo ciclo. questi non possono essere accorpati in piu postazioni quindi se il loro numero è maggiore di M' allora sarà questo il numero minimo di postazioni.
poi ci sta un esempio ma è abbastanza facile
