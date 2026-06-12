---
aliases:
  - "Livello di servizio"
  - "Qualità di prodotto e qualità di servizio"
---


> **In 10 secondi:** Qualità = _cosa_ l'azienda offre al cliente (conformità del prodotto alle specifiche). Servizio = _come_ glielo offre (prontezza, puntualità, disponibilità, accuratezza, assistenza). Sono entrambe **prestazioni di efficacia** — misurano la soddisfazione del cliente, non quanto efficienti sono i processi interni.


---

## §1 Domanda fondamentale

> **A che cosa serve guardare alla qualità e al servizio?** A misurare quanto l'azienda riesce a _soddisfare il cliente_ — separando la performance esterna (vista dal cliente) da quella interna (efficienza). Senza queste metriche, un'azienda potrebbe avere costi bassi e impianti saturi e perdere clienti in massa, accorgendosene solo quando crolla il fatturato.

---

## §2 Il problema concreto

**Atelier Crivelli**, casa di pelletteria luxury milanese, 80 dipendenti, due linee in parallelo:

- **Heritage** — borse classiche di catalogo, vendute in 35 boutique multimarca. Le boutique ordinano via portale e si aspettano la merce in pochi giorni → produzione **a magazzino** (MTS).
- **Bespoke** — borse personalizzate (pelle, fodera, monogramma, hardware) commissionate da clienti VIP → produzione **su commessa** (MTO).

Il direttore commerciale entra in riunione: _"Stiamo perdendo clienti, ma il bilancio è solido. Voi della produzione mi date sempre numeri di OEE e potenzialità — non mi spiegano niente di quello che vede il cliente."_

Il dilemma. L'OEE misura **efficienza interna** (TOVA/TC). Il cliente di Crivelli non vede né il TOVA né il tempo di carico. Il cliente vede:

- la borsa Bespoke che doveva arrivare il 30 maggio è arrivata il 14 giugno → **puntualità** ↓
- la boutique che ordina 50 borse Heritage e ne riceve solo 42, perché 8 erano in stock-out per 12 giorni → **disponibilità** ↓ + **persistenza stock-out** ↑
- la cliente VIP che apre la scatola e trova un monogramma sbagliato → **accuratezza** ↓
- il cliente che dopo un anno vuole far sostituire la fibbia e non riesce a farsi richiamare → **assistenza post-vendita** ↓

Sono **quattro fenomeni distinti**, ognuno con la sua metrica. Il vero problema di Crivelli è metterli tutti sotto l'etichetta generica "qualità": senza separare i piani, non si capisce dove intervenire.

---

## §3 La definizione

**Qualità e servizio** sono le due dimensioni dell'**efficacia** di un sistema di produzione, ovvero della sua capacità di soddisfare il cliente (esterno o interno).

**Scomposizione:**

- **Qualità di prodotto** ≔ conformità del prodotto alle specifiche del cliente. Risponde a: _cosa_ offre l'azienda?
- **Qualità di servizio** ≔ modalità con cui il prodotto viene reso disponibile e supportato lungo l'intero ciclo di vita. Risponde a: _come_ lo offre?

A loro volta, le metriche di servizio si articolano così:

```
Servizio
├── per commessa (ordine → produzione)
│   ├── prontezza (tempestività)   — durata: ordine → consegna
│   └── puntualità                  — scostamento date pianificate vs effettive
├── a magazzino (ordine → prelievo)
│   ├── disponibilità               — % beni ordinati immediatamente disponibili
│   └── persistenza stock-out       — durata della condizione di indisponibilità
├── trasversale (logistica in uscita)
│   ├── accuratezza                 — % spedizioni senza errori di articolo
│   └── completezza                 — % ordini soddisfatti per intero
└── ciclo di vita
    ├── pre-vendita                 — consulenza, configurazione, preventivazione
    └── post-vendita                — assistenza, garanzia, ricambi, manutenzione
```

> [!note] Forma generale delle metriche di efficacia $$\text{KPI}_\text{efficacia} = \frac{\text{eventi di successo}}{\text{eventi totali}}$$
> 
> dove "evento" può essere un ordine, una riga d'ordine, un prodotto consegnato, una richiesta di modifica; e "successo" è il rispetto della specifica concordata (tempo, quantità, conformità, completezza, …).

---

## §4 Come funziona

**Il cuore in una frase:** qualità misura la _conformità statica_ del prodotto, servizio misura il _flusso dinamico_ del rapporto cliente-azienda lungo l'intero processo logistico-produttivo.

**Connessione tra le parti:**

- Le aziende **per commessa** spostano l'attenzione del cliente sul **tempo** (quanto aspetto? la data viene rispettata?) → prontezza e puntualità sono vitali.
- Le aziende **a magazzino** spostano l'attenzione sull'**immediatezza** (è disponibile ora? quando torna disponibile?) → disponibilità e persistenza stock-out sono vitali.
- **Accuratezza e completezza** sono **trasversali**: anche il miglior produttore al mondo crolla se sbaglia l'imballaggio o consegna ordini parziali.
- Le metriche pre/post-vendita coronano il sistema: legate al concetto di [[Servitization]], misurano quanto l'azienda "sostiene" il cliente _dopo_ la vendita.

