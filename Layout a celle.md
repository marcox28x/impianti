
> **In 10 secondi:** configurazione ibrida tra job shop e flow shop in cui le macchine sono raggruppate in **celle** dedicate a **famiglie di prodotti con cicli simili** — ogni cella è organizzata in linea al suo interno, ma il sistema globale resta a famiglie. Si guadagna efficienza senza rinunciare del tutto alla flessibilità.

---

## §1 Domanda fondamentale

**Come ottengo l'efficienza del layout in linea quando i miei volumi non sono abbastanza alti — né i miei prodotti abbastanza standardizzati — per giustificare una linea dedicata, ma il job shop mi sta costando troppo in WIP e tempi di attraversamento?**

In altre parole: come metto ordine in un caos di varianti che però, se guardo bene, non sono _davvero_ tutte diverse?

---

## §2 Il problema concreto

Immagina **L'Atelier**, un'azienda di **cosmetica** di media dimensione, con 80 SKU attivi: rossetti, mascara, fondotinta, ombretti, eyeliner, blush in polvere, illuminanti. Volume totale annuo: 6 milioni di pezzi. Volume medio per SKU: ~75.000 pz/anno — alto in aggregato, basso per singolo prodotto.

Layout attuale (job shop):

- Reparto **miscelazione/formulazione**
- Reparto **riempimento contenitori**
- Reparto **packaging primario**
- Reparto **packaging secondario e astucciatura**

Ogni prodotto attraversa i reparti in ordine diverso, con tempi diversi. Risultato misurato:

- Setup medio tra cambio prodotto: **45 minuti** (un rossetto richiede lavaggio caldaie completamente diverso da un mascara)
- WIP medio: **18 giorni di produzione** in coda nei reparti
- Tempo di attraversamento: tra **5 e 22 giorni** (imprevedibile)
- Saturazione macchine: 58%

**Il dilemma:** non possono passare a flow shop (un rossetto e un mascara non hanno lo stesso ciclo: stick _vs_ tubetto con applicatore, formulazione cerosa _vs_ emulsione, packaging tubolare _vs_ astuccio rigido). Ma il job shop sta strangolando il time-to-market e i margini.

**Domanda aperta:** esiste una via di mezzo?

→ Sì: se nel caos delle 80 SKU si possono identificare **gruppi omogenei per ciclo**, il layout a celle è esattamente la risposta.

---

## §3 La definizione

> **Layout a celle (cell production):** configurazione di layout in cui le unità produttive sono aggregate in celle, ciascuna dedicata in modo esclusivo a una **famiglia di componenti/prodotti** che condividono cicli di lavorazione simili o uguali. All'interno della cella le macchine sono disposte in **sequenza lineare** secondo il ciclo della famiglia; il sistema globale è **ibrido** (alcune celle in linea + reparti per le lavorazioni residue).

Le tre parti da tenere a mente:

```
Layout a celle
├── Famiglia di componenti
│   ≔ gruppo di item con affinità di geometria, ciclo, processo
│   → setup interni minimi (gli item si somigliano)
│
├── Cella
│   ≔ insieme di macchine fisicamente raggruppate
│   ≔ dedicate ESCLUSIVAMENTE a una famiglia
│   → disposizione interna in linea
│
└── Sistema globale
    ≔ può essere ibrido: celle + reparti tradizionali
    → realizza il PF anche attraverso attraversamenti multipli di una/più celle
```

È l'applicazione del principio di **[[Group Technology]]** al problema del layout fisico.

---

## §4 Come funziona

**Il cuore:** prendi la varietà di un job shop e cerchi _isole di ripetitività_ — gruppi di prodotti che, pur essendo formalmente diversi, condividono lo stesso schema di lavorazione. Dove trovi un'isola, ci pianti una cella in linea.

Come le parti si connettono:

1. Si identifica nel mix produttivo un sottoinsieme di item che hanno **cicli simili** (anche solo per una porzione del ciclo totale).
2. Si **dedica** un set di macchine a quella famiglia (esclusivo: la cella non lavora altro).
3. Dentro la cella, le macchine sono disposte **in linea** secondo la sequenza tipica del ciclo della famiglia.
4. Il flusso _dentro_ la cella è semplice e unidirezionale; il flusso _tra_ celle può ancora essere complesso.
5. Item che non rientrano in nessuna famiglia → restano gestiti come job shop in reparti residui.

**Cosa accade se...**

- **...la famiglia coincide con un singolo cliente?** Si ottiene una specializzazione commerciale estrema: la cella diventa di fatto un mini-stabilimento dedicato a quel cliente.
- **...il volume di una famiglia continua a crescere?** La cella diventa conveniente da automatizzare e **evolve naturalmente in flow shop**: stessa logica di sequenza, ma con material handling automatizzato e macchine speciali. Questa è la traiettoria tipica: `job_shop → group_technology → flow_shop`.
- **...arriva un prodotto nuovo che non sta in nessuna cella?** Problema serio. La rigidità del sistema rende difficile inserirlo senza creare "operazioni fuori cella" (deroghe al flusso lineare), che sono fastidiose da gestire.
- **...una macchina della cella si guasta?** Tutta la cella si ferma. Non si può dirottare la lavorazione su una cella adiacente, perché violerebbe il principio di assegnazione esclusiva (altrimenti il sistema _degenera in job shop_). Per questo le celle richiedono macchine ad **alta disponibilità** e capacità **sovradimensionata**.

