---
aliases:
  - "Job Shop"
  - "Job-shop"
---


> [!tldr] In 10 secondi Il **job shop** è la soluzione impiantistica della massima flessibilità: macchine **general-purpose** raggruppate in **reparti per affinità tecnologica** (reparto torni, reparto frese…), in cui ogni prodotto segue un proprio routing — anche alternativo — attraversando i reparti che gli servono. Sinonimo di "produzione per reparti". È l'opposto polare del [[Flow Shop]].

---

## §1 Domanda fondamentale

**Come organizzo un sistema produttivo quando ogni ordine è diverso dal precedente, i volumi unitari sono bassi, e devo poter inserire nuovi prodotti continuamente senza riprogettare la fabbrica?**

---

## §2 Il problema concreto

Immagina la **Sartoria Verducci**, atelier sartoriale di alta moda maschile vicino a via Montenapoleone, Milano (settore **moda**). Producono **250 abiti bespoke all'anno**, ognuno tagliato e cucito su misura. Prezzo medio: **8.000 €**, lead time **6 settimane**.

I reparti sono organizzati per affinità tecnologica:

```
Reparto taglio       → 2 tavoli + 1 plotter da taglio + 3 tagliatori
Reparto sartoria     → 8 macchine da cucire industriali + 8 sarti
Reparto ricamo       → 3 telai a mano + 2 macchine da ricamo + 2 ricamatrici
Reparto rifinitura   → 4 stazioni di stiro + 4 finishers
Reparto controllo    → 1 stazione + 1 master tailor
```

Ogni abito ha una **scheda di lavorazione diversa**:

- Cliente A: smoking 3 pezzi → taglio → sartoria → rifinitura → controllo (no ricamo)
- Cliente B: giacca cerimonia → taglio → sartoria → ricamo (monogramma) → sartoria (rientro per asole) → rifinitura → controllo
- Cliente C: completo viaggio → taglio → sartoria → rifinitura → sartoria (correzione su prova) → rifinitura → controllo

In qualsiasi momento ci sono **circa 35 abiti contemporaneamente in lavorazione** (WIP), ognuno in un reparto diverso, ciascuno con priorità e date di consegna proprie.

**Il dilemma:**

- Non posso usare una linea ([[Flow Shop]]): non c'è un "abito tipo" da replicare, ogni cliente è una storia diversa.
- Non posso usare celle ([[Group Technology]]): il volume è troppo basso per dedicare risorse a famiglie di prodotti.
- Mi serve una soluzione che **assorba la variabilità** ma mi permetta di lavorare in modo razionale: macchine generiche, persone specializzate, reparti a vocazione tecnologica, e ordini che fluiscono ognuno per la sua strada.

Questa è esattamente la **filosofia del job shop**.

---

## §3 La definizione

Il **job shop** è un sistema produttivo caratterizzato da **attrezzature e manodopera genericamente in grado di svolgere più tipologie di lavorazioni**, organizzate in **reparti per affinità tecnologica**. È tipicamente la soluzione per prodotti realizzati su **ordine singolo o serie limitata**.

È spesso usato come **sinonimo di "produzione per reparti"** o "[[Layout per processo]]", per via dell'articolazione del processo produttivo per macchinari e operazioni omogenee sotto il profilo funzionale o tecnologico, con flussi fisici molto complessi e articolati.

**Scomposizione in parti:**

|Componente|Ruolo|
|---|---|
|**Macchine general-purpose**|progettate per ampia gamma di prodotti, non ottimizzate per famiglia specifica|
|**Reparti per affinità tecnologica**|torni, frese, rettifiche, foratrici… (oppure taglio, cucitura, rifinitura nella moda)|
|**Routing per-prodotto**|ogni prodotto ha il proprio ciclo tecnologico, spesso con **routing alternativi** (la stessa lavorazione su macchine diverse)|
|**Manodopera = risorsa critica**|spesso più macchine che persone; la qualità del prodotto dipende dalle persone|
|**Scorte interoperazionali**|code/buffer tra reparti che disaccoppiano le fasi e assorbono la variabilità|
|**Flussi intrecciati**|i routing dei diversi prodotti si incrociano, generando attese|

**Esempi tipici dal manuale:** fabbricazione calzaturiera (trancia, giunteria, manovia), mobiliera (taglio, squadrabordatura, nastratura, finitura), meccanica (tornitura, fresatura, lappatura, foratura).

---

## §4 Come funziona

**Il cuore in una frase:** il job shop scambia **efficienza per flessibilità totale** — accetta WIP alti, tempi di attraversamento lunghi e saturazione bassa, in cambio della capacità di gestire qualsiasi prodotto, qualsiasi mix, qualsiasi volume.

**Come si connettono le parti:**

