---
aliases:
  - "Flow Shop"
  - "Flow-shop"
---

> [!tldr] In 10 secondi Il **flow shop** è una soluzione impiantistica in cui le macchine sono disposte **in sequenza fissa** seguendo il ciclo tecnologico di un prodotto: un grezzo entra a un'estremità e ne esce un finito. È la naturale evoluzione della [[Group Technology]] quando i volumi salgono al punto da giustificare l'automazione spinta.

---

## §1 Domanda fondamentale

**Come organizzo le macchine quando devo produrre tantissimi pezzi quasi identici, in modo da massimizzare l'efficienza e minimizzare i tempi di attraversamento, anche a costo di sacrificare la flessibilità?**

---

## §2 Il problema concreto

Immagina lo stabilimento **Volkswagen di Salzgitter** (settore automotive). Devono produrre il **basamento motore** del 1.5 TSI: ne servono **2.400 al giorno**, sempre lo stesso pezzo, per 5 anni di vita commerciale del modello.

Il ciclo tecnologico del basamento è **rigidamente sequenziale**:

```
fresatura piano superiore → alesatura cilindri → 
finitura specchio → foratura testate → maschiatura → 
lavaggio → controllo dimensionale → marcatura
```

8 operazioni, sempre nello stesso ordine, sempre sullo stesso oggetto, per milioni di pezzi.

**Il dilemma:**

- Se uso un [[Job Shop]] → reparto frese, reparto alesatrici, reparto foratrici… il basamento gira per tutto il capannone, attraversa code, accumula WIP, tempi di attraversamento di giorni invece di minuti. **Spreco follia in trasporti e attese.**
- Se uso una cella di [[Group Technology]] → meglio, ma le macchine sono ancora general-purpose. Non posso spingere l'automazione al massimo perché la cella deve restare un minimo flessibile.
- **C'è qualcosa di meglio?** Sì: dispongo le 8 macchine in fila, le collego con un trasporto automatico, e installo macchine _speciali_ (non più general-purpose) progettate solo per quell'operazione su quel pezzo. Risultato: **un basamento finito ogni 36 secondi**, 24/7.

Questo è il flow shop.

---

## §3 La definizione

Il **flow shop** è un'organizzazione produttiva in cui i macchinari sono disposti in **sequenza fissata dal ciclo tecnologico (routing) del prodotto**. I pezzi vengono movimentati su sistemi di trasporto automatizzati che collegano le stazioni; il sistema costituisce un **insieme inscindibile**: entra il grezzo, esce il finito.

**Scomposizione in parti:**

|Componente|Ruolo|
|---|---|
|**Sequenza fissa di stazioni**|ogni stazione = una operazione del routing, niente alternative|
|**Macchine specializzate**|non più general-purpose; ottimizzate per una operazione su una famiglia ristretta di prodotti|
|**Material handling automatizzato**|nastri, transfer, robot, AGV, "tavola rotante" — collegano fisicamente le stazioni|
|**Sistemi di load/unload a fine linea**|inizio e fine sono "cordoni ombelicali" verso l'esterno|
|**Inscindibilità**|il sistema funziona come una _macchina unica_: si guasta una stazione → si ferma la linea|

**Configurazioni geometriche tipiche:** linea rettilinea, linea a U, zig-zag, **tavola rotante** (per pezzi piccoli con poche stazioni, dove la rotazione del piatto fa fare il "giro" al pezzo).

---

## §4 Come funziona

**Il cuore in una frase:** il flow shop trasforma il _fluire dei pezzi_ da problema di programmazione (nel job shop) in problema fisico-meccanico (basta che il nastro vada).

**Come si connettono le parti:**