**Casi limite e varianti:**

- **Azienda mista** (come Crivelli) → deve gestire **entrambi i set di metriche** in parallelo, non si può scegliere un solo gruppo.
- **Prontezza interna ≠ prontezza percepita dal cliente.** La prima va da _inizio produzione_ a _consegna a magazzino PF_; la seconda va da _accettazione dell'ordine_ a _consegna effettiva_. Includere o no le fasi di pianificazione e reperimento risorse cambia drammaticamente il numero. Il cliente paga la seconda.
- **Servizio è la leva più "economica".** Si modifica con sole **leve gestionali** (programmazione, scorte, organizzazione spedizioni), senza riconfigurare l'impianto. Per questo è spesso la prima area su cui agire quando il cliente lamenta inefficacia.
- **Cliente interno.** Le stesse metriche si applicano _intra-azienda_: un reparto a valle è cliente del reparto a monte. La completezza di un kit di componenti che arriva alla linea di assemblaggio è una misura di servizio interno.

---

## §5 Applicazione pratica (metodologia)

Quando devi **definire o valutare** il sistema di metriche di qualità e servizio per un'azienda specifica, segui questa procedura:

**Step 1 — Classifica la modalità di risposta al mercato.** Stabilisci se l'azienda opera prevalentemente per commessa, a magazzino, o entrambi (vedi [[CODP - Customer Order Decoupling Point|CODP]]). Questo decide _quali_ metriche di servizio sono prioritarie.

**Step 2 — Identifica i clienti rilevanti.** Sono solo esterni o anche interni? Il sistema di misura deve mappare entrambi i livelli se il processo produttivo è composto da più aree in cascata.

**Step 3 — Definisci "evento" e "successo" per ciascuna metrica.** Ogni KPI di efficacia ha forma `[successi/totali]`. Devi specificare in modo non ambiguo:

- _cos'è_ un evento (un ordine? una riga d'ordine? un prodotto?);
- _cos'è_ un successo (consegna entro la data del cliente? entro la data pianificata? con prodotto conforme?). Senza questa definizione operativa, due reparti misureranno cose diverse con lo stesso nome.

**Step 4 — Modellizza i tempi (per metriche temporali).** Per prontezza e puntualità servono **date di riferimento esplicite**:

- _accettazione ordine → inizio produzione → fine produzione → consegna a magazzino PF → spedizione → ricezione cliente_;
- _data richiesta dal cliente vs. data pianificata internamente vs. data effettiva_. Le metriche sono differenze tra coppie di queste date.

**Step 5 — Misura accuratezza e completezza sulla logistica in uscita.**

- Accuratezza ≔ numero di spedizioni _errate_ (articolo sbagliato) / spedizioni totali.
- Completezza ≔ numero di ordini consegnati _integralmente_ / ordini totali. Sono le metriche apparentemente "scontate" ma quasi sempre tra le più impattanti sulla soddisfazione percepita.

**Step 6 — Aggiungi il livello pre/post-vendita.** Definisci almeno: tempo medio di prima risposta a una richiesta di assistenza, % di ricambi disponibili entro X giorni, NPS o equivalenti.

**Checklist per non sbagliare:**

- [ ] Ho separato qualità (cosa) da servizio (come)?
- [ ] Ho riconosciuto se l'azienda è MTS, MTO o mista?
- [ ] Per ogni KPI ho una definizione operativa di "evento" e "successo"?
- [ ] Ho distinto prontezza interna (produzione) da prontezza percepita (totale)?
- [ ] Ho incluso accuratezza e completezza anche se sembrano banali?
- [ ] Sto coprendo l'intero ciclo di vita, incluso pre/post-vendita?
- [ ] Per il cliente interno applico lo stesso schema?

---

## §6 Domanda tipo esame

> **Domanda (orale/scritto).** _Definisca le prestazioni di "livello di servizio" in un sistema di produzione manifatturiero. Distingua i contesti applicativi rilevanti, indichi le principali misure utilizzate e discuta perché tali prestazioni siano considerate particolarmente "modificabili" dal management._

**Traccia di risposta strutturata** (nell'ordine in cui toccare i punti):

**1) Inquadramento iniziale.** Aprire chiarendo che qualità e servizio sono entrambe misure di **efficacia** (quindi orientate al cliente), distinte dall'efficienza che è invece interna. Richiamare il secondo livello di lettura delle prestazioni: produttività + qualità + servizio + flessibilità.

**2) Distinzione qualità vs servizio.** In una frase netta: qualità = conformità del prodotto alle specifiche (il "cosa"); servizio = modalità con cui il prodotto viene erogato lungo l'intero processo logistico (il "come").

**3) Tassonomia delle misure di servizio** (è qui che si guadagna il voto):

