---
aliases:
  - "Disponibilità"
  - "Disponibilità Ap"
  - "Manutenzione preventiva"
  - "Manutenzione su condizione"
  - "Fermate pianificate vs cause esterne"
---
**In 10 secondi:** La Disponibilità Ap misura la **frazione del tempo di carico in cui la macchina è effettivamente in grado di produrre**, dopo aver tolto le perdite di tempo "grandi" e misurabili: guasti e setup. È il primo dei tre coefficienti dell'[[OEE]] e il primo a essere tipicamente attaccato dalle aziende perché si calcola da dati aziendali documentati.

---

## §1 Domanda fondamentale

Della macchina che ho deciso di accendere oggi, **quanto tempo riesce davvero a stare in produzione** prima che si fermi per qualcosa di documentato (rottura o riattrezzaggio)?

---

## §2 Il problema concreto

**StampaTorino S.r.l.**, fornitore Tier 1 dell'automotive, ha una **pressa di stampaggio rotativa** da 800 tonnellate dedicata alle portiere di un SUV di gamma media. La pressa è programmata per lavorare **400 ore al mese** (2 turni × 5 giorni × 4 settimane, già al netto delle festività e della manutenzione preventiva pianificata della domenica).

A fine mese, il responsabile produzione tira fuori i registri:

- **3 guasti non programmati** al circuito idraulico → ciascuno 4-5 h di fermo, totale **14 h**
- **16 cambi stampo** durante il mese (alternanza tra portiera anteriore SX/DX e modello sedan/SUV) → ciascuno ~30 min, totale **8 h**

Il direttore di stabilimento chiede: _"Stiamo sotto target del 95%? Dove dobbiamo investire — su un nuovo sistema idraulico (per ridurre i guasti) o su un riattrezzaggio rapido tipo SMED (per ridurre i setup)?"_

Il dilemma: senza un numero unico che sintetizzi quanto "vive" la pressa, non si decide. E senza scomporre il numero nelle due voci (guasti vs setup), non si capisce su quale leva agire.

→ La Disponibilità Ap è esattamente il numero che il direttore cerca: dice quanto, sulle 400 h programmate, la pressa è realmente disponibile a produrre.

---

## §3 La definizione

**Definizione formale:**

> La **Disponibilità produttiva** Ap (Availability) è il rapporto tra il **Tempo Operativo TO** (tempo in cui la macchina effettivamente lavora) e il **Tempo di Carico TC** (tempo in cui era programmata per lavorare):

$$A_p = \frac{TO}{TC} \tag{13}$$

Operativamente, dato che $TO = TC - T_{guasti} - T_{setup}$, si calcola dai dati aziendali come:

$$A_p = \frac{TC - T_{guasti} - T_{setup}}{TC} \tag{14}$$

**Scomposizione delle parti:**

- $TC$ → tempo di carico, cioè il tempo per cui la macchina era _programmata per produrre_ (già al netto delle fermate pianificate e delle cause esterne).
- $T_{guasti}$ → somma delle durate di tutti i fermi **non pianificati** per rottura o malfunzionamento.
- $T_{setup}$ → somma delle durate di tutti i cambi prodotto, riattrezzaggi, regolazioni.
- $TO$ → tempo operativo: differenza tra TC e le due perdite "grandi" sopra.

**Caratteristiche numeriche:**

- È un **numero puro** ∈ [0, 1] (o equivalentemente in %).
- **Tipicamente > 90%** in impianti ben gestiti.
- **Esclude** gli effetti di qualità, perdite di velocità e fermate pianificate (quelli vivono altrove: qualità in [[Tasso di qualità|Q]], velocità in [[Efficienza prestazioni|Ep]], fermate pianificate stanno tra TA e TC).

**Disponibilità limite** (versione analitica, dai dati di targa del produttore):

$$A_{p,\text{lim}} = \frac{MTBF}{MTBF + MTTR}$$

dove [[MTBF]] = Mean Time Between Failures (tempo medio tra due guasti) e [[MTTR]] = Mean Time To Repair (tempo medio di riparazione). È la disponibilità "intrinseca" della macchina, considerando _solo_ i guasti, non i setup. Per costruzione: $A_p^{reale} \leq A_{p,\text{lim}}$ (perché Ap reale toglie anche i setup, che sono organizzativi e non intrinseci alla macchina).

