

> [!tldr] In 10 secondi Il **quadro sinottico tempi** è la scomposizione gerarchica del tempo solare in sei livelli decrescenti (TS → TA → TC → TO → TON → TOVA): a ogni passo si sottrae una categoria di perdita, finché resta solo il tempo per cui il cliente è disposto a pagare.

---

## §1 Domanda fondamentale

Se la mia macchina ha 8 760 ore all'anno a disposizione, **quante di queste ore stanno effettivamente generando valore** — e dove finiscono tutte le altre?

Il quadro sinottico è la mappa che traduce questa domanda in una classificazione operativa: un cassetto per ogni tipo di perdita, cosicché poi indici come [[OEE]] e [[TEEP]] possano misurarle separatamente.

---

## §2 Il problema concreto

Una **fab di semiconduttori** a Catania possiede una linea di **fotolitografia** (una sola, costata 18 milioni di euro). I responsabili di produzione devono presentare al CEO un report che spieghi _perché_ la linea ha prodotto solo 4 200 wafer conformi nell'ultimo anno, contro un teorico di circa 12 000.

Il direttore di reparto apre il foglio di lavoro:

- **Tempo solare**: 8 760 h (è un dato fisico, non si discute).
- L'impianto chiude **2 settimane in agosto + tutte le domeniche** → −1 008 h.
- Della restante apertura, **2 turni a settimana sono dedicati a manutenzione preventiva programmata** + ci sono stati periodi di **mancanza ordini in Q1** → altre −1 200 h perse.
- A linea accesa, ci sono stati **guasti per 380 h** e **set-up per cambio reticolo per 450 h**.
- Quando la linea andava, gli operatori la rallentavano spesso per **ispezioni visive non programmate** → si stima un'altra erosione del 12%.
- Infine, il 7% dei wafer prodotti è stato **scartato** dal controllo qualità.

Il dilemma: **se dico solo "abbiamo prodotto 4 200 wafer", il CEO non capisce dov'è il problema**. Devo separare le perdite "per scelta strategica" (ferie, manutenzione) da quelle "per inefficienza operativa" (guasti, scarti). Il quadro sinottico è esattamente il linguaggio che permette di farlo.

---

## §3 La definizione

Il **quadro sinottico tempi** è la rappresentazione grafica e gerarchica della scomposizione del tempo solare in sei livelli, ciascuno ottenuto sottraendo al precedente una specifica categoria di perdita. È il fondamento della metodologia [[OEE]] (Overall Equipment Effectiveness) introdotta da Nakajima nel 1988 nell'ambito del [[TPM]] (Total Productive Maintenance).

### Scomposizione in parti

```
TS    Tempo Solare
 │    [8 760 h/anno — il massimo fisicamente disponibile]
 │
 │    ─ tempo di chiusura impianto
 ▼    (giorni/orari in cui l'impianto NON è accessibile)
TA    Tempo di Apertura
 │    [periodo in cui l'impianto è accessibile alla manodopera]
 │
 │    ─ fermate pianificate (manutenzione preventiva, prove tecnologiche)
 │    ─ fermate per cause esterne (mancanza ordini/MP, scioperi)
 ▼
TC    Tempo di Carico  (loading time / planned operating time)
 │    [tempo per cui la macchina è programmata per lavorare = è "accesa"]
 │
 │    ─ fermate misurabili = "grandi fermate"
 │       (guasti, set-up, riattrezzaggi)
 ▼
TO    Tempo Operativo  (operating time)
 │    [tempo in cui la macchina effettivamente lavora]
 │
 │    ─ fermate non misurabili = "piccole fermate"
 │       (attese materiali, code, micro-stop)
 │    ─ perdite di velocità
 │       (rallentamenti, periodi transitori)
 ▼
TON   Tempo Operativo Netto  (net operating time)
 │    [lavora senza rallentamenti né micro-fermate]
 │
 │    ─ tempo per scarti
 │    ─ tempo per rilavorazioni
 ▼
TOVA  Tempo Operativo a Valore Aggiunto  (valuable operating time)
      [★ unico tempo per cui il cliente è disposto a pagare]
```

### Le sei grandi perdite (six big losses) raggruppate

