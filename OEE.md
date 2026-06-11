# Overall Equipment Effectiveness

> [!summary] In 10 secondi L'OEE è il **prodotto di tre coefficienti** (disponibilità · efficienza prestazioni · qualità) che ti dice quale frazione del **tempo di carico** è stata effettivamente "venduta al cliente". Misura quanto un impianto sta sfruttando il tempo in cui _dovrebbe_ produrre.


---

## §1 Domanda fondamentale

> Dato un impianto che è acceso e programmato per produrre, **quale frazione di quel tempo si è realmente trasformata in pezzi conformi venduti al cliente?**

Le altre frazioni sono perdite — e l'OEE le rende visibili una per una, in modo che tu sappia _dove_ intervenire (non solo _quanto_ sei inefficiente).

---

## §2 Il problema concreto

Pensa allo stabilimento di **verniciatura scocche** di una casa automotive nel cuneese. La linea ha una potenzialità di targa di **30 scocche/ora**, lavora su 2 turni da 8 ore per 5 giorni a settimana.

Il direttore di stabilimento si trova davanti due dati:

- **Capacità installata teorica**: 30 × 16 × 5 = 2.400 scocche/settimana
- **Output reale dichiarato dal capoturno**: ~1.500 scocche/settimana conformi

Il dilemma: **dove sono finite le 900 scocche mancanti?** Sono andate perdute in:

- guasti del robot di spruzzatura?
- cambio colore (set-up)?
- micro-fermate per intasamento ugelli?
- velocità ridotta perché un robot ha problemi di calibrazione?
- scocche con colature mandate in rilavorazione?
- scocche scartate per craterizzazione della vernice?

Senza un indicatore strutturato, il direttore può solo _intuire_. Decide di investire 800k€ in una nuova cabina automatica, ma non sa se il problema fosse davvero la cabina o la pulizia degli ugelli. **L'OEE risolve questo dilemma**: scompone le perdite per categoria e indica _dove_ il miglioramento è più redditizio.

---

## §3 La definizione

L'OEE è definito come:

$$OEE = \frac{\text{TOVA}}{TC} = A_p \cdot E_p \cdot Q$$

dove:

- **TOVA** = tempo operativo a valore aggiunto (solo pezzi conformi)
- **TC** = tempo di carico (impianto acceso e programmato)

**Scomposizione in tre fattori**:

|Coefficiente|Formula|Cosa misura|Range tipico|
|---|---|---|---|
|**A_p** Disponibilità|TO / TC|Quanto del tempo programmato la macchina ha _effettivamente prodotto_ (perdite: guasti, set-up)|> 90%|
|**E_p** Efficienza prestazioni|TON / TO|Quanto la macchina è andata _alla velocità giusta_ (perdite: microfermate, rallentamenti)|linea 0.80–0.95 / reparti 0.65–0.80|
|**Q** Tasso di qualità|TOVA / TON|Quanto del lavorato è _conforme_ (perdite: scarti, rilavorazioni)|95–100%|

Origine storica: introdotto negli anni '70 dal **Japan Institute of Plant Maintenance** all'interno della filosofia **TPM**; portato in Occidente da **Nakajima (1988)**.

---

## §4 Come funziona

**Cuore del concetto**: l'OEE fa una "cascata di sconti" sul tempo di carico — ogni coefficiente sottrae una categoria di perdita, e quello che rimane in fondo è il tempo che il cliente paga davvero.

```
TC   Tempo di carico  (macchina accesa e programmata)
      │
      │ × Ap    ←  − guasti, set-up
      ▼
TO   Tempo operativo
      │
      │ × Ep    ←  − microfermate, rallentamenti
      ▼
TON  Tempo operativo netto
      │
      │ × Q     ←  − scarti, rilavorazioni
      ▼
TOVA Tempo operativo a valore aggiunto    ← QUESTO il cliente paga

OEE  =  TOVA / TC  =  Ap · Ep · Q
```

I tre fattori catturano esattamente le **sei grandi perdite** (six big losses) di Nakajima:

- **A_p** → guasti, set-up/regolazioni
- **E_p** → microfermate, perdite di velocità
- **Q** → scarti, rilavorazioni

### Cosa accade se...

**...non parto da TC ma da TA (tempo apertura)?** → Stai calcolando il [[TEEP|TEEP - Total Effective Equipment Performance]], che è OEE × L (efficienza di carico). Il TEEP include anche le fermate pianificate; l'OEE no. _Mnemonic_: TEEP è "totale" (tutto il tempo accessibile), OEE è "operativo" (solo quando dovevi produrre).

**...non conosco le rilavorazioni?** Approssimi E_p per **difetto** e Q per **eccesso**. La cosa interessante: il prodotto E_p · Q **è invariante** rispetto a questa incertezza, quindi l'OEE complessivo resta corretto. Cambia solo l'attribuzione interna delle perdite. → vedi §7.

**...l'OEE viene basso (es. 50%)?** Non guardare il numero da solo: guarda _quale dei tre coefficienti_ tira giù il prodotto. Se A_p = 60% → problema di manutenzione/setup. Se Q = 70% → problema di processo. La diagnosi sta nei **fattori**, non nel totale.

---

## §5 Applicazione pratica

### Formula operativa

$$OEE = A_p \cdot E_p \cdot Q$$

con stime tipiche (specie quando mancano dati sulle rilavorazioni):

$$\tilde{E}_p = \frac{T_{std} \cdot (Q_{cnf} + Q_{scr})}{TO} \quad ; \quad \tilde{Q} = \frac{Q_{cnf}}{Q_{cnf} + Q_{scr}}$$

### Procedura passo-passo

1. **Definisci l'orizzonte temporale** (mese, anno, turno) — l'OEE va sempre riferito a un periodo.
2. **Calcola TA** = tempo solare − chiusura impianto.
3. **Calcola TC** = TA − fermate pianificate − cause esterne (manutenzione preventiva, scioperi, mancanza ordini).
4. **Calcola TO** = TC − tempo guasti − tempo set-up. Da qui ricavi $A_p = TO/TC$.
5. **Calcola TON** stimando il tempo standard: $TON = T_{std} \cdot (Q_{cnf} + Q_{scr})$. Da qui $\tilde{E}_p = TON/TO$.
6. **Calcola Q** = $Q_{cnf} / (Q_{cnf} + Q_{scr})$ (se non hai rilavorazioni; altrimenti includile a denominatore).
7. **Moltiplica**: $OEE = A_p \cdot \tilde{E}_p \cdot \tilde{Q}$.

### Checklist anti-errore

- [ ] Ho dichiarato chiaramente l'**orizzonte temporale**?
- [ ] Ho separato fermate **pianificate** (vanno in TA→TC) da fermate **per guasti/setup** (vanno in TC→TO)?
- [ ] Il tempo standard $T_{std}$ è il **reciproco** della potenzialità di targa? ($T_{std} = 1/P_{std}$)
- [ ] Sto usando le **stesse unità di tempo** per tutti i fattori (h con h, min con min)?
- [ ] Ho dichiarato esplicitamente se le rilavorazioni sono **note**, **stimate** o **ignote**?
- [ ] Il risultato è coerente coi **range di letteratura**? (linea: $A_p > 0{,}9$, $E_p \in [0{,}80; 0{,}95]$, $Q \in [0{,}95; 1{,}00]$)

---

## §6 Esercizio tipo esame

> **Linea di blistering** (settore farmaceutico). Un'azienda produce blister di compresse antinfiammatorie su una linea che lavora **300 giorni/anno, 24h/24**. A fine luglio è prevista una manutenzione generale di 15 giorni. Ogni **8 giorni** di produzione si effettua una sanificazione del nastro che richiede **6 ore**. Nello scorso mese si sono registrate **5 ore** di fermo per guasti meccanici. Ogni cambio formato (4 volte al mese) richiede **45 minuti** di riattrezzaggio. La potenzialità di targa è **600 blister/h**. Nell'ultimo anno la produzione conforme è stata di **3.700.000 blister**, gli scarti **240.000 blister**. Le rilavorazioni sono ignote. **Calcolare l'OEE annuo**.