---

## §4 Come funziona

**Cuore del meccanismo:** Ap traduce in un singolo numero la domanda "quanto del tempo che ho deciso di tenere accesa la macchina, lei è davvero in grado di produrre?". Il complemento $1 - A_p$ è esattamente la frazione di tempo perso per guasti + setup, cioè per le perdite del **gruppo A** delle [[Sei grandi perdite (six big losses)]].

**Connessione gerarchica:** Ap si colloca al primo livello di scomposizione del tempo di carico nella catena OEE. Schematizzando:

```
TC
 ↓ — perdite gruppo A (guasti + setup)   →  Ap = TO/TC
TO
 ↓ — perdite gruppo B (velocità + microfermate)  →  Ep = TON/TO
TON
 ↓ — perdite gruppo C (scarti + rilavorazioni)   →  Q = TOVA/TON
TOVA
```

→ $OEE = A_p \cdot E_p \cdot Q$ — Ap è il primo dei tre fattori moltiplicativi.

**Casi limite:**

- **Ap → 100%**: nessun guasto, nessun setup. È il limite teorico. Realisticamente, anche le linee migliori al mondo si fermano almeno per cambi prodotto.
- **Ap < 90% sostenuta nel tempo**: campanello d'allarme. Significa che oltre il 10% del tempo programmato è perso per fermi documentati. In automotive, farmaceutico, semiconductor è considerato preoccupante.
- **Ap reale ≪ Ap limite**: il problema non è la macchina (l'affidabilità intrinseca è buona), ma il modo in cui la usi: troppi cambi prodotto o setup mal gestiti. Soluzione: SMED, sequenziamento intelligente delle commesse.
- **Ap reale ≈ Ap limite**: i setup sono trascurabili o ben gestiti; il problema (se c'è) è la macchina stessa. Soluzione: manutenzione preventiva, ridondanza, sostituzione.
- **Ap = 95% ma OEE = 50%**: Ap alta non garantisce nulla sull'efficienza complessiva. Le altre due perdite (Ep e Q) possono distruggere l'OEE.

---

## §5 Applicazione pratica

**Formula principale:**

$$\boxed{A_p = \frac{TO}{TC} = \frac{TC - T_{guasti} - T_{setup}}{TC}}$$

**Disponibilità limite (da dati di targa):**

$$\boxed{A_{p,\text{lim}} = \frac{MTBF}{MTBF + MTTR}}$$

**Procedura step-by-step per calcolare Ap dai dati aziendali:**

1. **Definisci il periodo di analisi** (mese, trimestre, anno) e identifica chiaramente la macchina/linea.
2. **Calcola TC** = ore in cui la macchina era _programmata_ per produrre. Parti dal tempo di apertura impianto TA e sottrai le fermate pianificate (manutenzione preventiva, festività, mancanza ordini, ecc.).
3. **Estrai $T_{guasti}$** dai dati del CMMS o dei work-order di manutenzione: somma le durate di tutti i fermi NON programmati. Attenzione a non includere la manutenzione preventiva, che è già stata tolta in TC.
4. **Estrai $T_{setup}$** dai log del MES o dai registri di reparto: somma le durate di tutti i cambi prodotto, regolazioni, riattrezzaggi.
5. **Calcola $TO = TC - T_{guasti} - T_{setup}$**.
6. **Calcola $A_p = TO/TC$**.
7. **(Opzionale) Confronta con Ap limite** (da MTBF/MTTR di targa). Se $A_p^{reale} \ll A_{p,\text{lim}}$, il problema è organizzativo (setup); se $A_p^{reale} \approx A_{p,\text{lim}}$, il problema è la macchina.

**Checklist anti-errore:**

- [ ] Sto usando il **TC**, non il TA (tempo di apertura)? Le fermate pianificate vanno tolte _prima_.
- [ ] Ho escluso la **manutenzione preventiva programmata** dai guasti? Quella è una fermata pianificata, non una perdita.
- [ ] Ho incluso **tutti** i tipi di setup (cambio prodotto, cambio utensile, regolazioni)?
- [ ] Sto attribuendo correttamente i fermi alla macchina giusta? (Un blocco a valle può fermare la macchina a monte: di chi è la perdita?)
- [ ] Le unità sono coerenti (tutto in ore, o tutto in minuti)?
- [ ] Il risultato è ragionevole (tipicamente 0.85 – 0.98)?

---

## §6 Esercizio tipo esame

**Testo dell'esercizio:**

> La pressa di stampaggio di **StampaTorino S.r.l.** lavora portiere SUV. Nel mese di marzo è stata programmata per **400 ore** (2 turni × 5 giorni × 4 settimane). Dai dati aziendali emerge:
> 
> - **3 guasti** all'impianto idraulico, durata totale **14 ore**;
> - **16 cambi stampo**, durata media **30 minuti** ciascuno.
> 
> Il produttore della pressa dichiara dati di targa: **MTBF = 130 h**, **MTTR = 4 h**.
> 
> a) Calcola la Disponibilità reale $A_p$. b) Calcola la Disponibilità limite $A_{p,\text{lim}}$. c) Discuti il confronto tra i due valori e indica su quale leva conviene investire.

