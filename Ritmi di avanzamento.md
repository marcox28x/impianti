
> **In 10 secondi:** 4 modi di sincronizzare il passaggio dei pezzi tra stazioni — da asincrono (operatore o automatismo libero) a continuo (vincolato dal nastro). Trade-off ricorrente: rigidità/efficienza ↔ elasticità/WIP.

---

## §1 Domanda fondamentale

Una volta deciso di organizzare la produzione in stazioni di lavoro disposte in successione, **con quale meccanismo temporale i pezzi avanzano da una stazione alla successiva?**

---

## §2 Il problema concreto

Multinazionale dell'elettronica di consumo (es. Philips) progetta una linea per assemblare rasoi elettrici. Target: **1.500 pz / turno (8 h)** → ritmo richiesto ≈ 19 s/pz.

Il ciclo è articolato in 5 stazioni:

|Stazione|Attività|Tempo elemento (s)|
|---|---|---|
|S1|Montaggio motore|50|
|S2|Inserimento testina rasante|80|
|S3|Chiusura corpo macchina|65|
|S4|Test funzionale|90|
|S5|Packaging|45|

**Dilemma:** S4 ha tempo **doppio** di S5. Tre opzioni sul tavolo:

- impongo cadenza unica al ritmo della stazione più lenta (S4 = 90 s) → S5 lavora a metà saturazione, ma flusso ordinato;
- lascio ogni stazione al proprio ritmo → si accumulano semilavorati ovunque (WIP), ma nessuna stazione è artificialmente rallentata;
- delego all'operatore la scelta del momento di passaggio → meno alienante, ma serve organizzare i polmoni.

→ Le tre scelte corrispondono esattamente a **tre dei quattro ritmi di avanzamento**. La quarta è l'evoluzione "estrema" del ritmo imposto (trasferimento continuo), tipica dell'automotive.

---

## §3 La definizione

> **Ritmo di avanzamento** ≔ meccanismo temporale che regola lo spostamento del pezzo (o assieme) da una stazione di lavoro alla successiva lungo la linea.

Premesse necessarie:

- **stazione** = postazione di lavoro che esegue una o più _fasi_ del ciclo produttivo;
- la **potenzialità della linea** dipende **solo** dalla stazione (o gruppo di stazioni) più lenta **+** dalla modalità di avanzamento scelta.

**Quattro classi mutuamente esclusive:**

|#|Modalità|Chi impone il ritmo?|Buffer / polmoni|Esempio tipico|
|---|---|---|---|---|
|1|**Ritmo non imposto**|Sistema asincrono automatico, ogni stazione indipendente|Polmoni intermedi (presenti)|Assemblaggio elettronica varia|
|2|**Ritmo imposto**|Sistema di trasporto, cadenza unica per tutte|Polmoni di disaccoppiamento (opzionali)|Linee assemblaggio elettrodomestici|
|3|**Trasferimento continuo**|Convogliatore in moto continuo, geometria fissa|Generalmente assenti|Automotive (catene aeree/pavimento)|
|4|**Trasferimento non vincolato**|L'**operatore**|Buffer interoperazionali **obbligatori**|Assemblaggio manuale di precisione, job enrichment|

---

## §4 Come funziona

> **Idea centrale:** quanto più il ritmo è "imposto", tanto più la linea è efficiente ma rigida; quanto più è "libero", tanto più è elastica ma richiede WIP e gestione asincronie.

**Diagramma logico (asse rigidità ↔ flessibilità):**

```
        ↑ rigidità / efficienza / vincolo geometrico
        │
   [3] CONTINUO         convogliatore ininterrotto, distanza DT costante
        │               t_stazione = DT / v   (fisso, geometrico)
        │               guasto stazione → blocco totale linea
        │
   [2] IMPOSTO          cadenza T_CL unica imposta dal trasporto
        │               eventuali polmoni di disaccoppiamento per elasticità locale
        │
   [4] NON VINCOLATO    decisore = operatore
        │               buffer obbligatori (svincola monte/valle)
        │               motivazione: ergonomia, anti-alienazione, ↓incompleti
        │
   [1] NON IMPOSTO      stazioni indipendenti, prelievo-avvio asincrono automatico
        │               polmoni intermedi necessari
        │
        ↓ flessibilità / WIP / elasticità
```