1. Il **routing del prodotto è fissato** → il layout è "scolpito" su quel routing → ogni macchina è in **posizione obbligata**.
2. Volumi alti → **investimento in automazione conveniente**: macchine speciali, trasporto automatico, controlli integrati.
3. Macchine specializzate → ognuna fa una sola cosa, ma la fa benissimo e velocissimamente → **TCL ridotto**, saturazione altissima.
4. Sequenza fissa → niente WIP intermedio, niente code → **tempo di attraversamento ≈ somma dei tempi operativi** (vs. giorni di attesa in job shop).
5. Tempo ciclo (TCL) di tutta la linea = TCL della stazione [[Colli di bottiglia|collo di bottiglia]] → la linea va alla velocità del suo anello più debole.

**Cosa accade se…**

- **…si guasta una stazione?** L'intera linea si blocca (niente più routing alternativi come nel job shop). → Necessario investire in alta affidabilità + manutenzione preventiva spinta + eventuali stazioni in **parallelo** sui colli di bottiglia.
- **…cambio prodotto?** I set-up sono **molto pesanti** (macchine specializzate). Si risponde con **campagne produttive lunghe** (un mese del prodotto A, un mese del B), riducendo la frequenza dei cambi.
- **…la domanda crolla?** Disastro. La linea ha costi fissi alti e poca flessibilità: o produci a saturazione o sei in perdita. → Per questo il flow shop richiede una **domanda stabile e prevedibile** ([[CODP - Customer Order Decoupling Point|MTS]]).
- **…aumento i prodotti diversi?** Tendenzialmente non puoi: il flow shop nasce per **un prodotto** (o pochissime varianti molto simili). Se il mix esplode, la soluzione corretta è tornare a [[Group Technology]] o scomporre in più linee dedicate.

---

## §5 Applicazione pratica — quando e come scegliere il flow shop

**Metodologia operativa step-by-step**

**Step 1 — Verifica le pre-condizioni di mercato/prodotto**

- Volumi alti e stabili nel tempo (orizzonte pluriennale).
- Mix prodotti ristretto, alta standardizzazione.
- Modalità di risposta al mercato: tipicamente [[CODP - Customer Order Decoupling Point|MTS]] (raramente ATO).
- Concorrenza basata su **prezzo/costo**, non su personalizzazione.

**Step 2 — Analizza il routing del prodotto**

- Il ciclo tecnologico è **fisso e condiviso** da tutti i prodotti che attraverseranno la linea.
- Identifica le N operazioni elementari → diventeranno N stazioni.

**Step 3 — Calcola il [[Tempo di ciclo TCL|TCL]] richiesto**

- $TCL = T_{disponibile} / Q^*$ (output richiesto nel periodo)
- Verifica che sia raggiungibile dalla stazione più lenta (collo di bottiglia).

**Step 4 — Dimensiona le stazioni ([[Bilanciamento di linea]])**

- Bilancia i tempi operativi: TOPⱼ ≤ TCL per ogni stazione j.
- Se una operazione è troppo lenta → **macchine in parallelo** su quella stazione.
- Se un'operazione richiede troppo tempo singolarmente → **parcellizzazione** (la divido tra due macchine in serie).

**Step 5 — Scegli la geometria**

- Rettilinea: semplice, default per linee lunghe.
- A U: l'operatore al centro controlla più macchine; MP e PF in zone adiacenti.
- Zig-zag: vantaggi della U ma con MP e PF separati.
- Tavola rotante: pezzi piccoli, poche stazioni.

**Step 6 — Progetta il material handling**

- Trasporto continuo (convogliatore in moto continuo) vs trasferimento sincronizzato vs trasferimento non vincolato con buffer.
- La scelta dipende da: variabilità tempi operativi, peso/dimensione pezzi, livello di automazione voluto.

**Step 7 — Pianifica la gestione di guasti e manutenzione**

- TPM, manutenzione preventiva, disponibilità target tipicamente > 95%.
- Eventuali **buffer interoperazionali** come polmoni contro micro-fermate.

**Step 8 — Verifica con [[Analisi CVP]]**