- **per commessa** → prontezza (intervallo tempo ordine → consegna) e puntualità (scostamento data pianificata ↔ effettiva); spiegare la differenza tra prontezza interna e prontezza percepita dal cliente;
- **a magazzino** → disponibilità (% beni ordinati subito disponibili) e persistenza dello stock-out (durata media indisponibilità);
- **trasversali** ai due contesti → accuratezza (errori di articolo nelle spedizioni) e completezza (ordini soddisfatti integralmente);
- **a coronamento** → assistenza pre e post-vendita.

**4) Forma analitica generale.** Citare la struttura `[eventi di successo / eventi totali]` come pattern comune per le metriche di efficacia, sottolineando l'importanza di una definizione operativa caso per caso di "evento" e "successo".

**5) Composizione tra processi.** Sottolineare che il livello di servizio è frutto della combinazione di **processo produttivo** (realizza il prodotto) + **processo logistico** (lo distribuisce): gli stessi indicatori, con adattamenti, si applicano a entrambi.

**6) Chiusura forte — perché sono "modificabili".** Le prestazioni di servizio sono tra le **più facilmente migliorabili agendo su sole leve gestionali** (programmazione, dimensionamento scorte, organizzazione spedizioni), con interventi limitati sulla configurazione fisica del sistema. Questo le rende il primo terreno di intervento quando si vuole alzare la soddisfazione del cliente in tempi rapidi, senza ammortizzare nuovi investimenti.

**7) (Bonus se c'è tempo)** Cliente interno: lo schema vale anche tra reparti contigui in cascata, dove un'area è cliente di quella a monte.

---

## §7 Errori comuni

> [!warning] ❌ Confondere qualità di prodotto e qualità di servizio Sono due dimensioni distinte. Il _tasso qualità_ $Q$ dell'OEE misura la conformità del prodotto (% conformi sul totale realizzato): è **qualità di prodotto**. La puntualità delle consegne, invece, è **qualità di servizio**: un prodotto può essere perfettamente conforme e arrivare in ritardo, e viceversa. _Come evitarlo:_ tieni mentalmente separati "cosa offro" (qualità) da "come lo offro" (servizio).

> [!warning] ❌ Applicare le metriche del contesto sbagliato Misurare la disponibilità in un'azienda ETO (cantieristica navale, aerospaziale, impianti complessi) non ha senso: il prodotto non esiste a magazzino, viene creato a partire dall'ordine. Specularmente, misurare la prontezza in un produttore di smartphone MTS è poco rilevante: la consegna è quasi istantanea dal magazzino centrale. _Come evitarlo:_ parti sempre dalla classificazione [[CODP - Customer Order Decoupling Point|CODP]] dell'azienda; le metriche di servizio sono _condizionate_ alla modalità di risposta al mercato.

> [!warning] ❌ Non distinguere prontezza interna da prontezza percepita All'esame è classico l'errore di calcolare la prontezza solo dall'inizio produzione, dimenticando le fasi di pianificazione e reperimento risorse. Il cliente vede invece un tempo _totale_, dall'accettazione dell'ordine alla consegna effettiva — e quel tempo è ciò che paga. _Come evitarlo:_ quando misuri un tempo, dichiara sempre **da quale evento** parte e **a quale evento** termina.

---

## §8 Collegamenti

**Prerequisiti (cosa devi sapere PRIMA):**

- [[Efficacia ed efficienza]] — la dicotomia generale di cui qualità e servizio sono il lato efficacia
- [[CODP - Customer Order Decoupling Point|CODP]] — il punto di disaccoppiamento, decide quali metriche di servizio sono pertinenti
	 — modalità di risposta al mercato che condizionano le metriche
- Cliente interno vs cliente esterno — per applicare lo schema anche intra-azienda

**Dipendenze (cosa ne consegue):**

- [[Flessibilità]] — la quarta dimensione prestazionale, ibrida tra efficacia ed efficienza
- [[Tempo di attraversamento]] — base tecnica per misurare la prontezza interna
- [[OEE]] e [[Tasso di qualità (Q)]] — il pezzo "qualità di prodotto" entra dentro l'OEE come fattore $Q$
- [[Servitization]] — porta l'attenzione sul lato pre/post-vendita, fino a invertire il rapporto prodotto/servizio
- Dimensionamento scorte — leva gestionale tipica per aumentare disponibilità e ridurre stock-out

---

## §9 Auto-verifica

Tre domande, dalla più semplice alla più profonda. Rispondi _senza_ riguardare la nota.

1. **Base.** In una frase, qual è la differenza tra qualità (di prodotto) e servizio (qualità di servizio)?
    
2. **Intermedia.** Un'azienda che produce su commessa quali due metriche di servizio deve misurare prioritariamente, e cosa misurano esattamente l'una e l'altra? Per un'azienda a magazzino, quali altre due si aggiungono o sostituiscono? E quali due metriche valgono in entrambi i contesti?
    
3. **Profonda.** Perché si afferma che il livello di servizio è la prestazione "più modificabile" tra quelle esterne? Cosa implica questa proprietà sulla strategia di un'azienda che voglia migliorare la soddisfazione del cliente nel breve periodo? Fai un esempio concreto di leva _gestionale_ (non strutturale) che agisce su una metrica di servizio.