
> [!info] Classificazione **Concetto quantitativo** (basato su soglie percentuali e calcolo cumulato), con una componente metodologica di triage. La struttura di §5 e §6 segue lo schema quantitativo.

**In 10 secondi:** una manciata di codici/prodotti genera la maggior parte del valore. L'analisi ABC li separa in tre fasce di importanza (A, B, C) per concentrare attenzione, dettaglio progettuale e risorse dove il ritorno è più alto.

---

## §1 Domanda fondamentale

Quando ho un mix di prodotti, codici a magazzino o famiglie tecnologiche **molto numerosi**, su quali concentrare l'analisi dettagliata (cicli di produzione, dimensionamento, controllo) senza affogare nei dati?

---

## §2 Il problema concreto

Pensa a **LumièreCo**, brand di cosmetica medio con 200 SKU a catalogo: rossetti, fondotinta, palette occhi, skincare, profumi. La direzione operations sta progettando il nuovo magazzino centrale e si trova davanti un foglio Excel con 200 righe di codici, ognuno con la propria giacenza media e il proprio fatturato annuo.

Dei 200 SKU:

- **20** sono best-seller stagionali ad alta rotazione (mascara iconico, primer top di gamma).
- **50** sono linee mature consolidate.
- I restanti **130** sono coda lunga: edizioni limitate, varianti regionali, codici in fase di phase-out.

Dimensionare il magazzino significa decidere spazio, scaffalature e sistemi di movimentazione **per ogni codice**. Studiarli tutti e 200 in dettaglio richiederebbe mesi e ritarderebbe il progetto; ignorarne alcuni rischia di sotto-dimensionare aree critiche.

**Il dilemma**: serve un criterio rigoroso per decidere **dove vale la pena spendere tempo** e dove invece bastano coefficienti di sicurezza standard.

---

## §3 La definizione

L'**analisi ABC** (o **analisi di Pareto**, o **regola 80-20**) è una tecnica di classificazione che ordina un insieme di elementi per valore decrescente di un parametro scelto, ne calcola il contributo cumulato e li raggruppa in tre fasce di importanza.

**Scomposizione in parti**:

```
Fascia A (verde)  : elementi che contribuiscono fino a ~80% del valore totale
Fascia B (giallo) : elementi che portano dal ~80% al ~95% del valore
Fascia C (rosso)  : elementi che completano il restante 5% (apporto marginale)
```

Tipicamente, **circa il 20% degli elementi** ricade in fascia A — da cui il nome "regola 80-20".

Componenti concettuali:

- **Asse x**: numero di elementi (codici, famiglie, SKU…), ordinati per valore decrescente, spesso espresso come % del totale.
- **Asse y**: valore cumulato percentuale del parametro scelto.
- **Soglie 80/95/100**: convenzioni operative, **non dogmi** — variano col parametro e col contesto.
- **Parametro**: dipende dall'obiettivo (giacenza, fatturato, profitto, n. movimentazioni, capitale immobilizzato, costo MP…).

---

## §4 Come funziona

**Cuore in una frase**: ordinare per importanza, sommare progressivamente, tagliare dove si raggiungono le soglie.

**Connessione delle parti**:

1. Scegli **cosa misurare** (parametro coerente con la decisione da prendere).
2. Calcola il valore di ogni elemento e **ordinali in senso decrescente**.
3. Costruisci l'**istogramma cumulato**: per ogni elemento somma il suo valore a quelli precedenti, dividi per il totale.
4. Applica le soglie 80/95/100 → fasce A, B, C.
5. **Politica differenziata** per fascia: A → analisi dettagliata; B → analisi mirata; C → semplificazione, coefficienti standard, eventuale eliminazione.

**Casi limite e varianti**:

- _Cambia il parametro, cambia la classificazione_: lo stesso codice può finire in classe B per quantità immagazzinata e in classe A per valore economico totale (es. profumo di lusso → alto valore unitario, bassa rotazione).
- _Distribuzione poco "pareto-iana"_: se la curva cumulata è quasi lineare (tutti gli elementi pesano in modo simile), l'analisi ABC perde potere discriminante → segnale che il portafoglio è già selezionato o omogeneo.
- _ABC incrociata_: combinare due parametri (es. fatturato × n. movimentazioni) genera matrice 3×3, utile per politiche di stoccaggio differenziate (alto valore + alta movimentazione → zona picking dedicata; alto valore + bassa movimentazione → area sicurezza).

**Doppio uso nel corso**:

- **Cap 4 — Mix produttivo**: parametro = fatturato/profitto delle famiglie di prodotto. Output: fascia A → progettazione dettagliata del ciclo di produzione; fascia C → candidate all'eliminazione dal programma; fascia B → analisi ulteriore di convenienza.
- **Cap 6 — Magazzini**: parametro = giacenza media (o capitale immobilizzato, o n. movimentazioni). Output: dimensionamento concentrato sulle classi A+B (≈95% delle giacenze); per la C bastano coefficienti di sicurezza. Tipico in questo dominio: 10% codici → 70-80% giacenze (A); 25% → 15-25% (B); 65% → 5% (C).

---

## §5 Applicazione pratica

### Formula di base

Per N elementi ordinati per valore decrescente $v_1 \geq v_2 \geq \dots \geq v_N$, la quota cumulata al k-esimo elemento è:

$$ Q_k = \frac{\sum_{i=1}^{k} v_i}{\sum_{i=1}^{N} v_i} \cdot 100~ $$

L'elemento k-esimo appartiene a:

- **Fascia A** se $Q_k \leq 80~$
- **Fascia B** se $80~ < Q_k \leq 95~$
- **Fascia C** se $Q_k > 95~$

### Procedura step-by-step

1. **Definisci il parametro** in linea con l'obiettivo (giacenza, fatturato, capitale, movimentazioni, profitto…).
2. **Raccogli i dati** per ogni elemento del set, allineati allo stesso periodo temporale.
3. **Ordina in senso decrescente** rispetto al parametro.
4. **Calcola il totale** $V_{tot} = \sum v_i$.
5. **Calcola la quota cumulata** elemento per elemento.
6. **Assegna la fascia** secondo le soglie scelte (80/95 o varianti).
7. **Verifica la "pareto-bontà"**: la fascia A dovrebbe contenere idealmente ~20~ degli elementi. Se ne contiene il 60~, le soglie vanno ricalibrate o il parametro non è informativo per il tuo caso.
8. **Definisci policy per fascia** (controllo, dimensionamento, eliminazione, riprogettazione).

### Checklist pre-applicazione

- [ ] Il parametro scelto riflette davvero l'importanza per la decisione che devo prendere?
- [ ] Ho i dati allineati allo stesso periodo temporale?
- [ ] Ho ordinato in senso decrescente **prima** di calcolare la cumulata?
- [ ] Le soglie 80/95% sono adatte al mio caso o vanno tarate (es. magazzino: 70/95)?
- [ ] Ho considerato di rifare l'analisi con un parametro diverso per una vista incrociata?
- [ ] Ho verificato che la fascia A contenga una minoranza di codici (regola di sanità)?

---

## §6 Esercizio tipo esame

**Traccia**: l'azienda **VeloMotor S.p.A.**, produttore automotive di componenti, ha a catalogo 10 codici di alberi motore. Il responsabile pianificazione ha estratto il fatturato annuo (in k€) per ciascun codice:

|Codice|Fatturato (k€)|
|---|---|
|AM-01|45|
|AM-02|380|
|AM-03|12|
|AM-04|220|
|AM-05|8|
|AM-06|95|
|AM-07|5|
|AM-08|150|
|AM-09|65|
|AM-10|20|

**Domande**:

- a) Classifica i codici in fasce A/B/C secondo l'analisi ABC sul fatturato.
- b) Quale percentuale di codici è in fascia A? Commenta rispetto alla regola 80-20.
- c) Se la direzione decidesse di eliminare i codici di fascia C, quanto fatturato perderebbe?

### Soluzione

**Step 1 — Ordina per fatturato decrescente e calcola il totale**:

$V_{tot} = 380 + 220 + 150 + 95 + 65 + 45 + 20 + 12 + 8 + 5 = 1000$ k€.

**Step 2 — Calcola quota singola e cumulata, assegna fascia**:

|Rank|Codice|Fatturato|% singola|Cumulato|% cumulata|Fascia|
|---|---|---|---|---|---|---|
|1|AM-02|380|38,0%|380|38,0%|A|
|2|AM-04|220|22,0%|600|60,0%|A|
|3|AM-08|150|15,0%|750|75,0%|A|
|4|AM-06|95|9,5%|845|84,5%|B|
|5|AM-09|65|6,5%|910|91,0%|B|
|6|AM-01|45|4,5%|955|95,5%|C|
|7|AM-10|20|2,0%|975|97,5%|C|
|8|AM-03|12|1,2%|987|98,7%|C|
|9|AM-05|8|0,8%|995|99,5%|C|
|10|AM-07|5|0,5%|1000|100,0%|C|

**Step 3 — Risposte**:

- **a)** **Fascia A**: AM-02, AM-04, AM-08 (3 codici). **Fascia B**: AM-06, AM-09 (2 codici). **Fascia C**: AM-01, AM-10, AM-03, AM-05, AM-07 (5 codici).
- **b)** Fascia A = 3/10 = **30% dei codici** → genera il **75% del fatturato**. La regola 80-20 è qui leggermente "spostata" (30% → 75% invece di 20% → 80%), ma il **principio Pareto è confermato**: una minoranza di codici fa la maggior parte del valore. Su soli 10 elementi, le percentuali "saltano" più grossolanamente: con N grandi la regola tende a stabilizzarsi vicino al canonico 20-80.
- **c)** Eliminando la fascia C si perderebbero $45 + 20 + 12 + 8 + 5 = 90$ k€, pari al **9% del fatturato totale**. La decisione va però completata valutando se quei codici di fascia C generano costi sproporzionati alla loro resa (set-up frequenti, scorta dedicata, complessità gestionale, occupazione di linea).

### Variante ("e se cambiasse X?")

> _E se avessi anche i dati di profitto e scoprissi che AM-06 (oggi in B) ha margine negativo, mentre AM-05 (oggi in C) ha margine altissimo?_

L'ABC sul fatturato perde rilevanza decisionale: andrebbe **rifatta sul profitto**. Probabilmente AM-06 scenderebbe di fascia (o uscirebbe dal portafoglio), mentre AM-05 — codice ad alta marginalità ma volumi bassi — salirebbe, magari fino in B. **Lezione**: la scelta del parametro coincide con la scelta della politica.

---

## §7 Errori comuni

> [!warning] ❌ Confondere "% codici" con "% valore" La regola 80-20 dice che **~20% degli elementi** porta **~80% del valore**. Non significa "80% dei codici è in classe A". Sull'asse x e y ci sono grandezze diverse. Chi sta in classe A è una **minoranza di codici** che pesa molto. Tieni separati mentalmente "quanti sono" e "quanto valgono".

> [!warning] ❌ Trattare 80/95/100 come soglie sacre Sono **convenzioni** che funzionano in molti casi ma vanno calibrate. Per il dimensionamento di magazzino il libro suggerisce per la classe A "10% degli articoli con il 70-80% delle giacenze" — già una variante. Se la tua distribuzione è diversa, sposta le soglie e dichiaralo esplicitamente.

> [!warning] ❌ Usare un solo parametro e fermarsi lì Un codice può essere classe C per quantità ma classe A per valore (es. componenti elettronici di alta gamma). Politiche di magazzino, controllo qualità e ciclo di produzione possono richiedere ABC diverse sullo **stesso set**. Se decidi su un solo parametro, rischi di sotto-tutelare codici critici.

---

## §8 Collegamenti

**Prerequisiti — cosa devo sapere prima**:

- [[Distinta base (BOM)]] e [[Ciclo di lavorazione]] — l'ABC è uno strumento dell'[[Ingegnerizzazione del prodotto]] e si applica al mix identificato dalla distinta.
- [[Programma di produzione]] — il set di partenza su cui eseguire l'ABC.
- [[Similitudine tecnologica]] — spesso si raggruppano i prodotti in famiglie _prima_ di applicare l'ABC.

**Conseguenze — cosa abilita / a cosa serve**:

- [[Make or buy]] — la fascia A (dettaglio) abilita la decisione make/buy informata; la fascia C spesso → buy o eliminazione.
- [[Dimensionamento magazzino]] — l'ABC sulle giacenze definisce il sottoinsieme su cui dimensionare ($G_{min}, G_m, G_{max}$).
- [[Group Technology]] e [[Layout a celle]] — l'ABC supporta l'identificazione delle famiglie tecnologiche su cui costruire le celle.
- [[VRP - Variety Reduction Program]] — l'ABC è un input per decidere quali codici unificare o eliminare.
- [[Mix produttivo]] — output diretto dell'analisi ABC su fatturato/profitto delle famiglie.

---

## §9 Auto-verifica

1. **Senza guardare la nota**, riassumi in 30 secondi cosa fa l'analisi ABC e qual è il suo output operativo.
2. Spiega **perché** lo stesso codice può finire in classi diverse cambiando il parametro: porta un esempio inventato (settore a tua scelta).
3. Nell'azienda VeloMotor, supponi che AM-02 (il codice di fascia A più importante per fatturato) sia anche quello con il **margine peggiore**. Come riorganizzi l'analisi e che decisione operativa prendi? _(Domanda critica: integra ABC, scelta del parametro, e ragionamento make/buy/keep.)_