- Confronta costi totali del flow shop vs alternative al volume previsto.
- Il flow shop è giustificato solo oltre il **volume critico Q*** (intersezione delle rette di costo).

> [!check] Checklist rapida prima di decidere "flow shop sì/no"
> 
> - [ ] Domanda annua > 50.000–100.000 pezzi (ordine di grandezza, dipende dal settore)?
> - [ ] Pochi prodotti diversi (1–5) con cicli quasi identici?
> - [ ] Domanda stabile e prevedibile su almeno 3–5 anni?
> - [ ] Modello di mercato MTS/ATO?
> - [ ] Routing tecnologico fisso e condiviso?
> - [ ] Disponibilità a investire in macchine speciali e automazione?
> - [ ] Volume Q > Q* (volume critico CVP)?
> - [ ] Tollerabile la rigidità in caso di calo domanda?
> 
> **Se TUTTE sì → flow shop. Se anche una sola no → considera Group Technology.**

---

## §6 Domanda tipo esame

> **Domanda (orale/scritto):** Discuti il flow shop come soluzione impiantistica. In particolare: definiscilo, posizionalo nella matrice prodotto-processo rispetto a job shop e group technology, illustrane vantaggi e svantaggi, e indica le condizioni di mercato e di prodotto che lo rendono fisiologico. Perché un guasto in un flow shop ha conseguenze più gravi che in un job shop?

