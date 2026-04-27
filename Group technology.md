
> **In 10 secondi**: GT è una filosofia progettuale che riorganizza l'impianto in _celle_ dedicate a _famiglie_ di componenti accomunati da ciclo/geometria simile. Ibrido tra job-shop e flow-shop: meno flessibile del primo, più semplice del secondo. Riduce setup, WIP e tempi di attraversamento al prezzo di rigidità inter-cella.

**Tipologia**: concetto qualitativo (filosofia/metodologia organizzativa)

---

## §1 DOMANDA FONDAMENTALE

> Come ottengo i benefici di una linea (basso WIP, flusso semplice, saturazione alta) **senza** rinunciare del tutto alla flessibilità del job shop, quando i miei volumi sono troppo bassi per giustificare una linea dedicata per ogni prodotto?

---

## §2 IL PROBLEMA CONCRETO
Immagina un'azienda piemontese che produce **componenti meccanici per motori elettrici automotive** — alberi rotori, flange di accoppiamento, supporti statorici, carter in alluminio. Sembra una gamma ristretta, ma in realtà sono ~480 codici attivi raggruppabili in 6 macro-famiglie, con una domanda totale di 120.000 pezzi/anno e lotti tra 50 e 500 pezzi.

L'impianto oggi è organizzato come job shop classico: 4 reparti — 12 torni, 8 frese, 5 trapani, 4 rettifiche — e ogni codice attraversa 3-5 reparti seguendo il proprio ciclo. Sulla carta funziona; nei numeri quotidiani molto meno:

- tempo medio di attraversamento di un lotto: **18 giorni**
- di questi 18 giorni, solo **~11 ore** sono lavorazione effettiva
- il restante 99% del tempo è coda davanti a una macchina, attesa di trasporto, o stoccaggio intermedio
- WIP medio in stabilimento: **14.000 pezzi** parcheggiati ovunque
- saturazione macchine appena al **55%**
- e il 38% del tempo macchina se ne va in **setup**, perché due lavorazioni consecutive sullo stesso tornio sono spesso codici totalmente diversi (un albero, poi un carter, poi una flangia)

Il marketing chiede consegne entro 7 giorni. Da 18 a meno di 7 non si arriva con piccoli aggiustamenti — serve un cambio strutturale di layout.

L'ingegneria valuta i due estremi e li scarta entrambi:

- **Linea dedicata per ogni codice**: zero setup, massima velocità, ma con 480 codici e lotti da max 500 pezzi è economicamente impraticabile. Stai costruendo 480 mini-impianti che lavoreranno per pochi giorni l'anno ciascuno.
- **Restare in job shop**: investimento ridotto, massima flessibilità, ma il lead time di 18 giorni è strutturale — è una conseguenza geometrica di come sono disposte le macchine, non si abbatte con la sola gestione.

Però c'è un dato che apre la via di mezzo: i 480 codici **non hanno tutti cicli diversi**. Quando li classifichi per geometria + sequenza di operazioni, emergono spontaneamente 6 raggruppamenti naturali. Tutti gli alberi rotori si lavorano in modo simile tra loro, idem le flange, i supporti, i carter. Su questa osservazione si fonda la group technology.

---

## §3 LA DEFINIZIONE

> **Group technology**: filosofia progettuale che aggrega le risorse produttive in **celle**, ciascuna delle quali è univocamente assegnata a una **famiglia di componenti** caratterizzati da affinità di geometria e/o ciclo tecnologico.

La definizione regge su tre concetti che vanno digeriti uno alla volta.

**Famiglia.** Un insieme di codici che condividono geometria simile (tutti cilindri lunghi, tutti dischi forati, ecc.), oppure ciclo di lavorazione simile (tutti vogliono tornitura → fresatura → rettifica), oppure attrezzaggi compatibili. Il vero indicatore operativo è uno solo: il **setup tra un codice e l'altro della famiglia è breve**, molto più breve del setup necessario per passare a un codice di un'altra famiglia. Se quel test sui setup non torna, la famiglia non è ben definita — qualunque cosa dica la matrice teorica.

**Cella.** Il raggruppamento fisico delle macchine che servono a quella famiglia, e _solo_ di quelle. Non la metà di un reparto, non un'area condivisa con altri: macchine vere, dedicate, posizionate dove possibile in **disposizione lineare** seguendo la sequenza tipica del ciclo. La cella è di fatto un mini flow shop interno a un job shop più ampio.

