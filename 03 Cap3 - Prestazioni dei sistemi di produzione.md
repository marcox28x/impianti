---
aliases:
  - "03 Cap3 - Prestazioni"
  - "03 Prestazioni dei sistemi di produzione"
  - "Prestazioni dei sistemi di produzione"
---
## Domanda del capitolo
**Come si misura quanto un sistema produttivo lavora bene, e quanta parte del suo tempo genera davvero valore per il cliente?**

## Mini-riassunto
Il capitolo parte dalle definizioni di efficienza/efficacia e dalle **4 prestazioni** (produttività, qualità, servizio, flessibilità), poi le rende misurabili: potenzialità P, tempo di attraversamento TA con l'indice di flusso IF, potenzialità di mix (media armonica!). Il cuore è la "cipolla dei tempi" che scende da TS (tempo solare, 8760 h) a TOVA (unico tempo che il cliente paga): le sei grandi perdite erodono il tempo strato per strato e generano i 4 coefficienti (L, Ap, Ep, Q) e i due indicatori sintetici **OEE = Ap·Ep·Q** e **TEEP = L·Ap·Ep·Q**. Da questi si calcola la **capacità produttiva** reale: CP = P·TC·OEE.

## Concetti trattati

### 3.1 La misura delle prestazioni
- [[La misura delle prestazioni]] · [[efficienza vs efficacia]] ([[efficienza]] = output/input, [[efficacia]] = successi/eventi)
- Le 4 prestazioni: [[produttività]] (efficienza **statica**; v. anche [[produttività globale]]) · qualità · servizio · flessibilità (efficienza **dinamica**)

#### 3.1.1 Flessibilità e versatilità
- [[Flessibilità]] — 4 dimensioni (mix, prodotto, volume = elasticità, piano); **versatilità** = solo macchinari, necessaria ma non sufficiente

#### 3.1.2 Livello di servizio
- [[qualità e servizio|Livello di servizio]] — per commessa: prontezza + puntualità; a magazzino: disponibilità + persistenza stock-out; comuni: accuratezza + completezza

### 3.2 Le misure quantitative

#### 3.2.1 Potenzialità produttiva
- [[Potenzialità produttiva]] — P = ritmo standard = throughput rate; teorica (targa) vs effettiva; misure disaggregate (lavoro, macchinari, materiali = "resa")

#### 3.2.2 Tempo di attraversamento
- [[Tempo di attraversamento]] — TA, TVA, TCL (= TA della macchina più lenta), **IF = TA/TVA** (ottimi 1–2, buoni 3–5, tipici 10–100); esempio canonico 5 stazioni con analisi a segmenti
- ⚠️ doppio uso dei simboli: TA attraversamento ≠ TA apertura (§3.2.4); TS standard = 1/P ≠ TS solare

#### 3.2.3 Potenzialità di mix
- [[Potenzialità di mix]] — Pmix = 1/Σ(αi/Pi) = Σβi·Pi; ⚠️ media **armonica** pesata sui volumi, non aritmetica; β (% in tempo) ≠ α (% in volume)

#### 3.2.4 Overall Equipment Effectiveness
- [[Sei grandi perdite (six big losses)]] — fermate misurabili · perdite di velocità · perdite per difetti
- [[Quadro sinottico tempi]] — gerarchia TS → TA → [[tempo di carico|TC]] → [[tempo operativo|TO]] → TON → TOVA
- Coefficienti: [[Efficienza di carico (L)]] · [[Disponibilità (Ap)]] (← [[fermate misurabili]], [[MTBF e MTTR]]) · [[Efficienza prestazioni (Ep)]] · [[Tasso di qualità (Q)]]
- [[OEE]] = Ap·Ep·Q · [[TEEP]] = L·Ap·Ep·Q · contesto: [[TPM]]
- ⚠️ **Incertezza sulle rilavorazioni**: Ep* sottostima, Q* sovrastima, ma Ep*·Q* = Ep·Q → **OEE invariato**
- Esempi svolti: nylon (PDF, OEE 80,4%) · [[Esercizio svolto - OEE linea di stampaggio]]

#### 3.2.5 Capacità produttiva
- [[Capacità produttiva (CP)]] — CP = P·TOVA = P·TA·TEEP = P·TC·OEE; teorica vs reale; esempio Gragnano (Pmix + OEE → CP_mix)

### ⚠️ Affidabilità — fuori dal PDF 2026
- [[MTBF e MTTR]] restano utili per la stima ex-ante di Ap. Ma il capitolo affidabilità completo (R(t), λ, MTTF/MRL, Weibull, vasca da bagno, RBD, FTA/MOCUS) è chiesto in `domande_impianti` e **ASSENTE dal PDF Cap3 2026** → chiarire col docente prima di studiarlo da fonti esterne.

## Formule da ricordare a memoria
- $IF = TA/TVA \ge 1$
- $P_{mix} = \dfrac{1}{\sum_i \alpha_i / P_i} = \sum_i \beta_i P_i$ con $\alpha_i = Q_i/Q_{tot}$, $\beta_i = T_i/T_{tot}$
- $OEE = A_p \cdot E_p \cdot Q$ · $TEEP = L \cdot A_p \cdot E_p \cdot Q$
- $CP = P \cdot TC \cdot OEE = P \cdot TA \cdot TEEP = P \cdot TOVA$

## Punti chiave per l'esame
- Saper **disegnare la cipolla dei tempi** e associare ogni perdita allo strato giusto (manutenzione preventiva → pianificata, riduce L; guasti → misurabili, riducono Ap).
- Differenza **OEE vs TEEP**: L è invisibile all'OEE — un OEE alto non dice che l'impianto è ben caricato.
- **Pmix è media armonica**: l'errore "media aritmetica" è la trappola numero uno; e β ≠ α (il prodotto lento pesa più in tempo che in volume).
- **Rilavorazioni ignote → OEE comunque corretto** (Ep*·Q* = Ep·Q): saperlo dimostrare.
- Valori tipici: Ap > 90%, Ep 0,80–0,95 (linea) / 0,65–0,80 (reparti), Q 95–100%.
- Dichiarare sempre quale **TA** e quale **TS** si sta usando.

## Collegamenti
- ← [[02 Cap2 - Classificazione dei sistemi di produzione]]: i target di prestazione dipendono dalla classe (job shop ≠ linea)
- → [[04 Cap4 - Progettazione dei sistemi di produzione]]: OEE e CP sono **input al dimensionamento**
- → [[05 Cap5 - Configurazione dei sistemi di produzione]]: i K1–K4 sono i "gemelli progettuali" dei coefficienti OEE (K1≈Q, K2≈Ap, K3+K4≈Ep·L); TA/TVA/TCL è lo stesso linguaggio delle [[Curve logistiche operative]]