1. **Macchine generiche** → posso usarle per qualunque prodotto → posso accettare ordini eterogenei.
2. **Raggruppate per affinità tecnologica** (tutte le frese insieme, tutti i torni insieme) → la manodopera si specializza per **tecnologia** (un buon fresatore, un buon tornitore), non per prodotto.
3. **Routing libero per ogni prodotto** → ogni ordine "naviga" nei reparti che gli servono, nell'ordine che gli serve → flussi intrecciati.
4. **Routing alternativi** → se il tornio T3 è guasto o saturo, uso T2 dello stesso reparto, o magari un tornio di un altro reparto: **robustezza ai guasti**, ma anche tante opzioni di programmazione.
5. **Scorte interoperazionali** tra reparti → ogni reparto può lavorare al proprio ritmo senza essere bloccato dai vicini.
6. **Manodopera = risorsa critica** (più macchine che persone) → posso aumentare i volumi assumendo, non comprando macchine: **elasticità di volume tramite persone**.

**La flessibilità è triplice** (questo è il punto da ricordare a memoria):

- **Flessibilità di prodotto:** macchine generiche + scorte di disaccoppiamento → inserisco un nuovo prodotto, anche da industrializzare, senza disturbare la produzione esistente.
- **Flessibilità di mix:** posso passare da un mix a un altro velocemente, anche in corso d'opera.
- **Flessibilità di volume:** aggiungo manodopera (la risorsa scarsa) → cresco facilmente.

**Cosa accade se…**

- **…si guasta una macchina?** Esistono routing alternativi e scorte di disaccoppiamento. La produzione continua, eventualmente più lenta, ma non si ferma.
- **…aumento i volumi?** Assumo personale qualificato. Le macchine sono sotto-saturate, c'è capacità di assorbimento.
- **…un prodotto diventa volume-leader?** Migra fuori dal job shop: prima va a [[Group Technology]] (cella dedicata), poi eventualmente a [[Flow Shop]] (linea automatizzata). Il job shop è una "**incubatrice**" di prodotti.
- **…cresce troppo il numero di ordini contemporanei?** Il sistema collassa sulla **schedulazione**: il problema diventa "due risorse critiche (manodopera + macchine) con routing arbitrari" → matematicamente intrattabile. WIP esplode, tempi di attraversamento si dilatano in modo imprevedibile, le date di consegna saltano.

---

## §5 Applicazione pratica — quando e come scegliere il job shop

**Metodologia operativa step-by-step**

**Step 1 — Verifica le pre-condizioni di mercato/prodotto**

- Volumi unitari **bassi o medio-bassi** per singolo prodotto.
- Mix prodotti **ampio e variabile**, possibilmente con prodotti nuovi che entrano spesso.
- Modalità di risposta: tipicamente [[CODP - Customer Order Decoupling Point|MTO, PTO o ETO]] (raramente MTS).
- Concorrenza basata su **personalizzazione, qualità sartoriale, varietà**, non su prezzo unitario.

**Step 2 — Mappa i routing dei prodotti realizzabili**

- Per ogni prodotto: quali operazioni servono e in che ordine?
- Identifica le tecnologie comuni → suggeriscono i reparti.
- Verifica che la sovrapposizione tra routing sia **bassa** (se tutti i prodotti seguono lo stesso ordine di operazioni → forse ti serve una linea, non un job shop).

**Step 3 — Raggruppa le macchine per affinità tecnologica**

- Reparto torni, reparto frese, reparto saldatura… (o nella moda: taglio, cucitura, ricamo, rifinitura).
- Macchine **general-purpose**: scegli capacità ampie, non specializzate.
- Lascia spazio per crescere: nuove macchine simili si aggiungono al reparto già esistente.

**Step 4 — Dimensiona le scorte interoperazionali**

- Servono per disaccoppiare i reparti e assorbire la variabilità di tempi e priorità.
- Non sono "spreco": sono la condizione che permette al sistema di funzionare.
- Più variabilità → più scorte (consapevolezza, non bug).

**Step 5 — Dimensiona la manodopera (la risorsa critica)**

- Calcola fabbisogno per reparto in base ai routing previsti.
- Punta sulla **polivalenza** dentro il reparto (un sarto sa fare giacche e pantaloni; un tornitore sa fare diversi tipi di pezzi).
- La leva di crescita futura sarà l'assunzione, non l'acquisto macchine.

**Step 6 — Pianifica il sistema di programmazione**

- Accetta che la programmazione di ottimo è impossibile (troppi gradi di libertà).
- Usa **regole di priorità euristiche** (FIFO, EDD - Earliest Due Date, SPT - Shortest Processing Time…).
- Assegna a ogni reparto un **capo reparto bravo**: nel job shop la qualità della gestione operativa dipende molto dalle persone.