**Cosa accade se… (casi limite e varianti):**

- **Continuo senza buffer + guasto S3** → blocco a cascata di tutta la linea (rischio strutturale del flow-shop più estremo).
- **Non imposto con polmoni infiniti** → la "linea" degenera in N postazioni indipendenti, perde senso di linea.
- **Imposto + polmoni di disaccoppiamento ben dimensionati** → ibrido: ritmo unico ma sezioni temporaneamente autonome in caso di micro-fermate (collegamento diretto a [[Magazzini interoperazionali]]).
- **Non vincolato vs Non imposto:** stessa struttura logica (buffer + asincronia), differiscono per _chi_ decide → automatismo tecnico vs operatore umano. La scelta del non vincolato è motivata da fattori **gestionali e organizzativi**, non tecnici.

---

## §5 Applicazione pratica — metodologia di scelta

### Procedura step-by-step

**Step 1 — Caratterizza il prodotto.**

- volume alto e standardizzato → orientamento verso imposto / continuo;
- volume medio-basso o mix → non imposto;
- ingombro/peso elevato → continuo (es. auto su catena aerea);
- cicli omogenei tra prodotti → imposto fattibile; eterogenei → non imposto.

**Step 2 — Valuta i tempi delle stazioni.**

- tempi **bilanciati** (varianza bassa) → imposto / continuo viabili senza penalizzazioni;
- tempi **sbilanciati** → con ritmo imposto si paga in saturazione; alternative: parallelizzare il collo di bottiglia oppure passare a non imposto + polmoni.

**Step 3 — Considera la manodopera.**

- lavoro percepito come alienante o esigenze di job enrichment → **non vincolato** (svincola operatore dalla cadenza);
- manodopera generica + alta automazione → imposto / continuo;
- compatibilità con [[Specializzazione manodopera]]: ricomposta/isola ↔ non vincolato; parcellizzata ↔ imposto/continuo.

**Step 4 — Stima frequenza guasti e variabilità.**

- alta → buffer indispensabili → non imposto, oppure imposto con disaccoppiamento;
- bassa + alta automazione affidabile → continuo accettabile.

**Step 5 — Verifica contro l'obiettivo gestionale.**

- massima efficienza & alti volumi → **continuo**;
- flessibilità mix & medi volumi → **non imposto**;
- qualità del lavoro & motivazione → **non vincolato**;
- compromesso linea automatizzata con elasticità locale → **imposto + buffer**.

### Checklist anti-errore

- [ ] Ho identificato la stazione collo di bottiglia? (determina la potenzialità reale)
- [ ] Nelle modalità che lo richiedono (1 e 4) ho **esplicitamente** previsto polmoni / buffer?
- [ ] Per il continuo: ho verificato che `t_stazione = DT/v` sia ≥ del massimo contenuto di lavoro per stazione?
- [ ] La modalità scelta è coerente con la specializzazione della manodopera prevista?
- [ ] Ho valutato l'impatto di un guasto locale sull'intera linea (continuo è il più vulnerabile)?
- [ ] Se ho scelto "non vincolato", ho una giustificazione **organizzativa** (non solo tecnica)?

---

## §6 Domanda tipo esame

> _«Si descrivano le quattro modalità di avanzamento dei pezzi in una linea di produzione, evidenziando per ciascuna il meccanismo di sincronizzazione, i requisiti in termini di buffer e un settore industriale tipico. Si discuta il trade-off tra rigidità ed elasticità e si motivi la presenza del trasferimento non vincolato.»_

### Traccia di risposta strutturata (5–7 minuti)