---

## §5 Applicazione pratica (metodologia)

Come si progetta un layout a celle, passo per passo:

**Step 1 — Censimento mix produttivo** Elenca tutti gli item in produzione, per ognuno raccogli: ciclo di lavorazione (sequenza fasi + macchine), geometria/morfologia, volume annuo.

**Step 2 — Costruzione [[Diagramma multiprodotto]]** Costruisci la matrice `item × macchine` segnando le sequenze di attraversamento. È lo strumento canonico per _vedere_ le similarità di ciclo.

**Step 3 — Identificazione famiglie (clustering)** Raggruppa item con cicli simili. Criteri di affinità (in ordine di importanza):

- Sequenza delle macchine attraversate
- Geometria/morfologia (incide su attrezzature/setup)
- Tempi di lavorazione comparabili Tipicamente si ottengono 3–6 famiglie + un residuo "orfano".

**Step 4 — Dimensionamento di ciascuna cella** Per ogni famiglia: calcola il fabbisogno orario (volume aggregato della famiglia / tempo apertura), poi dimensiona il numero di macchine per stazione (vedi [[Saturazione e numero macchine]]). **Sovradimensiona** rispetto al fabbisogno medio: la cella non può sforare verso altre celle.

**Step 5 — Disposizione fisica intra-cella** Macchine in linea secondo la sequenza tipica del ciclo della famiglia. Geometrie possibili: rettilineo, U, zig-zag (vedi [[Geometrie del layout in linea]]).

**Step 6 — Gestione del residuo** Gli item "orfani" (che non stanno in nessuna famiglia) restano in un'area job shop residuale. Lavorazioni speciali centralizzate (es. verniciatura, trattamenti termici, sterilizzazione) restano fuori cella per ragioni di investimento.

**Step 7 — Coordinamento globale** Definisci come i materiali si muovono tra celle e tra celle e reparti residui. Questo è il punto critico: tanto più ibrido il sistema, tanto più sofisticato deve essere il coordinamento.

### Checklist per non sbagliare

- [ ] Le famiglie identificate sono **realmente** omogenee per ciclo (non solo per prodotto finito)?
- [ ] Ho **sovradimensionato la capacità** di ogni cella per assorbire variazioni di mix?
- [ ] Le macchine di cella sono ad **alta disponibilità** (guasto = blocco cella)?
- [ ] Ho previsto la gestione delle **"operazioni fuori cella"** (centralizzate per investimento)?
- [ ] Il numero di **prodotti orfani** è sostenibile in un'area residua?
- [ ] Ho considerato la **traiettoria evolutiva**: cella → flow shop se i volumi crescono?
- [ ] Lo **sbilanciamento dei carichi tra celle** al variare del mix è gestibile?

---

## §6 Domanda tipo esame (orale/scritto)

> _"Il candidato descriva la configurazione a celle, spiegandone i principi e le motivazioni che ne giustificano l'adozione. Confronti i vantaggi e gli svantaggi rispetto a job shop e flow shop, e indichi in quali condizioni di mercato/produzione la soluzione risulta preferibile."_

### Traccia di risposta strutturata

**Apertura — inquadramento (30 secondi):** "Il layout a celle è una configurazione ibrida tra job shop e flow shop, basata sui principi della group technology. Nasce per dare risposta a contesti di varietà media e volumi medi, dove né il job shop né la linea dedicata sono ottimali."

**Definizione tecnica:** Si raggruppano macchine in celle, ciascuna dedicata esclusivamente a una famiglia di componenti con cicli simili. Intra-cella la disposizione è lineare; il sistema globale può essere ibrido (celle + reparti residui).

**Quando conviene — condizioni di applicabilità:**

- Mix produttivo in cui sono identificabili famiglie omogenee per ciclo
- Volumi unitari per famiglia sufficienti a saturare una cella ma non a giustificare una linea automatizzata dedicata
- Azienda con domanda specializzata su pochi clienti/prodotti (evoluzione naturale dal job shop)

**Vantaggi rispetto al job shop:**

- WIP ridotto (annulla colli di bottiglia imprevisti da congestione)
- Tempi di attraversamento ridotti e soprattutto più **stabili** (date di consegna affidabili)
- Saturazione macchine maggiore
- Capacità della cella facilmente identificabile (collo di bottiglia stabile)
- Programmazione semplificata (problema combinatorio più piccolo)
- Setup interni alla cella ridotti (item simili)

**Svantaggi rispetto al job shop (= prezzo della rigidità):**

- Flessibilità ridotta: gli item sono rigidamente assegnati a celle
- Capacità non trasferibile tra celle (no dirottamento in caso di guasto/sovraccarico)
- Necessità di **sovradimensionamento** della capacità
- Necessità di **alta disponibilità** delle macchine (guasto = blocco cella)
- Problemi di sbilanciamento dei carichi tra celle al variare del mix