**Step 7 — Accetta consapevolmente i punti deboli**

- Tempi di attraversamento lunghi e variabili → comunica al cliente lead time prudenti.
- WIP alto → mettilo a budget.
- Saturazione macchine bassa (es. 40–60%) → è il prezzo della flessibilità, non un difetto da correggere.
- Qualità meno costante → introduci controlli intermedi e formalizza istruzioni di lavoro.

> [!check] Checklist rapida prima di decidere "job shop sì/no"
> 
> - [ ] Volumi unitari bassi (decine/centinaia di pezzi diversi all'anno)?
> - [ ] Mix prodotti ampio e in continua evoluzione?
> - [ ] Routing diversi tra prodotti (poca standardizzazione del ciclo)?
> - [ ] Mercato di tipo MTO / PTO / ETO?
> - [ ] Manodopera qualificata disponibile e centrale per la qualità?
> - [ ] Tolleri WIP alto, saturazione bassa, lead time variabili?
> - [ ] Necessità di robustezza ai guasti e ai cambi di priorità?
> 
> **Se la maggior parte è sì → job shop. Se i volumi salgono e il mix si stabilizza su poche famiglie → cominci a guardare verso [[Group Technology]].**

---

## §6 Domanda tipo esame

> **Domanda (orale/scritto):** Discuti il job shop come soluzione impiantistica. In particolare: definiscilo, posizionalo nella matrice prodotto-processo, illustra le tre dimensioni di flessibilità che lo caratterizzano, e i suoi principali punti di debolezza. Spiega il "paradosso della flessibilità" del job shop e in quali condizioni esso è la soluzione fisiologica.

**Traccia di risposta strutturata** (i punti vanno toccati in quest'ordine):

1. **Definizione (30 sec):** Il job shop è un sistema produttivo con macchine general-purpose, manodopera generica, organizzato per **reparti per affinità tecnologica** (torni, frese, rettifiche…). Sinonimo di "produzione per reparti". Ogni prodotto ha un proprio ciclo tecnologico (routing), spesso con routing alternativi. La manodopera è la **risorsa critica** (più macchine che persone). Esempi: fabbricazioni calzaturiere, mobiliere, meccaniche.
    
2. **Posizionamento nella matrice prodotto-processo:** **Vertice in alto a sinistra** (alta varietà, bassi volumi, flusso frammentario). Lungo la diagonale fisiologica: job shop → group technology → flow shop → processo continuo. Modalità di risposta al mercato compatibile: ETO, PTO, MTO.
    
3. **Le tre dimensioni di flessibilità:**
    
    - **Prodotto:** macchine generiche e scorte di disaccoppiamento → posso introdurre nuovi prodotti senza riprogettare la fabbrica.
    - **Mix:** posso passare da un mix a un altro rapidamente, anche in corso d'opera.
    - **Volume:** aggiungo manodopera (la risorsa scarsa) per crescere → elasticità produttiva facile.
4. **Punti di debolezza** (da elencare con ordine):
    
    - **Programmazione difficile:** paradosso della flessibilità (vedi punto 5).
    - **Generazione di WIP elevato** (guasti, cambi di priorità, congestioni, colli di bottiglia imprevisti).
    - **Scarsa saturazione delle macchine** (gran parte del tempo di attraversamento è improduttivo).
    - **Costo manodopera** alto rispetto a sistemi automatizzati.
    - **Difficoltà di gestione** della manodopera, dipendente dal capo reparto.
    - **Schedulazione con due risorse critiche** (uomini + macchine) → problema NP-difficile.
    - **Qualità meno costante** rispetto a sistemi più automatizzati.
5. **Il paradosso della flessibilità (punto chiave da non saltare):** _paradossalmente, l'estrema flessibilità del job shop ne ostacola la programmabilità_. Il numero di soluzioni di programmazione possibili è talmente ampio da rendere virtualmente impossibile l'introduzione di approcci di ottimizzazione. Anche definire la capacità produttiva e i vincoli del sistema è difficile, con ricadute sulla **prevedibilità dei tempi di consegna**.
    
6. **Condizioni fisiologiche:** Volumi unitari bassi o medio-bassi, mix prodotti ampio e variabile, mercato che apprezza personalizzazione e varietà più del prezzo, prodotti spesso unici o in serie limitata. Quando un prodotto cresce in volume e si stabilizza, esce dal job shop e migra naturalmente verso [[Group Technology]] (e, se cresce ancora, verso [[Flow Shop]]).
    

---

## §7 Errori comuni

> [!warning] ❌ Errore 1: pensare che "job shop = inefficiente" Il job shop **non è** un sistema mal progettato: è la soluzione **giusta** per il problema giusto (alta varietà, bassi volumi, ordini eterogenei). Il vero errore è usarlo per produzioni che dovrebbero essere flow shop (alti volumi standardizzati): in quel caso si paga la flessibilità senza usarla. La saturazione bassa, il WIP alto, i tempi lunghi sono il **prezzo strutturale** della flessibilità, non un difetto da correggere a tutti i costi. La domanda corretta non è "come rendo questo job shop efficiente?" ma "il job shop è ancora la soluzione giusta per la mia domanda?".

> [!warning] ❌ Errore 2: confondere "job shop" e "layout per processo" Sono concetti **strettamente correlati ma non identici**. Il [[Layout per processo]] è la **disposizione spaziale fisica** delle macchine (come sono messe nello stabilimento). Il job shop è la **soluzione impiantistico-organizzativa**: include il layout per processo + la filosofia di routing libero + la specializzazione della manodopera per tecnologia + il modello di gestione delle scorte interoperazionali. In pratica si usano come sinonimi al 99%, ma all'orale il professore può chiederti la differenza: il layout è "dove stanno le macchine", il job shop è "come funziona tutto il sistema".

> [!warning] ❌ Errore 3: sottovalutare il ruolo della manodopera vs. macchine Nel flow shop la **macchina** è la risorsa critica (specializzata, costosa, satura). Nel job shop la **manodopera** è la risorsa critica: spesso ci sono più macchine che persone, e la qualità del prodotto + la velocità di esecuzione dipendono dal singolo operatore. Conseguenze pratiche da non dimenticare: (a) la **schedulazione** è un problema con **due risorse critiche** simultanee, (b) la crescita di volume si fa con assunzioni, non con investimenti in macchinari, (c) il capo reparto è figura strategica.

---

## §8 Collegamenti

**Prerequisiti (cosa devi sapere PRIMA):**

- [[Routing / Ciclo tecnologico]] — concetto base che sta dietro al job shop
- Macchine general-purpose vs specializzate — distinzione costitutiva
- Reparti per affinità tecnologica — principio organizzativo
- [[CODP - Customer Order Decoupling Point|CODP]] — contesto di mercato compatibile
- [[Matrice Prodotto-Processo]] — dove si colloca il job shop (vertice alto-sinistra)
- [[Classificazione per processi tecnologici|Produzione per parti vs per processo]] — il job shop è quasi sempre per parti
- Discreta (unitaria / a lotti) vs continua — il job shop è discreto

**Conseguenze (cosa ne dipende DOPO):**

- [[Group Technology]] — l'evoluzione naturale quando i volumi salgono e il mix si specializza
- [[Flow Shop]] — il polo opposto, lo sbocco finale dell'evoluzione
- [[Layout per processo]] — la traduzione spaziale del job shop
- [[WIP - Work In Process]] — strutturalmente alto in job shop
- [[Tempi di attraversamento]] — lunghi e variabili
- [[Saturazione e Coefficiente di utilizzazione]] — strutturalmente bassa
- Schedulazione e regole di priorità — FIFO, EDD, SPT in contesto job shop
- [[OEE]] e [[TEEP]] — Ep tipica 0.65–0.80 per reparti (vs 0.80–0.95 per linee)
- [[Scorte interoperazionali]] — disaccoppiano i reparti
- [[Diagramma multiprodotto]] — strumento di analisi flussi tipico in job shop

---

## §9 Auto-verifica

1. **(facile)** Cos'è un job shop? In una frase: come sono organizzate le macchine, qual è la sua risorsa critica, e qual è il suo principale punto di forza?
    
2. **(medio)** Spiega il "paradosso della flessibilità" del job shop. Perché la stessa caratteristica che lo rende prezioso (la flessibilità) è anche la sua principale debolezza in fase di programmazione e schedulazione?
    
3. **(profondo)** Un'azienda di **stampi industriali per il settore farmaceutico** ha 80 dipendenti e produce circa 500 stampi diversi all'anno, ognuno custom. Lavora in modalità ETO. Il management propone di passare a una soluzione meno flessibile (celle group-tech) per ridurre il WIP e i tempi di attraversamento. Cosa le suggeriresti di analizzare prima di decidere? In quali condizioni la migrazione è giustificata, e in quali sarebbe un errore strategico?
    

---

Coppia ufficialmente chiusa: **[[Job Shop]] ↔ [[Flow Shop]]** sono i due poli della classificazione, [[Group Technology]] è lo step intermedio. Se vuoi, il prossimo step naturale è proprio la nota su **[[Group Technology]]** (per chiudere il triangolo delle soluzioni impiantistiche), oppure la **[[Matrice Prodotto-Processo]]** (che fa da framework unificante per tutte e tre). Quale preferisci?