1. **Premessa (≈30 s).** Definire stazione e fase. Ricordare che la potenzialità della linea dipende dalla stazione più lenta + dalla modalità di avanzamento.
2. **Ritmo non imposto.** Stazioni indipendenti, sistema asincrono di prelievo-avvio, polmoni intermedi presenti. Vantaggio: flessibilità. Svantaggio: WIP elevato. Tipico: assemblaggio elettronica con varianti.
3. **Ritmo imposto.** Cadenza unica fissata dal trasporto, uguale per tutte le stazioni; possibili polmoni di disaccoppiamento per micro-arresti locali. Vantaggio: efficienza, semplicità di programmazione. Svantaggio: rigidità, perdita di saturazione se tempi sbilanciati. Tipico: assemblaggio elettrodomestici.
4. **Trasferimento continuo.** _Caso particolare_ del ritmo imposto: convogliatore in moto continuo (aereo o a pavimento), prodotti a distanza costante, `t_staz = DT/v`. Vantaggio: massima efficienza per prodotti voluminosi e alti volumi. Svantaggio: guasto locale = blocco totale, rigidità estrema. Tipico: automotive.
5. **Trasferimento non vincolato.** L'operatore decide quando inviare il pezzo a valle → buffer interoperazionali **obbligatori**. Logicamente simile ai precedenti, ma motivato da ragioni **gestionali**: svincolare l'operatore da una cadenza fissa, ridurre incompleti, rendere il lavoro meno alienante (collegamento al concetto di [[Specializzazione manodopera]] ricomposta o a isola).
6. **Trade-off conclusivo.** Asse efficienza ↔ flessibilità. Continuo = max efficienza, min flessibilità, max impatto guasti. Non imposto = inverso. Non vincolato = compromesso che privilegia il fattore umano. La scelta dipende da volumi, varietà, affidabilità impianto e politica del lavoro adottata.

---

## §7 Errori comuni

> [!warning] ❌ Confondere "ritmo imposto" con "trasferimento continuo" Il continuo è un _caso particolare_ dell'imposto. In entrambi la cadenza è fissa, ma nel continuo è il convogliatore in moto a imporla **geometricamente** (`t = DT/v`), mentre l'imposto generico può essere a step / intermittenza. **Come evitarlo:** ricorda la gerarchia: ogni continuo è imposto, ma non viceversa.

> [!warning] ❌ Dimenticare che "non imposto" e "non vincolato" richiedono polmoni Senza buffer, le asincronie tra stazioni bloccano immediatamente la linea (condizioni di _starving_ o _blocking_). **Come evitarlo:** se in un esercizio o all'orale scegli una di queste due modalità, dichiara **sempre** la presenza di magazzini interoperazionali (collegamento naturale al cap. 5.3.2).

> [!warning] ❌ Equiparare "non vincolato" a "non imposto" Strutturalmente simili (entrambi asincroni, entrambi con buffer), ma differiscono per il **decisore**: nel non imposto è un sistema automatico; nel non vincolato è l'operatore. Le motivazioni sono **tecniche** vs **umane/organizzative**. **Come evitarlo:** all'esame cita sempre _chi_ decide il passaggio e perché.

---

## §8 Collegamenti

### Prerequisiti (sapere PRIMA)

- [[Stazioni e fasi]] — concetto base di aggregazione delle attività in postazioni
- [[Job-shop vs Flow-shop]] — contesto: i ritmi imposto/continuo sono tipici del flow-shop
- [[Group Technology e celle]] — evoluzione storica verso linee dedicate

### Conseguenze (sapere DOPO / argomenti a valle)

- [[Bilanciamento di linea monoprodotto]] — il bilanciamento ha senso pieno solo con ritmo imposto
- [[Tempo di ciclo TCL]] — formalizza la cadenza: `TCL = TP / Q*` oppure `TCL = DT/v` per il continuo
- [[Magazzini interoperazionali]] — dimensionamento dei polmoni (cap. 5.3.2 e 5.3.3)
- [[Specializzazione manodopera]] — parcellizzata / ricomposta / a isola; legame diretto: non vincolato ↔ ricomposta o isola
- [[Layout per prodotto]] — il layout in linea ospita queste modalità di avanzamento

---

## §9 Auto-verifica

1. **(base)** Quali sono le 4 modalità di avanzamento e quale è caso particolare di un'altra?
2. **(media)** In quali due modalità i polmoni sono _obbligatori_ o _fortemente raccomandati_? Cosa succede se mancano?
3. **(profonda)** Una linea di assemblaggio per smartwatch ha 6 stazioni con tempi sbilanciati (da 20 s a 70 s) e gli operatori chiedono job enrichment. La direzione spinge per "massima efficienza, ritmo continuo". Quale ritmo proporresti come compromesso? Giustifica la scelta toccando: motivazione operatori, gestione delle asincronie, ruolo del collo di bottiglia, dimensionamento dei buffer.