**Soluzione passo-passo:**

**Punto a) — Disponibilità reale**

_Step 1: identifico TC._ $TC = 400$ h (dato).

_Step 2: calcolo i tempi di perdita del gruppo A._

- $T_{guasti} = 14$ h (dato).
- $T_{setup} = 16 \cdot 30 \text{ min} = 480 \text{ min} = 8$ h.

_Step 3: calcolo TO._ $$TO = TC - T_{guasti} - T_{setup} = 400 - 14 - 8 = 378 \text{ h}$$

_Step 4: calcolo Ap._ $$A_p = \frac{TO}{TC} = \frac{378}{400} = 0{,}945 = \mathbf{94{,}5}$$

**Punto b) — Disponibilità limite**

$$A_{p,\text{lim}} = \frac{MTBF}{MTBF + MTTR} = \frac{130}{130 + 4} = \frac{130}{134} = 0{,}970 = \mathbf{97{,}0}$$

**Punto c) — Interpretazione**

$A_p^{reale} = 94{,}5 < A_{p,\text{lim}} = 97{,}0$. La differenza è di **2,5 punti percentuali**, che corrispondono a circa $0{,}025 \cdot 400 = 10$ h/mese di disponibilità persa **non riconducibile alla macchina**. Quasi tutta questa perdita è dovuta ai setup (8 h su 10 h di gap; le altre 2 h sono dovute al fatto che i 3 guasti hanno durata media 14/3 ≈ 4,67 h, leggermente sopra l'MTTR di targa di 4 h).

Quindi:

- La pressa **come macchina** è già molto vicina al suo limite teorico di affidabilità.
- Il margine di miglioramento più grande è **organizzativo**: ridurre i setup tramite SMED o sequenziare meglio le commesse per minimizzare i cambi.
- Investire in un nuovo impianto idraulico più affidabile (ridurre MTBF/aumentare MTTR) darebbe al massimo 1,5 punti percentuali (la differenza tra Ap_lim attuale e 100%, e solo se i guasti diventassero zero).

→ Decisione: **investire in SMED**, non sull'idraulica.

---

**Variante** ("e se cambiasse X?"):

> _L'azienda introduce un programma SMED che dimezza i tempi di setup. Ricalcola Ap e calcola anche di quanto migliora la produzione mensile, supponendo che la pressa abbia un ritmo standard di 60 portiere/h._

_Step 1: nuovo $T_{setup}$._ $T_{setup}^{new} = 8 / 2 = 4$ h.

_Step 2: nuovo TO._ $TO^{new} = 400 - 14 - 4 = 382$ h.

_Step 3: nuova Ap._ $$A_p^{new} = \frac{382}{400} = 0{,}955 = \mathbf{95{,}5}$$

_Step 4: portiere extra prodotte._ $\Delta TO = 4$ h ⇒ $\Delta Q = 4 \cdot 60 = \mathbf{240}$ portiere extra al mese (assumendo Ep = Q = 100, altrimenti il guadagno effettivo è $\Delta TO \cdot 60 \cdot E_p \cdot Q$).

Il salto di Ap è di soli +1 punto percentuale, ma in volume corrisponde a 240 portiere/mese — non trascurabile per un Tier 1 con margini ridotti.

---

## §7 Errori comuni

> [!warning] ❌ Errore 1 — Usare TA al posto di TC al denominatore Se metti $A_p = TO/TA$ stai calcolando in realtà $L \cdot A_p$ (efficienza di carico × disponibilità), e ottieni un numero più piccolo che mescola due fattori distinti. Ap si misura **rispetto al tempo di carico** (programmato per produrre), non rispetto al tempo di apertura impianto. **Come evitarlo:** parti sempre dalla gerarchia $TS \to TA \to TC \to TO \to TON \to TOVA$. Ogni coefficiente OEE rapporta due livelli **adiacenti**: Ap = TO/TC, non TO/TA.

> [!warning] ❌ Errore 2 — Includere la manutenzione preventiva tra i guasti La manutenzione preventiva programmata è una **fermata pianificata**, già esclusa nel passaggio TA → TC. Includerla anche nei guasti significa contarla due volte e abbassare ingiustamente Ap. I "guasti" del gruppo A sono solo i fermi **non programmati**. **Come evitarlo:** la regola è "era a calendario? → fermata pianificata, riduce TC. Non era a calendario? → guasto, riduce TO".

> [!warning] ❌ Errore 3 — Confondere Ap reale con disponibilità limite $A_{p,\text{lim}} = MTBF/(MTBF+MTTR)$ considera **solo** i guasti, non i setup. È la disponibilità intrinseca della macchina. L'Ap reale che usi nell'OEE include anche i setup ed è quindi $\leq A_{p,\text{lim}}$. Confonderle porta a sopravvalutare la disponibilità reale (e a non vedere il problema dei setup). **Come evitarlo:** la disponibilità limite è un **benchmark teorico** (cosa potresti ottenere se elimini i setup); l'Ap reale è il dato che serve per OEE. Tienile separate e confrontale per la diagnosi.

---

## §8 Collegamenti

**Cosa devo sapere PRIMA (prerequisiti):**

- [[Gerarchia dei tempi OEE]] — TS, TA, TC, TO, TON, TOVA: la scala temporale in cui Ap si colloca al primo livello.
- [[Sei grandi perdite (six big losses)]] — Ap "morde" il gruppo A (guasti + setup). Senza questo framework, la divisione tra le tre perdite Ap, Ep, Q resta artificiosa.
- [[MTBF]] / [[MTTR]] — i due indicatori da cui si calcola la disponibilità limite.

**Cosa ne consegue (dipendenze):**

- [[OEE]] — Overall Equipment Effectiveness: $OEE = A_p \cdot E_p \cdot Q$. Ap è il primo fattore moltiplicativo.
- [[TEEP]] — Total Effective Equipment Performance: $TEEP = L \cdot A_p \cdot E_p \cdot Q$. Aggiunge l'efficienza di carico L.
- [[Efficienza prestazioni|Ep]] e [[Tasso di qualità|Q]] — gli altri due coefficienti OEE, che agiscono su livelli successivi della gerarchia tempi.
- [[SMED]] — tecnica per ridurre la quota setup di Ap (Single Minute Exchange of Die).
- [[Manutenzione preventiva]] / [[Manutenzione su condizione]] — strategie per ridurre la quota guasti di Ap (allungare MTBF, accorciare MTTR).
- [[Capacità produttiva (CP)]] — $CP = P \cdot TC \cdot OEE$: Ap entra qui via OEE, e quindi influenza direttamente il dimensionamento dell'impianto.

---

## §9 Auto-verifica

1. **(facile)** Cosa misura la Disponibilità Ap? Quali due voci di perdita "morde"? Qual è il suo intervallo tipico in impianti ben gestiti?
2. **(media)** Scrivi le due formule operative per calcolare Ap (una dal rapporto TO/TC, una dai dati aziendali) e spiega perché sono equivalenti. Cosa cambia tra Ap reale e Ap limite, e quale formula serve per ognuna?
3. **(profonda)** Una pressa ha Ap reale = 88% e Ap limite = 92%. La direzione propone di sostituire il sistema idraulico per portare Ap limite al 96%. È una decisione efficace? Giustifica numericamente quanto Ap reale potrebbe migliorare al massimo, e suggerisci quale altra leva indagare prima di firmare la spesa.