**Vincolo di esclusività.** Una famiglia → una cella, in modo univoco. E una cella accetta solo la sua famiglia. Questo è il punto cruciale, e quello che spesso si fraintende: anche in caso di guasto di una macchina in cella, **non si dirottano i pezzi su celle vicine**. Se inizi a fare eccezioni — "oggi la rettifica di Cella 1 è ferma, mando questi alberi alla rettifica di Cella 2" — i setup brevi spariscono (perché Cella 2 non è attrezzata per gli alberi), le code tornano, e in pochi mesi la GT si è degenerata in un job shop con un layout diverso. La rigidità non è un limite implementativo: è il cuore del sistema.

---

## §4 COME FUNZIONA

> **Cuore**: si sostituisce la specializzazione _per tecnologia_ (job shop = "tutti i torni insieme") con la specializzazione _per prodotto_ (cella = "tutto ciò che serve alla famiglia A, insieme").

**Schema logico** (prima vs. dopo):

```
JOB SHOP (prima)                    GROUP TECHNOLOGY (dopo)
────────────────                    ───────────────────────

[Tornitura] ──┐                     Famiglia A (alberi)
[Fresatura] ──┤  flusso              ↓
[Foratura]  ──┤  disordinato        Cella 1:  tor → fres → rett
[Rettifica] ──┘  multi-direzione    
                                    Famiglia B (flange)
ogni codice attraversa               ↓
3–5 reparti, flussi                 Cella 2:  tor → for → rett
incrociati, code, WIP alto          
                                    Famiglia C (supporti)
                                     ↓
                                    Cella 3:  fres → for

                                    + operazioni FUORI CELLA
                                      (trattamenti termici,
                                       verniciatura) centralizzate
                                       per tutte le celle
```

**Dinamica chiave**:

- I **setup** crollano (intra-famiglia gli attrezzaggi sono simili)
- Il flusso intra-cella è **lineare e unidirezionale** (mini flow-shop)
- Inter-cella, l'organizzazione resta a reparti separati (no scambi tra celle)
- La manodopera si specializza meno _sul tipo di lavorazione_ e più _sulla famiglia di item_

**Casi limite e varianti**:

- _Estremizzazione_: famiglia = prodotti venduti a un singolo cliente → specializzazione commerciale spinta
- _Operazioni "fuori cella"_: lavorazioni costose o pericolose (trattamenti termici, verniciatura, lavorazioni superficiali) restano centralizzate → turbano la linearità ma sono inevitabili
- _Evoluzione naturale_: cella che cresce in volume → si trasforma in **flow shop** dedicato (next step)
- _Degenerazione_: se in caso di guasto si dirottano prodotti su celle adiacenti, la GT torna ad essere job shop → vincolo da preservare progettualmente

---

## §5 APPLICAZIONE PRATICA — Metodologia operativa

### Step-by-step (transizione job shop → GT)

Passare da job shop a GT non è un esercizio teorico, è un progetto vero con passi ordinati. Vale la pena vederli capendo il _perché_ di ognuno, non solo il _cosa_.

**Censimento dei codici.** Estrai dal database tutti i codici attivi e per ognuno il ciclo di lavorazione completo: sequenza delle operazioni, macchine usate, tempi di lavorazione e di setup. Senza questo dato non puoi raggruppare niente — è la base del progetto.

**Matrice pezzo-macchina.** Costruisci una matrice binaria: righe = codici, colonne = tipi di macchina, casella = 1 se quel codice usa quella macchina, 0 altrimenti. Sembra banale ma è lo strumento chiave: una volta che riordini righe e colonne ottenendo blocchi quasi-diagonali, ogni blocco è un candidato per una coppia (famiglia, cella). I codici dello stesso blocco condividono lo stesso sottoinsieme di macchine.

**Validazione tecnica sui setup.** La matrice ti dice "questi codici usano le stesse macchine", ma non basta: devi verificare empiricamente in officina che i tempi di attrezzaggio tra un codice e l'altro della stessa famiglia siano davvero brevi. Due codici possono passare entrambi su un tornio ma con utensili e maschere completamente diversi — in quel caso non sono della stessa famiglia, qualunque cosa dica la matrice.

**Dimensionamento di ogni cella.** Per ciascuna macchina della cella calcoli il numero di unità necessarie: `N_j = ⌈ Q_famiglia / P_j ⌉`. Importante: alzi il **target di disponibilità** delle macchine (≥ 95%) rispetto al job shop, perché in cella non hai backup esterni. MTBF alto, MTTR basso, manutenzione preventiva seria.

