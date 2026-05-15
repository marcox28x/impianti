
---

## tags: [impianti, cap3, prestazioni, OEE, quantitativo] tipo: atomic classificazione: quantitativo

# Efficienza di carico — L

> [!tldr] In 10 secondi **L = TC / TA**: quanta parte del tempo in cui l'impianto è _aperto_ è stata effettivamente _programmata_ per produrre. Misura la qualità della **scelta gestionale** di assegnazione, non il funzionamento delle macchine.

---

## §1 Domanda fondamentale

Dato un impianto che potrebbe essere usato per X ore (TA), **quante ho davvero deciso di farlo lavorare** (TC), al netto delle fermate che ho pianificato io e di quelle imposte dall'esterno?

L risponde a: _"sto sfruttando il tempo che ho a disposizione, oppure lo sto buttando in scelte gestionali sbagliate?"_

---

## §2 Il problema concreto

Una multinazionale farmaceutica ha una **linea di blisteraggio per compresse** nel sito di produzione solidi. Il responsabile di reparto ti porta i dati del mese scorso e ti chiede:

> "La linea è aperta 22 giorni al mese, 16 ore al giorno (due turni). Però abbiamo:
> 
> - **22 ore** di sanificazione GMP (1h/giorno, obbligo regolatorio prima del cambio lotto)
> - **8 ore** di convalida di un nuovo formato di blister
> - **4 ore** di prove tecnologiche per un principio attivo nuovo
> - **16 ore** persi per sciopero del fornitore di alluminio packaging
> 
> La direzione vuole capire **quanto stiamo davvero programmando produzione** rispetto al tempo disponibile."

Il dilemma: tutti questi tempi sono _fermi_, ma non tutti hanno la stessa natura. La sanificazione è obbligatoria, lo sciopero è subìto, le prove tecnologiche sono una scelta. Mescolarli con guasti e set-up porterebbe a confondere problemi di **gestione del tempo** con problemi di **affidabilità della macchina** → non sapremmo dove intervenire. Serve un indice che isoli la prima cosa.

→ Quell'indice è **L**.

---

## §3 La definizione

**Efficienza di carico (Load — L)**: rapporto tra tempo di carico e tempo di apertura impianto.

$$L = \frac{T_C}{T_A} = \frac{T_A - T_{\text{ferm.pianif.}} - T_{\text{cause est.}}}{T_A}$$

### Scomposizione

```
TA  ── tempo apertura impianto (TS − chiusure)
 │
 ├── fermate pianificate    (manut. preventiva, prove tecnologiche,
 │                            periodi senza programmazione produttiva)
 ├── cause esterne          (mancanza ordini, mancanza MP, scioperi,
 │                            imprevisti esterni)
 │
 └── TC ── tempo di carico (planned operating time)
```

L vive in **§3 Cap3** del corso, dentro la metodologia OEE/TEEP. È il **primo gradino** della scomposizione gerarchica dei tempi (TS → TA → **TC** → TO → TON → TOVA).

Numero puro, ∈ [0,1], spesso espresso in %. Adimensionale.

---

## §4 Come funziona

> **Il cuore in una frase**: L misura _l'efficacia del sistema di assegnazione della produzione_ — non come la macchina lavora, ma come io decido di tenerla impegnata.

### Come si connettono le parti

- **TA** è il tempo in cui l'impianto _potrebbe_ lavorare (porte aperte, infrastruttura disponibile).
- Da lì sottraggo due categorie di tempo improduttivo che hanno una caratteristica comune: **non c'entrano con la macchina**, sono decisioni o eventi a livello di programmazione/contesto.
    - **Fermate pianificate** → scelte interne (manut. preventiva, prove, gap di programmazione)
    - **Cause esterne** → eventi che subisco (scioperi, mancanza ordini, mancanza MP)
- Quel che resta è **TC**, il tempo che _ho deciso_ di destinare alla produzione effettiva.

### Cosa accade se…

- **L = 1** → ogni minuto di apertura è programmato per produrre. Probabilmente la programmazione è ottima, oppure (caso reale) sto sottostimando le fermate pianificate.
- **L molto bassa (es. 0.4)** → due possibilità opposte:
    - _patologico_: ho programmazione caotica, mancano ordini, fornitori instabili → da correggere
    - _fisiologico_: dimensionamento con TA volutamente sovrabbondante (es. impianto a 1 turno con TA "potenziale" di 3 turni) → L bassa ma scelta strategica