|Gruppo|Perdita|Si sottrae a →|
|---|---|---|
|**Tempo misurabili**|Guasti|TC → TO|
|**Tempo misurabili**|Set-up e regolazioni|TC → TO|
|**Velocità** (non misurabili)|Tempi morti (micro-stop, attese)|TO → TON|
|**Velocità** (non misurabili)|Riduzione velocità (rallentamenti)|TO → TON|
|**Difetti**|Scarti|TON → TOVA|
|**Difetti**|Rilavorazioni|TON → TOVA|

---

## §4 Come funziona

Il cuore del meccanismo: **ogni livello "promette" al successivo solo ciò che resta dopo aver sottratto una famiglia omogenea di perdite**. La gerarchia non è arbitraria — segue un criterio di "controllabilità crescente":

- **TS → TA**: dipende da scelte di **calendario aziendale** (ferie, turni, festività). Quasi non negoziabile.
- **TA → TC**: dipende da **politiche di manutenzione e mercato** (quanta produzione assegno alla macchina). È una scelta strategica.
- **TC → TO**: dipende dall'**affidabilità tecnica** della macchina e dall'**organizzazione dei cambi prodotto**. È il regno della manutenzione e del SMED.
- **TO → TON**: dipende da **flusso di materiali, code, micro-fermate, rallentamenti**. È il livello più sfuggente perché non viene registrato direttamente da nessun sistema aziendale → si misura _indirettamente_ tramite il [[ritmo standard di produzione]].
- **TON → TOVA**: dipende dalla **qualità del processo**. Tutto ciò che è stato lavorato ma non è conforme è tempo "sprecato".

### Cosa accade se...