**Layout interno alla cella.** Disposizione lineare seguendo la sequenza prevalente del ciclo. Se lo spazio o l'esigenza di presidio multi-macchina lo suggerisce, valuti un **layout a U**: l'operatore al centro vede tutte le sue macchine e può intervenire ovunque senza spostarsi più di pochi metri.

**Operazioni fuori cella.** Identifichi esplicitamente quali lavorazioni resteranno centralizzate (trattamenti termici e simili) e progetti l'interfaccia di pianificazione: come si prenota il forno, chi muove i lotti, dove parcheggiano in attesa. Lasciare implicita questa parte è uno degli errori più frequenti, e fa rientrare le code dalla finestra.

**Sovradimensionamento di capacità.** Prevedi un margine del 10–20% di capacità in più per ogni cella. Sembra spreco ma è il prezzo della disciplina del flusso: dato che NON puoi dirottare verso altre celle, ti serve cuscinetto interno per assorbire le variazioni di mix all'interno della famiglia.

### Lista di controllo prima di chiudere il progetto

- [ ] le famiglie sono basate su **ciclo + geometria**, non su criteri commerciali (a meno che non sia esattamente il caso del cliente unico)
- [ ] ogni famiglia è assegnata a una sola cella, ogni cella accetta una sola famiglia
- [ ] tutti i codici della famiglia trovano in cella tutte le macchine necessarie — le uniche eccezioni sono le operazioni fuori cella esplicitamente identificate
- [ ] macchine in cella con disponibilità target ≥ 95% (MTBF/MTTR adeguati)
- [ ] previsto un meccanismo di pianificazione per le operazioni centralizzate
- [ ] capacità sovradimensionata del 10–20% per ogni cella
- [ ] verificata la stabilità del collo di bottiglia intra-cella al variare del mix di codici della famiglia
- [ ] costo della duplicazione di alcune macchine accettato (alcuni torni saranno presenti in più celle: è il prezzo da pagare)
---

## §6 DOMANDA TIPO ESAME (orale/scritto)

**Traccia**: _"Si discuta la group technology come soluzione impiantistica, evidenziandone i principi costitutivi, i vantaggi e i limiti rispetto al job shop e al flow shop. Si specifichi inoltre in quali condizioni di mercato e di portafoglio prodotti tale soluzione risulti preferibile."_

### Traccia di risposta strutturata (ordine consigliato)

1. **Definizione e collocazione concettuale**: GT è una _filosofia progettuale ibrida_, evoluzione naturale del job shop quando la domanda si specializza su un mix più ristretto e i volumi unitari salgono. Si colloca tra job shop (alta flessibilità, bassa efficienza) e flow shop (alta efficienza, bassa flessibilità).
    
2. **Tre principi costitutivi**:
    
    - aggregazione macchine in **celle** (non più reparti per tecnologia)
    - **assegnazione univoca** famiglia ↔ cella (NO instradamento incrociato)
    - disposizione **lineare** intra-cella secondo il ciclo prevalente
    - criterio di costituzione famiglia: affinità **geometrica + ciclo** → setup minimi
3. **Vantaggi vs job shop**:
    
    - WIP ↓ (programmazione semplificata, no colli di bottiglia imprevisti da congestione)
    - Tempi di attraversamento ↓ e soprattutto **più stabili** (migliore stima delle date di consegna)
    - Saturazione macchine ↑
    - Capacità di cella facilmente identificabile (collo di bottiglia stabile, item analoghi)
    - Schedulazione affrontabile con approcci di ottimizzazione (numero di soluzioni gestibile)
4. **Svantaggi e rigidità**:
    
    - **No** flessibilità inter-cella (un guasto in cella non può essere assorbito da celle adiacenti)
    - Necessità di macchine ad **alta disponibilità** + sovradimensionamento di capacità
    - Rischio di **sbilanciamento dei carichi** tra celle al variare del mix
    - Operazioni "fuori cella" turbano la linearità del flusso e complicano la programmazione
    - Possibile duplicazione di macchine (la stessa tipologia in più celle)
5. **Confronto con flow shop**: GT è meno rigida (la cella lavora N codici della famiglia, una linea no), meno automatizzata, ma anche meno costosa — adatta a volumi medi.
    
6. **Condizioni di applicabilità**:
    
    - Volumi unitari **medi** (più alti del job shop, più bassi del flow shop)
    - Mix produttivo **specializzabile** in famiglie tecnologiche identificabili
    - Domanda relativamente **stabile** sul mix di famiglie (alta turbolenza → tante operazioni fuori cella → vantaggi GT erosi)
    - Volontà di abbattere lead time e WIP, in cambio di flessibilità