### Soluzione passo-passo

**Step 1 — Tempo apertura** $$T_A = 300 \text{ gg} \cdot 24 \text{ h/gg} = 7.200 \text{ h}$$ (la manutenzione generale di 15 giorni è già esclusa: lavoro 300 gg, non 365)

**Step 2 — Fermate pianificate (sanificazioni)** Una sanificazione ogni 8 giorni → in 300 gg ho 300/8 = 37,5 sanificazioni: $$T_{san} = 37{,}5 \cdot 6 = 225 \text{ h}$$

**Step 3 — Tempo di carico** $$T_C = T_A - T_{san} = 7.200 - 225 = 6.975 \text{ h}$$ $$L = T_C / T_A = 6.975/7.200 = 96{,}9$$

**Step 4 — Tempo guasti (estrapolato all'anno)** $$t_{gua} = \frac{5 \text{ h}}{30 \text{ gg}} \cdot 300 \text{ gg} = 50 \text{ h}$$

**Step 5 — Tempo set-up** 4 cambi/mese × 12 mesi × 0,75 h = 36 h.

**Step 6 — Tempo operativo e disponibilità** $$T_O = T_C - t_{gua} - t_{set} = 6.975 - 50 - 36 = 6.889 \text{ h}$$ $$A_p = T_O / T_C = 6.889/6.975 = 98{,}77$$

**Step 7 — Efficienza prestazioni stimata** $$T_{std} = 1/600 \text{ h/blister}$$ $$TON = T_{std} \cdot (Q_{cnf} + Q_{scr}) = \frac{1}{600}(3.700.000 + 240.000) = 6.566{,}7 \text{ h}$$ $$\tilde{E}_p = TON/T_O = 6.566{,}7/6.889 = 95{,}32$$ _(stima per difetto, le rilavorazioni vere alzerebbero il numeratore)_

**Step 8 — Tasso di qualità stimato** $$\tilde{Q} = \frac{3.700.000}{3.700.000 + 240.000} = 93{,}91$$ _(stima per eccesso, le rilavorazioni vere abbasserebbero il denominatore)_

**Step 9 — OEE** $$\boxed{OEE = A_p \cdot \tilde{E}_p \cdot \tilde{Q} = 0{,}9877 \cdot 0{,}9532 \cdot 0{,}9391 = 88{,}4}$$

> [!note] Punto chiave Anche se $\tilde{E}_p$ e $\tilde{Q}$ presi singolarmente sono _sbagliati_ (uno per difetto, uno per eccesso), il loro prodotto $\tilde{E}_p \cdot \tilde{Q}$ **coincide** col prodotto vero $E_p \cdot Q$. Quindi l'OEE è corretto, **ma non si può discutere su quale dei due fattori sia il problema** finché non si misurano le rilavorazioni.

### Variante "e se..."

> _E se cambiasse il numero di sanificazioni, passando da una ogni 8 a una ogni 4 giorni?_

$T_{san} = 75 \cdot 6 = 450$ h → $T_C = 6.750$ h → $L = 93{,}75$. $A_p$ cambia poco (denominatore TC cambia, ma anche $T_O$ scala simile): $A_p = (6.750-86)/6.750 = 98{,}73$. $\tilde{E}_p$ cambia perché $T_O$ è diminuito a parità di TON richiesto (assumendo stessa produzione): $\tilde{E}_p = 6.566{,}7 / 6.664 = 98{,}54$. **OEE_nuovo ≈ 0,9873 · 0,9854 · 0,9391 = 91,4%**. Sembra paradossale: aumento le sanificazioni e l'OEE _cresce_? No: l'OEE è cresciuto perché le sanificazioni le ho spostate dentro le fermate pianificate (escluse da TC). Il **TEEP**, che parte da TA, sarebbe sceso. → Lezione: OEE e TEEP rispondono a domande diverse. Per giudicare un sistema globalmente serve guardare entrambi.

---

## §7 Errori comuni

> [!warning] ❌ Errore 1 — Confondere OEE e TEEP Mettere le fermate pianificate (manutenzione preventiva, festività) tra le perdite di disponibilità, ottenendo un OEE artificialmente basso. **Perché è sbagliato**: $A_p$ misura solo perdite _non programmate_ dentro $T_C$. Le fermate pianificate vivono nel passaggio $T_A \to T_C$ (efficienza di carico $L$). **Come evitarlo**: chiediti sempre "questa fermata era nel piano di produzione di lunedì mattina?" Se sì → fermata pianificata, esce da TC. Se no → guasto o setup, entra in $A_p$.

> [!warning] ❌ Errore 2 — Calcolare E_p come (Q_cnf · T_std) / TO ignorando gli scarti Mettere a numeratore solo il tempo dei conformi sottostima brutalmente $E_p$. **Perché è sbagliato**: anche gli scarti hanno consumato tempo macchina alla velocità di progetto. $E_p$ misura _velocità_, non _qualità_ — quella è già contata in $Q$. **Come evitarlo**: numeratore di $E_p$ = $T_{std} \cdot$ (tutto ciò che è stato lavorato) = $T_{std} \cdot (Q_{cnf} + Q_{scr} + Q_{ril})$.

> [!warning] ❌ Errore 3 — Trattare $\tilde{E}_p$ e $\tilde{Q}$ come fossero i valori veri quando le rilavorazioni sono ignote Concludere che "il problema è la qualità" basandosi su $\tilde{Q}$ stimato, quando in realtà le rilavorazioni nascoste lo gonfiano. **Perché è sbagliato**: $\tilde{Q}$ è una stima per **eccesso**, $\tilde{E}_p$ per **difetto**. Il prodotto è giusto, i singoli no. **Come evitarlo**: in assenza di dati sulle rilavorazioni, **non fare diagnosi sui singoli coefficienti** — usa solo il prodotto. Se vuoi diagnosticare, prima costruisci un sistema di rilevazione delle rilavorazioni.

---

## §8 Collegamenti

### Prerequisiti (cosa devi sapere PRIMA)

- [[Quadro sinottico tempi]] — la cascata dei tempi è il fondamento
- [[Disponibilità (Ap)]] · [[Efficienza prestazioni (Ep)]] · [[Tasso di qualità (Q)]] — i tre coefficienti che compongono l'OEE
- [[Sei grandi perdite (six big losses)]] — la classificazione Nakajima delle perdite
- [[Total Productive Maintenance (TPM)]] — la cornice metodologica in cui nasce l'OEE
- [[Potenzialità produttiva (P)]] — serve per ricavare il tempo standard $T_{std}=1/P^{std}$

### Dipendenze (cosa ne consegue)

- [[TEEP]] — versione che parte da TA invece che TC; OEE × L
- [[Capacità produttiva (CP)|Capacità produttiva (CP)]] — $CP = P \cdot T_C \cdot OEE$ è la capacità reale
- [[MTBF e MTTR]] — usati per stimare $A_p$ a priori (disponibilità limite)
- [[Potenzialità di mix]] — quando ci sono più prodotti, il $T_{std}$ diventa pesato sul mix
- [[03 Prestazioni dei sistemi di produzione]] — MOC capitolo

---

## §9 Auto-verifica

1. **(facile)** Quali sono i tre coefficienti che compongono l'OEE e quale categoria di perdite cattura ciascuno?
2. **(media)** Perché $E_p$ va calcolata includendo gli scarti al numeratore e non solo i conformi? E perché invece $Q$ usa solo i conformi al numeratore?
3. **(profonda)** Se non conosco le rilavorazioni, posso comunque calcolare un OEE corretto? Su cosa _non_ posso fare diagnosi e perché? Cosa cambierebbe se misurassi le rilavorazioni _senza_ cambiare nulla nel processo reale?