- **... salto un livello?** Se confronto direttamente TOVA con TS ottengo il TEEP, che misura "quanto valore estraggo dal tempo che la natura mi regala". È utile per decisioni di investimento (vale la pena duplicare la macchina?). Se invece confronto TOVA con TC ottengo l'OEE, più equo perché esclude le scelte strategiche di calendario.
- **... una perdita è classificata male?** Errore tipico: contare un guasto come "set-up". Numericamente TO non cambia (entrambi si sottraggono allo stesso livello), ma la **diagnosi** è sbagliata: investirò in SMED quando dovrei investire in manutenzione predittiva.
- **... non ho dati storici sui rallentamenti?** Non posso misurare TON direttamente. Lo ricostruisco da $TON = T_{std} \cdot (Q_{cnf} + Q_{scarti} + Q_{rilav})$ dove $T_{std}$ è il tempo standard per pezzo (l'inverso del ritmo di progetto).

---

## §5 Applicazione pratica (metodologia operativa)

Essendo un framework qualitativo, l'applicazione consiste nel **classificare correttamente ogni ora "persa" nel cassetto giusto**. Procedura step-by-step:

### Step 1 — Parti dal tempo solare

Scrivi sempre $TS = 8,760$ h/anno (o frazione corrispondente: 720 h/mese ≈ 30·24, 168 h/settimana, ecc.). È il punto di ancoraggio.

### Step 2 — Sottrai il tempo di chiusura → ottieni TA

Cerca nel calendario aziendale: ferie collettive, weekend non lavorati, festività. **Domanda guida**: "in queste ore, l'impianto è accessibile a _qualcuno_?"

### Step 3 — Sottrai fermate pianificate + cause esterne → ottieni TC

Due famiglie distinte:

- **Pianificate** = decise _internamente_ (manutenzione preventiva, prove, formazione, periodi senza assegnazione di produzione).
- **Cause esterne** = subite (no ordini, no materie prime, scioperi).

**Domanda guida**: "in queste ore, l'azienda _avrebbe voluto_ far girare la macchina?"

### Step 4 — Sottrai guasti + set-up → ottieni TO

Si tratta delle "grandi fermate" misurabili. **Cerca nei registri**: ordini di lavoro di manutenzione correttiva, log di cambio utensile, schede di set-up. **Domanda guida**: "la macchina era programmata per produrre, ma c'è stato un evento _registrato_ che l'ha fermata?"

### Step 5 — Stima Ep (perché TON non si misura direttamente)

Le piccole fermate e i rallentamenti **non sono nei registri**. Per ricavare TON:

$$TON = T_{std} \cdot (Q_{cnf} + Q_{scarti} + Q_{rilav})$$

dove $T_{std} = 1/P^{std}$ è il tempo teorico per pezzo. In pratica si calcola direttamente $E_p = TON/TO$ con la formula indiretta.

### Step 6 — Sottrai tempo scarti + rilavorazioni → ottieni TOVA

$$TOVA = T_{std} \cdot Q_{conformi}$$

### Checklist anti-errore

- [ ] Ogni perdita è stata assegnata a **un solo** livello (no double counting).
- [ ] Le fermate misurabili (guasti, set-up) sono **separate** da quelle non misurabili (rallentamenti, attese).
- [ ] I rallentamenti **non** sono stati confusi con i guasti (i primi sono velocità, i secondi sono tempo).
- [ ] Le rilavorazioni sono contate come _tempo perso_ in TOVA (anche se il prodotto è poi recuperato).
- [ ] La somma di tutti i tempi sottratti + TOVA = TS (verifica chiusura del bilancio).

---

## §6 Domanda tipo esame

> **Domanda orale (o aperta scritta)**: "Spiegare il quadro sinottico dei tempi proposto dalla metodologia OEE. Discutere il significato di ciascun livello e la natura delle perdite che si interpongono tra livelli adiacenti, motivando perché alcune sono dette 'misurabili' e altre no. Concludere chiarendo perché il TOVA viene definito 'l'unico tempo per cui il cliente è disposto a pagare'."

### Traccia di risposta strutturata

**Punto 1 — Inquadramento (30 sec)** Citare contesto: metodologia OEE, origine giapponese (Istituto JIPM, anni '70), introduzione negli USA da Nakajima (1988) nell'ambito del TPM. Obiettivo: diagnosticare le inefficienze a partire dall'idea che ogni perdita di produzione è riconducibile a un uso imperfetto del tempo.

**Punto 2 — La gerarchia a sei livelli (cuore della risposta)** Snocciolarli _in ordine_ con la causa di sottrazione:

- TS (8 760 h) → −chiusura impianto → **TA**
- TA → −fermate pianificate e cause esterne → **TC**
- TC → −guasti e set-up → **TO**
- TO → −micro-fermate e rallentamenti → **TON**
- TON → −scarti e rilavorazioni → **TOVA**

**Punto 3 — Le sei grandi perdite e la dicotomia misurabili/non misurabili**

- _Misurabili_: guasti e set-up. Lasciano traccia in documenti contabili (ordini di intervento, schede di cambio prodotto).
- _Non misurabili_: micro-fermate e rallentamenti. Non c'è registrazione: l'operatore che rallenta una macchina per un'avaria minore non lo segna da nessuna parte. Si stimano _indirettamente_ tramite il ritmo standard.
- _Da difetti_: scarti e rilavorazioni. Misurabili dai dati di qualità.

**Punto 4 — Perché TOVA è il "tempo che il cliente paga"** Il cliente acquista solo prodotto **conforme**. Ogni altra ora — incluse le manutenzioni necessarie, i set-up inevitabili, persino i rallentamenti — è un costo che l'azienda assorbe nel prezzo ma che non aggiunge valore percepito. La metafora chiave: è la "linea di galleggiamento" tra spreco e valore.

**Punto 5 — Aggancio agli indici (chiusura)** Da questa scomposizione discendono naturalmente:

- $L = TC/TA$ — efficienza di carico
- $A_p = TO/TC$ — disponibilità
- $E_p = TON/TO$ — efficienza prestazioni
- $Q = TOVA/TON$ — tasso di qualità
- $OEE = A_p \cdot E_p \cdot Q = TOVA/TC$
- $TEEP = L \cdot A_p \cdot E_p \cdot Q = TOVA/TA$

### Variante numerica (se l'esaminatore chiede dati)

Riprendendo il caso fab semiconduttori del §2:

- $TS = 8,760$ h
- $TA = 8,760 - 1,008 = 7,752$ h
- $TC = 7,752 - 1,200 = 6,552$ h → $L = 6,552/7,752 \approx 84{,}5%$
- $TO = 6,552 - 380 - 450 = 5,722$ h → $A_p = 5,722/6,552 \approx 87{,}3%$
- $TON = 5,722 \cdot 0{,}88 \approx 5,036$ h → $E_p = 88%$
- $TOVA = 5,036 \cdot 0{,}93 \approx 4,684$ h → $Q = 93%$
- $OEE = 87{,}3% \cdot 88% \cdot 93% \approx 71{,}4%$

---

## §7 Errori comuni

> [!warning] ❌ Confondere TS con il tempo standard di produzione Il PDF del corso usa **TS** sia per _tempo solare_ (Cap.3 §3.2.4) sia per _tempo standard di attraversamento_ (Cap.3 §3.2.2). Sono concetti completamente diversi: il primo è 8 760 h/anno, il secondo è il tempo per pezzo (es. 36 secondi/wafer). **Come evitarlo**: nel contesto OEE/quadro sinottico, TS = tempo solare; nel contesto della formula $E_p$, T_std = ritmo standard.

> [!warning] ❌ Mettere la manutenzione preventiva nel cassetto sbagliato La manutenzione **preventiva** (programmata) si sottrae a TA per ottenere TC: è una _fermata pianificata_. La manutenzione **correttiva** (guasto) si sottrae a TC per ottenere TO: è una _fermata misurabile per guasto_. Confonderle inquina la diagnosi: sembrerà che la macchina sia inaffidabile quando in realtà la stai mettendo a riposo per cura.

> [!warning] ❌ Pensare che TOVA = tempo di lavoro "produttivo" Anche scarti e rilavorazioni sono "lavorazione effettiva", la macchina sta girando. Ma per TOVA contano solo i pezzi **conformi**. Uno scarto consuma tempo operativo netto ma non aggiunge valore. **Come evitarlo**: ricordare la regola del cliente — paga solo ciò che riceve come buono.

---

## §8 Collegamenti

### Prerequisiti (cosa devo sapere PRIMA)

- [[Potenzialità produttiva]] — il concetto di P [pz/h] su cui si appoggiano i ritmi standard
- [[Sei grandi perdite (six big losses)]] — la classificazione delle inefficienze che genera la gerarchia
- [[TPM Total Productive Maintenance]] — cornice metodologica originale (Nakajima 1988)
- [[Misura delle prestazioni]] — il principio "diagnosi → terapia" che giustifica la scomposizione

### Conseguenze (cosa ne consegue)

- [[Efficienza di carico L]] — primo indice derivato (TC/TA)
- [[Disponibilità Ap]] — secondo indice (TO/TC), legata a [[MTBF]] e [[MTTR]]
- [[Efficienza delle prestazioni Ep]] — terzo indice (TON/TO), calcolata indirettamente
- [[Tasso di qualità Q]] — quarto indice (TOVA/TON)
- [[OEE Overall Equipment Effectiveness]] — Ap·Ep·Q = TOVA/TC
- [[TEEP]] — L·Ap·Ep·Q = TOVA/TA
- [[Capacità produttiva (CP)]] — CP = P·TOVA = P·TC·OEE = P·TA·TEEP
- [[Potenzialità di mix]] — usa lo stesso framework su prodotti multipli

### Mappa di chapter

- [[03 Cap3 - Prestazioni dei sistemi di produzione]]
- [[00 Impianti - MOC]]

---

## §9 Auto-verifica

1. **(facile)** Quanto vale TS in ore all'anno e perché è un valore fisso?
    
2. **(media)** Una linea ha registrato: 200 h di manutenzione preventiva, 150 h di guasti, 80 h di set-up, 5% di scarti, una stima di Ep = 90%. A quale livello del quadro sinottico va sottratta ciascuna di queste perdite, e in che ordine?
    
3. **(profonda)** Perché le "perdite di velocità" (TO → TON) sono dette _non misurabili_, mentre i guasti e i set-up (TC → TO) sono _misurabili_? Quale conseguenza pratica ha questa asimmetria sul modo in cui si calcola Ep rispetto ad Ap? E perché, in ultima analisi, questa asimmetria _non_ compromette il calcolo dell'OEE complessivo?