**Svantaggi rispetto al flow shop:**

- Minore efficienza unitaria (no automazione spinta del material handling)
- Minore standardizzazione

**Criticità trasversali:**

- Gestione di operazioni "fuori cella" (centralizzazioni per investimento: verniciatura, trattamenti termici)
- Inserimento di prodotti nuovi che non rientrano nelle famiglie esistenti
- Coordinamento globale del sistema ibrido

**Chiusura:** "In sintesi, la group technology è l'**evoluzione naturale del job shop** quando la domanda si specializza e i volumi unitari crescono. Se questa traiettoria continua, la cella stessa può evolvere in flow shop dedicato."

---

## §7 Errori comuni

> [!warning] ❌ Errore 1 — Confondere "cella" con "linea (flow shop)" **Cosa sbaglio:** dire che la cella _è_ una linea, o usare "layout a celle" come sinonimo di "layout in linea". **Perché è sbagliato:** la cella è organizzata in linea _al suo interno_, ma il sistema globale resta a famiglie. Il flow shop è un'unica linea dedicata a un prodotto (o famiglia ristrettissima), con material handling automatizzato. **Come evitarlo:** ricorda la traiettoria evolutiva: `job_shop → group_technology → flow_shop`. La cella è lo step intermedio, non il finale.

> [!warning] ❌ Errore 2 — Pensare che la cella sia _più_ flessibile del job shop **Cosa sbaglio:** affermare che, essendo "ibrida", la cella è più flessibile sia del job shop sia del flow shop. **Perché è sbagliato:** la cella è **meno flessibile** del job shop, non più. Gli item sono rigidamente vincolati alla cella, non si possono dirottare. La cella combina la _programmabilità_ del flow shop con la _capacità di gestire varietà_ del job shop, ma paga la sua via di mezzo in flessibilità. **Come evitarlo:** memorizza la gerarchia: `job_shop > group_tech > flow_shop` per flessibilità; `flow_shop > group_tech > job_shop` per efficienza.

> [!warning] ❌ Errore 3 — Dimenticare le "operazioni fuori cella" **Cosa sbaglio:** descrivere il layout a celle come un sistema puro, in cui _tutto_ avviene in cella. **Perché è sbagliato:** quasi sempre esistono lavorazioni che, per ragioni di costo dell'investimento (es. impianti di verniciatura, trattamenti termici, sterilizzazione farmaceutica), restano centralizzate e fuori cella. Il prodotto deve quindi uscire dalla cella, attraversare l'area centralizzata, e rientrare — turbando la linearità del flusso. **Come evitarlo:** nelle risposte d'esame, cita sempre il problema delle operazioni fuori cella e della necessità di coordinamento globale del sistema ibrido.

---

## §8 Collegamenti

### Prerequisiti (devo sapere prima)

- [[Job Shop]] — la configurazione "padre", da cui la cella si evolve
- [[Flow Shop]] — la configurazione "figlia", verso cui la cella può evolvere
- [[Ciclo di lavorazione]] — l'unità di analisi su cui si basa la formazione delle famiglie
- [[Layout per processo]] — riferimento concettuale per i reparti residui
- [[Layout per prodotto]] — riferimento concettuale per la disposizione intra-cella

### Dipendenze (ciò che si appoggia su questa nota)

- [[Group Technology]] — il principio teorico applicato
- [[Famiglie di componenti]] — l'unità organizzativa fondamentale
- [[Diagramma multiprodotto]] — strumento operativo per identificare le famiglie
- [[Saturazione e numero macchine]] — dimensionamento di ciascuna cella
- [[Bilanciamento linea monoprodotto]] — applicabile all'interno della cella
- [[Analisi CVP]] — confronto economico con le alternative

### Concetti correlati

- [[Setup e riattrezzaggi]] — la riduzione dei setup interni è la chiave del vantaggio
- [[WIP - Work In Process]] — la riduzione del WIP è il principale beneficio operativo
- [[Tempo di attraversamento]] — stabile e prevedibile nella cella

---

## §9 Auto-verifica

1. **(Base)** Qual è la differenza concreta tra una _cella_ di group technology e un _reparto_ di job shop?
2. **(Media)** Perché una cella ha _minore_ flessibilità di un job shop, pur essendo "più moderna"? Da cosa deriva questa rigidità in pratica?
3. **(Profonda)** In quali condizioni di mercato e produzione una cella evolve naturalmente in flow shop, e quali sono le tre cose che cambiano in questo passaggio?

---

> [!note] Posizionamento nel sistema Questa nota si colloca all'interno del [[06 Cap6 - Layout e flussi di materiali]] come una delle quattro tipologie di layout fondamentali (insieme a [[Layout a postazioni fisse]], [[Layout per processo]], [[Layout per prodotto]]). Concettualmente è il "ponte" tra il Cap2 (classificazione: group technology) e il Cap6 (layout fisico).