- **L confronto tra reparti dello stesso sito** → utile per capire chi pianifica meglio.
- **L confronto tra siti diversi** → da prendere con le pinze: dipende anche da regime turni e tipo di prodotto.

---

## §5 Applicazione pratica

### Formula operativa

$$L = \frac{T_C}{T_A} \quad\text{con}\quad T_C = T_A - \sum t_{\text{pianif.}} - \sum t_{\text{cause est.}}$$

### Procedura passo-passo

1. **Definisci l'orizzonte temporale** (giorno / settimana / mese / anno) → fissa il calendario di analisi.
2. **Calcola TA**: parti dal tempo solare (TS) e sottrai le chiusure ufficiali dell'impianto (notti, weekend non lavorati, ferie aziendali). $\to$ TA = giorni_lavorativi × ore_apertura_giornaliera
3. **Elenca tutte le fermate pianificate** (interne):
    - manutenzione preventiva
    - prove tecnologiche, qualifiche, validazioni
    - periodi programmati senza produzione (es. macchina ferma per scelta)
    - sanificazioni / setup ricorrenti **se pianificati a calendario**
4. **Elenca le cause esterne**:
    - scioperi, mancanza MP, mancanza ordini, blackout, eventi non controllabili
5. **Calcola TC** = TA − Σ(pianificate) − Σ(esterne).
6. **L = TC / TA**, esprimi in %.

### Checklist anti-errore

- [ ] Le ore di **guasto** NON sono qui (vanno in Ap).
- [ ] I **set-up** di cambio prodotto NON sono qui (vanno in Ap, sono "fermate misurabili").
- [ ] Le **rilavorazioni** e gli **scarti** NON sono qui (vanno in Q).
- [ ] I **rallentamenti** della macchina NON sono qui (vanno in Ep).
- [ ] Verifica unità di misura coerenti tra TA e fermate (tutto in ore o tutto in minuti).
- [ ] Se sei al **primo dimensionamento** (impianto non ancora in produzione), prendi L da impianti simili (benchmark).

---

## §6 Esercizio tipo esame

### Traccia

> Un'azienda automotive ha una **linea di verniciatura scocche** con i seguenti dati mensili:
> 
> - Apertura: **20 giorni × 24 h** (3 turni)
> - Manutenzione preventiva pianificata: **2 turni** (16 h)
> - Prove di un nuovo colore di vernice (programmate): **6 h**
> - Sciopero del trasportatore di vernici: **12 h**
> - Guasti del robot verniciatore: **18 h** _(distrattore)_
> - Cambi colore (set-up): **24 h** _(distrattore)_
> 
> Calcolare l'efficienza di carico L.

### Soluzione passo-passo

**Step 1 — TA** $$T_A = 20 \cdot 24 = 480 \text{ h}$$

**Step 2 — Identificare cosa rientra in L** Solo fermate pianificate + cause esterne. **Escludo guasti e set-up** (vanno in Ap, non in L).

- Fermate pianificate: 16 (manut. prev.) + 6 (prove colore) = **22 h**
- Cause esterne: 12 (sciopero fornitore) = **12 h**

**Step 3 — TC** $$T_C = 480 - 22 - 12 = 446 \text{ h}$$

**Step 4 — L** $$L = \frac{446}{480} = 0{,}9292 \approx 92{,}9$$

> [!check] Risposta L ≈ **92,9 **. La direzione sta sfruttando bene il tempo disponibile in termini di programmazione/cause esterne. I 18h di guasto e i 24h di setup sono problemi reali, ma di natura diversa → andranno a deprimere Ap, non L.

### Variante "e se…"

> **E se l'azienda decidesse di passare da 3 turni a 2 turni** (chiudendo 8h/giorno per scelta strategica), mantenendo gli stessi eventi?

Due strade interpretative — ed è qui che si gioca la comprensione:

- **Opzione A — riduco TA**: le 8h chiuse sono _chiusura impianto_, quindi escono dal TA.
    
    - TA = 20 × 16 = 320 h
    - Fermate pianificate ed esterne (rimodulate): 22 + 12 = 34 h
    - L = (320−34)/320 = **89,4 %**
    - L scende perché il denominatore si è ridotto più del numeratore.
- **Opzione B — mantengo TA = 480 e considero le 8h come "fermata pianificata"**:
    
    - TC = 480 − (22+160+12) = 286 h
    - L = 286/480 = **59,6 %**

> [!info] Quale è giusta? **L'opzione A è quella corretta secondo la definizione del corso**: il tempo di chiusura impianto va sottratto al TS _prima_ di ottenere TA. L'opzione B sarebbe sensata solo se l'impianto fosse formalmente aperto ma non programmato — ed è proprio il tipo di scelta che differenzia un'analisi seria da una superficiale.

---

## §7 Errori comuni

> [!warning] ❌ Errore 1 — Mettere i guasti dentro L _"La macchina si è rotta per 5 ore, le tolgo dal TC."_ **Perché è sbagliato**: i guasti sono **fermate misurabili** legate all'**affidabilità** della macchina, non alla programmazione. Vanno nella **Disponibilità (Ap)**. **Come evitarlo**: tieni a mente la regola → _L = scelte gestionali; Ap = comportamento macchina_.

> [!warning] ❌ Errore 2 — Includere L nel calcolo dell'OEE _"OEE = L · Ap · Ep · Q"_ — sbagliato. **Perché è sbagliato**: OEE parte dal tempo di **carico** (TC), non dall'apertura. L è già "fuori scena" quando entriamo in OEE. La formula corretta è:
> 
> - **OEE = Ap · Ep · Q** (parte da TC)
> - **TEEP = L · Ap · Ep · Q** (parte da TA) **Come evitarlo**: ricorda la mnemonica → _OEE = "Effectiveness", parte dalla macchina; TEEP = "Total", parte dall'orologio del calendario_.

> [!warning] ❌ Errore 3 — Pensare che L bassa sia sempre patologica _"L = 50%, quindi stiamo lavorando male."_ **Perché è sbagliato**: una L bassa può derivare da una **scelta dimensionale strategica** (es. impianto pensato per assorbire picchi di domanda, oggi a regime ridotto) o da **vincoli normativi** (sanificazioni GMP nel farmaceutico). Va sempre **contestualizzata**. **Come evitarlo**: prima di giudicare L, chiediti _"il valore basso viene da scelte mie o da inefficienze?"_

---

## §8 Collegamenti

### Prerequisiti (da sapere PRIMA)

- [[Quadro sinottico tempi]]
- [[Sei grandi perdite (six big losses)]] — quadro generale delle perdite OEE
- [[Fermate pianificate vs cause esterne]]

### Conseguenze (cosa viene DOPO)

- [[Disponibilità (Ap)]] — gradino successivo nella cascata dei tempi
- [[Efficienza prestazioni - Ep]]
- [[Tasso di qualità (Q)]]
- [[OEE]] — non include L (parte da TC)
- [[TEEP]] — include L (= L·Ap·Ep·Q)
- [[Capacità produttiva (CP)]] — uso tipico: CP = P · TA · TEEP

### Trasversali

- [[03 Cap3 - Prestazioni dei sistemi di produzione]]
- [[Esempio Gragnano - calcolo OEE mix]]
- [[Esempio nylon - linea continua]]

---

## §9 Auto-verifica

1. **Base** → Qual è la formula di L e cosa rappresentano numeratore e denominatore?
2. **Discriminazione** → Le seguenti perdite di tempo: (a) manutenzione preventiva, (b) guasto improvviso, (c) sciopero, (d) cambio attrezzaggio, (e) rallentamento operatore. Quali pesano su L? Per le altre, dove vanno?
3. **Profondità** → Un impianto ha L = 95% e Ap = 60%. Un secondo impianto ha L = 60% e Ap = 95%. Hanno entrambi TC·Ap simili. Su quale dei due intervieni prima e perché? _(Suggerimento: l'intervento per migliorare L è di natura diversa rispetto a quello per migliorare Ap — uno tocca la pianificazione/contratti, l'altro tocca manutenzione/macchine.)_