**Traccia di risposta strutturata** (i punti vanno toccati in quest'ordine):

1. **Definizione (30 sec):** flow shop = macchine disposte in sequenza secondo il routing del prodotto, collegate da trasporto automatizzato; sistema inscindibile grezzo→finito; macchine specializzate, non general-purpose.
    
2. **Posizionamento nella matrice prodotto-processo:** vertice in basso a destra (alti volumi, bassa varietà, flusso lineare/continuo). Lungo la diagonale fisiologica: job shop (alta varietà, basso volume) → group technology (volumi medi, mix specializzato per famiglie) → flow shop (volumi alti, prodotto unico o quasi) → processo continuo automatizzato.
    
3. **Vantaggi:**
    
    - Massima **efficienza** e saturazione macchine.
    - **Tempi di attraversamento minimi**, prevedibili, controllabili.
    - **Costi di trasporto interno minimi** (macchine adiacenti, posizioni ottimizzate).
    - **WIP ridotto** quasi a zero.
    - Programmazione semplice (il sistema "si auto-programma": basta alimentarlo).
    - Possibilità di [[economia di scala]].
    - Controllo qualità integrato e standardizzato.
4. **Svantaggi:**
    
    - **Rigidità totale**: cambia il prodotto e devi riprogettare la linea.
    - **Investimento iniziale enorme** (macchine speciali, automazione).
    - **Fragilità ai guasti**: una stazione ferma blocca tutto.
    - **Set-up impattanti** tra prodotti diversi → si gestisce con campagne lunghe.
    - **Duplicazione macchine** se la stessa operazione si ripete in più punti del ciclo.
    - **Sensibilità al calo di domanda** (alti costi fissi).
5. **Condizioni fisiologiche:** volumi alti e stabili, prodotti standardizzati, mix ristretto, mercato MTS, competizione su prezzo/costo, ciclo tecnologico fisso e condiviso, orizzonte pluriennale.
    
6. **Sul guasto (la domanda specifica):** in un job shop esistono **routing alternativi** (la stessa lavorazione su macchine diverse dello stesso reparto o di reparti differenti) e **scorte interoperazionali** che disaccoppiano i reparti → un guasto crea un disservizio locale, gestibile. In un flow shop **non esistono alternative**: la sequenza è fissa, le macchine sono specializzate, non c'è scorta tra le stazioni → un guasto ferma l'intera linea. Per questo il flow shop richiede investimenti in alta disponibilità (TPM, manutenzione preventiva, eventuali macchine in parallelo come ridondanza sui colli di bottiglia).
    

---

## §7 Errori comuni

> [!warning] ❌ Errore 1: confondere "flow shop" con "produzione per processo" o "produzione continua" Sono **dimensioni diverse** della classificazione. _Flow shop_ è una soluzione di **layout** (spaziale/organizzativa); _per processo_ è una classificazione **tecnologica** (irreversibilità chimica/fisica); _continua_ è una classificazione di **volumi/cadenza**. Un flow shop tipicamente è anche per parti e a lotti (es. basamenti motore: per parti, discreta a lotti, layout flow shop). Una raffineria è per processo + continua, ma il suo layout impiantistico è ancora altra cosa. **Non sono sinonimi.**

> [!warning] ❌ Errore 2: pensare che il flow shop scali bene anche con varietà alta Sbagliato. Il flow shop **muore** se il mix prodotti cresce: i set-up tra prodotti sono pesanti, le macchine sono specializzate. Il **collocamento patologico** nella matrice prodotto-processo è proprio "flow shop con alta varietà": penalizza tutto (fermo macchina, set-up, scarti, saturazione). Se il mix cresce, **torna alla group technology**.

> [!warning] ❌ Errore 3: trattare il flow shop come "il job shop più efficiente" Non è il job shop "fatto meglio". È una soluzione **completamente diversa** che scambia flessibilità per efficienza. Sceglierlo significa rinunciare consapevolmente a routing alternativi, mix variabile, gestione facile dei nuovi prodotti. È una scommessa strategica sulla **stabilità del prodotto** nel medio-lungo periodo.

---

## §8 Collegamenti

**Prerequisiti (cosa devi sapere PRIMA):**

- [[Job Shop]] — il punto di partenza, l'opposto in flessibilità
- [[Group Technology]] — lo step intermedio da cui il flow shop evolve
- [[Routing / Ciclo tecnologico]] — il flow shop è "scolpito" sul routing
- [[CODP - Customer Order Decoupling Point|CODP]] — modalità di risposta al mercato compatibile
- [[Matrice Prodotto-Processo]] — dove si colloca il flow shop
- [[Classificazione per processi tecnologici|Produzione per parti vs per processo]] — distinzione tecnologica diversa dal layout

**Conseguenze (cosa ne dipende DOPO):**

- [[Layout per prodotto]] — la traduzione fisica/spaziale del flow shop
- [[Bilanciamento di linea]] — come si dimensionano le stazioni
- [[Tempo di ciclo TCL]] — parametro guida del flow shop
- [[Saturazione e Coefficiente di utilizzazione]] — tipicamente alta
- [[Colli di bottiglia]] — concetto chiave per dimensionare
- [[Analisi CVP]] — strumento decisionale flow shop vs alternative
- [[Postponement]] — tecnica per estendere il flow shop a varietà maggiori
- [[OEE]] e [[TEEP]] — metrica di prestazione critica per flow shop (Ap, Ep alti)
- Layout in linea — geometrie — rettilineo, U, zig-zag, tavola rotante

---

## §9 Auto-verifica

1. **(facile)** In una frase: cos'è un flow shop e qual è la sua caratteristica costitutiva che lo distingue dal job shop?
    
2. **(medio)** Perché lungo la diagonale "fisiologica" della matrice prodotto-processo il flow shop si trova nel vertice opposto al job shop? Spiega usando almeno 3 dimensioni (volume, varietà, flusso) e collega ciascuna a una conseguenza operativa.
    
3. **(profondo)** Un'azienda di **elettronica di consumo** produce 8 modelli di smartwatch a volumi medio-bassi (15.000 pezzi/anno per modello), oggi gestiti in group technology. Il management propone di passare a un flow shop unico per ridurre i costi di produzione. Quali rischi corre? Quali alternative impiantistiche più prudenti esistono? In che condizioni la decisione del management diventerebbe corretta?
    

---