7. **Chiusura**: la GT è raramente applicabile a _tutto_ il sistema produttivo; tipicamente si configura un **sistema misto** in cui parte è organizzata per celle e parte rimane a reparti — più crescono le due porzioni, più diventa critico il **coordinamento complessivo**.
    

---

## §7 ERRORI COMUNI

> [!warning] Errore 1 — Confondere GT con un job shop "ben organizzato" ❌ Pensare che basti raggruppare fisicamente macchine per ottenere GT. **Perché**: il principio costitutivo è l'**assegnazione univoca famiglia → cella** + il vincolo che impedisce dirottamenti tra celle. Senza questi vincoli, la soluzione "degenera" automaticamente in job shop al primo guasto o picco di domanda. ✅ **Come evitarlo**: nella verifica progettuale, controlla esplicitamente che NON sia previsto instradamento di prodotti tra celle (le sole eccezioni ammesse sono le operazioni fuori cella centralizzate, esplicitamente progettate).

> [!warning] Errore 2 — Costituire famiglie su criteri commerciali invece che tecnologici ❌ Aggregare prodotti perché venduti allo stesso cliente, allo stesso canale, con lo stesso imballo. **Perché**: la famiglia GT serve a ridurre i **setup intra-famiglia** e a permettere flusso lineare. Criteri commerciali non garantiscono affinità di ciclo o geometria → potresti finire con setup lunghi anche dentro la cella e perdere il vantaggio principale. ✅ **Come evitarlo**: parti dalla **matrice pezzo-macchina** e dalla **verifica empirica dei tempi di setup**. I criteri commerciali al massimo possono raffinare il clustering, mai guidarlo.

> [!warning] Errore 3 — Sottostimare il rischio di sbilanciamento di carico ❌ Dimensionare ogni cella sulla domanda media della propria famiglia, "tanto poi si compensa". **Perché**: in GT la cella NON ha ridondanza esterna. Se la domanda della famiglia A cresce e quella di B cala, la cella A satura mentre B resta scarica e _non puoi_ spostare prodotti — è un vincolo di progetto, non un'inefficienza temporanea. ✅ **Come evitarlo**: sovradimensiona la capacità di ogni cella (10-20%); monitora la stabilità del mix nel tempo storico; in caso di domanda molto turbolenta, valuta esplicitamente soluzioni miste (parte in celle, parte a reparti).

---

## §8 COLLEGAMENTI

### Prerequisiti (sapere PRIMA)

- [[Job shop]] — la GT nasce come evoluzione del job shop
- [[Famiglie di prodotto]] — concetto di aggregazione codice/famiglia/tipo
- [[Setup]] — la riduzione dei setup è il driver principale della GT
- [[Ciclo di lavorazione]] — la GT si fonda sull'analogia di cicli
- [[02 Cap2 — Classificazione dei sistemi di produzione]] — quadro complessivo

### Conseguenze (cosa ne consegue)

- [[Flow shop]] — evoluzione naturale di una cella ad alti volumi
- [[Layout a celle]] — applicazione fisica del principio GT al [[06 Cap6 — Layout e flussi|layout]]
- [[Saturazione macchine]] — la GT la migliora, ma richiede sovradimensionamento
- [[WIP]] — la GT lo riduce drasticamente
- [[Collo di bottiglia]] — in GT è **stabile** intra-cella (vantaggio chiave per programmazione)
- [[Postponement]] — la GT abilita strategie di customizzazione tardiva su famiglie

### Trade-off chiave

> flessibilità ↔ efficienza → la GT si colloca in posizione **intermedia**, prendendo un po' di entrambi

---

## §9 AUTO-VERIFICA

1. **Base**: Quali sono i 3 principi costitutivi che distinguono una cella GT da un raggruppamento qualunque di macchine?
    
2. **Medio**: Spiega perché in una soluzione GT è essenziale che le macchine in cella abbiano alta disponibilità (alto MTBF, basso MTTR), mentre in un job shop questo vincolo è meno stringente. (Suggerimento: pensa a cosa succede in caso di guasto.)
    
3. **Avanzato**: Un'azienda con domanda molto **volatile** sul mix prodotti (es. settore moda) ha 5 celle GT bilanciate sulla domanda media annua. Cosa accade nei mesi in cui la domanda di una famiglia raddoppia mentre un'altra dimezza? Quali contromisure progettuali si possono adottare _senza_ tornare a un job shop?




![[job_shop_vs_group_technology_layout.svg]]
