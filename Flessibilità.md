

> **In 10 secondi:** capacità di un sistema aziendale _nel suo complesso_ di reagire a cambiamenti del contesto (nuovi prodotti, mix, volumi, piani di consegna). Si misura in tempo di risposta + costo di risposta. Si declina in 4 dimensioni. Non va confusa con la _versatilità_, che riguarda solo i macchinari.

---

## §1 Domanda fondamentale

**Come misuro e governo la capacità del mio sistema produttivo di reagire ai cambiamenti che il mercato mi chiede — distinguendo cosa dipende dalle macchine e cosa dipende dall'organizzazione nel suo complesso?**

In altre parole: il mio impianto risponde bene a _cosa_? A più prodotti nello stesso lotto? A nuovi modelli che arrivano? A picchi di volume? A cambi di scadenza in corsa? Sono cose diverse, e si pagano in modi diversi.

---

## §2 Il problema concreto

Immagina **Filomena & Co.**, produttore italiano di abbigliamento medio-alto. Storia tipica: 2 collezioni/anno (primavera-estate, autunno-inverno), 180 SKU per collezione, lead time tipico di **4 mesi** tra disegno e capo in negozio. Sistema produttivo: macchine da taglio versatili, ma cicli di lavoro ottimizzati per lotti da 800 capi e fornitori di tessuto contrattualizzati con lead time di 6 settimane.

A inizio anno, la direzione decide: per non perdere terreno contro i concorrenti fast-fashion, si lancia una **"fast collection"** parallela:

- **50 nuovi SKU/mese**
- Lead time obiettivo: **2 settimane** dall'idea al negozio
- Lotti da **100–300 capi** invece che 800
- Possibilità di **ri-pianificare la settimana successiva** se un capo "tira" più del previsto

Le richieste alla produzione esplodono in 4 direzioni contemporaneamente:

1. _"Riusciamo a gestire un mix così ampio senza che i setup ci uccidano?"_
2. _"Come industrializziamo 50 nuovi codici al mese, ognuno con cartamodello, marker, scheda tecnica?"_
3. _"E se a marzo le vendite di certi capi triplicano e dobbiamo seguirle?"_
4. _"E se a metà settimana ci dicono di interrompere il capo X e accelerare il capo Y?"_

**Il dilemma:** le macchine attuali sono parzialmente versatili (la macchina da taglio è general-purpose), ma il **know-how**, l'**organizzazione**, i **fornitori** e le **procedure** sono pensati per un mondo a 4 mesi e 800 pezzi. Comprare nuove macchine non basta. Filomena ha bisogno di capire _che tipo_ di flessibilità le manca, perché ogni tipo richiede interventi diversi.

---

## §3 La definizione

> **Flessibilità:** insieme delle risposte che un sistema aziendale nel suo complesso è in grado di generare a fronte di variazioni e richieste — lancio di nuovi prodotti, evoluzione di specifiche, variazioni di volume, modifiche dei piani di consegna.

Punto chiave della definizione: **"sistema aziendale nel suo complesso"**. Non solo macchine: anche know-how, personale, organizzazione, procedure di programmazione e controllo, fornitori, sistemi informativi.

### Le 4 dimensioni della flessibilità

```
Flessibilità
├── di MIX        : capacità di riassortire un'ampia gamma a costi accettabili
│                   nell'ambito di un range definito
│                   "posso passare in fretta da A a B a C?"
│
├── di PRODOTTO   : capacità di industrializzare un nuovo codice
│                   con tempi e costi accettabili
│                   "posso introdurre qualcosa che prima non esisteva?"
│
├── di VOLUME     : capacità di assorbire variazioni quantitative
│ (= elasticità)    mantenendo livelli di efficienza adeguati
│                   "posso fare di più o di meno quando me lo chiedono?"
│
└── di PIANO      : capacità di modificare anche sensibilmente
                    le sequenze del piano di produzione
                    "posso rimescolare l'ordine in corsa?"
```

### Versatilità (sottoinsieme tecnico della flessibilità)

> **Versatilità:** caratteristica riferita **unicamente a macchinari e impianti**. È condizione **necessaria ma non sufficiente** per garantire la flessibilità.

```
Versatilità (solo macchinari)
├── Riconfigurabilità : ampiezza della gamma realizzabile
│                       + costi/tempi di set up
│                       + extra-scarti al riavvio (controllo di processo)
│
└── Convertibilità    : difficoltà di messa a punto della fase
                        di industrializzazione di un nuovo prodotto
```

---

## §4 Come funziona

**Il cuore:** la flessibilità è **produttività in condizioni di transitorio**. Quando il sistema deve cambiare qualcosa, c'è sempre un "prezzo" da pagare — in tempo e in denaro. La flessibilità è la misura di _quanto_ questo prezzo è basso.

Come le parti si connettono:

- Ogni dimensione risponde a un **tipo diverso di cambiamento** richiesto dal mercato.
- Ogni dimensione ha **due metriche di misura**: il _tempo_ di risposta (legato alla prontezza, una prestazione di servizio) e il _costo_ della risposta (legato alla produttività, una prestazione di efficienza).
- La **versatilità** delle macchine alimenta — ma non determina — la flessibilità complessiva. Una macchina riconfigurabile in 10 minuti è inutile se ci vogliono 3 settimane per produrre la scheda tecnica del nuovo capo.
- Le altre componenti del sistema (manodopera polivalente, fornitori reattivi, sistema informativo integrato, procedure agili) sono quelle che trasformano la versatilità tecnica in flessibilità reale.

**Cosa accade se...**

- **...prendi le macchine più versatili del mondo ma il personale conosce solo una lavorazione?** Hai versatilità senza flessibilità. Le macchine possono fare tante cose, ma nessuno sa dire loro cosa fare.
- **...hai un job shop?** Massima flessibilità su tutte e quattro le dimensioni (macchine general-purpose, scorte disaccoppianti, possibilità di inserire nuovi prodotti e nuovi mix, elasticità tramite manodopera aggiuntiva). Paga questo con bassa efficienza, alta WIP, difficile programmabilità.
- **...hai un flow shop?** Quasi zero flessibilità (la linea è rigida, dedicata, vincolata in sequenza, ogni cambio richiede set-up importanti, ogni guasto blocca tutto). In cambio massima efficienza.
- **...il mercato ti chiede contemporaneamente alta flessibilità di prodotto e bassi costi unitari?** È il regno della [[Mass customization]] e del [[VRP - Variety Reduction Program]]: standardizzi internamente (parti fisse) e diversifichi all'esterno (parti variabili). Il [[Postponement]] è una leva chiave.
- **...la domanda è ciclica/stagionale?** Ti serve soprattutto **elasticità** (flessibilità di volume): leve tipiche sono turni aggiuntivi, terzisti, manodopera flessibile, sovradimensionamento delle risorse.

### Posizionamento rispetto alle altre prestazioni

La flessibilità non rientra puramente né nell'efficienza né nell'efficacia, ma le interseca entrambe:

- **Lato efficienza:** misura _con quale costo_ il sistema reagisce.
- **Lato efficacia/servizio:** misura _in quanto tempo_ il sistema reagisce.

È la prestazione "trasversale" che si attiva quando il sistema deve uscire dal regime stazionario.

---

## §5 Applicazione pratica (metodologia)

Come si analizza la flessibilità di un sistema produttivo, passo per passo.

**Step 1 — Identifica il tipo di cambiamento atteso** Mappa le sollecitazioni che il mercato porta al sistema: si tratta di varietà istantanea (mix), di nuovi codici (prodotto), di oscillazioni quantitative (volume), di urgenze di riprogrammazione (piano)? Spesso convivono, ma con pesi diversi.

**Step 2 — Per ogni dimensione, definisci le metriche** Per ognuna delle 4 dimensioni rilevanti:

- _Tempo di risposta:_ quanto ci mette il sistema a passare allo stato nuovo? (es. tempo di set-up tra prodotti, tempo di industrializzazione di un nuovo codice, tempo di scale-up di volume, tempo per ri-emettere il piano)
- _Costo di risposta:_ qual è il costo extra rispetto al regime stazionario? (set-up cost, costi tecnici dell'ingegnerizzazione, costo della capacità extra, costi di re-scheduling)

**Step 3 — Distingui versatilità (macchine) da flessibilità (sistema)** Per ogni dimensione: quanto del tempo/costo è dovuto ai macchinari, quanto invece a organizzazione, fornitori, know-how, IT? Questa diagnosi orienta le leve.

**Step 4 — Identifica le leve azionabili per ogni dimensione**

|Dimensione|Leve tipiche|
|---|---|
|Mix|Macchine general-purpose, set-up ridotti (SMED), GT/celle|
|Prodotto|Concurrent engineering, modularità, VRP, postponement|
|Volume|Sovradimensionamento, turni, terzisti, polivalenza manodopera|
|Piano|Sistemi informativi integrati, buffer interoperazionali, procedure agili|

**Step 5 — Scegli le priorità (non si può massimizzare tutto)** La flessibilità si paga in efficienza. Decidi _quali_ dimensioni di flessibilità sono davvero strategiche per il tuo contesto competitivo e accetta consapevolmente che le altre saranno limitate.

**Step 6 — Progetta interventi mirati** Non interventi generici "vogliamo più flessibilità", ma azioni specifiche su una dimensione: es. ridurre i set-up del 30%, oppure portare il time-to-market di un nuovo SKU da 90 a 30 giorni.

### Checklist per non sbagliare

- [ ] Ho distinto le **4 dimensioni**, non parlato di "flessibilità" in modo generico?
- [ ] Sto misurando per ciascuna sia il **tempo** sia il **costo** di risposta?
- [ ] Ho separato cosa dipende dai **macchinari (versatilità)** e cosa dal **sistema (flessibilità)**?
- [ ] Ho riconosciuto il **trade-off con l'efficienza**, anziché trattare la flessibilità come gratuita?
- [ ] Ho considerato che la flessibilità dipende anche da **fornitori e organizzazione**, non solo dall'interno della fabbrica?
- [ ] Le **leve** scelte sono coerenti con la dimensione che voglio migliorare?

---

## §6 Domanda tipo esame (orale/scritto)

> _"Il candidato definisca la flessibilità di un sistema produttivo, ne elenchi le dimensioni e ne discuta la differenza rispetto alla versatilità. Indichi inoltre come la flessibilità si misuri e in che relazione si ponga con le altre prestazioni aziendali (efficienza, efficacia/servizio, qualità)."_

### Traccia di risposta strutturata

**Apertura — definizione (1 minuto):** "La flessibilità è l'insieme delle risposte che un sistema aziendale nel suo complesso genera a fronte di variazioni del contesto: lancio di nuovi prodotti, evoluzione di specifiche, variazioni di volume, modifiche dei piani di consegna. È una prestazione _del sistema_, non solo della parte impiantistica."

**Le 4 dimensioni — con esempi:**

1. **Flessibilità di mix:** capacità di riassortire un'ampia gamma di prodotti a costi accettabili in un range definito. Esempio: un'azienda che alterna frequentemente la produzione di codici diversi su una stessa linea.
2. **Flessibilità di prodotto:** capacità di industrializzare un _nuovo_ codice con tempi e costi accettabili. Esempio: introdurre una nuova variante di un orologio.
3. **Flessibilità di volume (elasticità):** capacità di assorbire variazioni quantitative mantenendo l'efficienza. Esempio: rispondere alla stagionalità o a picchi/cadute di domanda.
4. **Flessibilità di piano:** capacità di modificare le sequenze del piano di produzione in corsa, per far fronte a imprevisti o urgenze.

**Distinzione tra flessibilità e versatilità:** "La versatilità è una _caratteristica unicamente dei macchinari e degli impianti_. È condizione **necessaria ma non sufficiente** per la flessibilità. Le sue due dimensioni sono:

- **Riconfigurabilità:** funzione dell'ampiezza della gamma realizzabile dalla macchina, dei costi e tempi di set-up, e degli extra-scarti al riavvio (rilevanti nei processi controllati);
- **Convertibilità:** funzione della difficoltà di messa a punto della fase di industrializzazione di un nuovo prodotto.

La flessibilità invece dipende anche da know-how, personale, strutture organizzative, procedure di programmazione e controllo."

**Misura della flessibilità:** Le metriche di flessibilità si riconducono a:

- **Metriche di servizio (prontezza):** il _tempo_ di risposta al cambiamento;
- **Metriche di produttività:** il _costo_ per ottenere il cambiamento (input/output in regime di transitorio).

**Posizionamento tra le prestazioni aziendali:** "La flessibilità è difficilmente classificabile a priori come misura di efficienza o di efficacia. Da un lato misura la produttività di utilizzo dei fattori in condizioni di transitorio (efficienza); dall'altro misura la tempestività di reazione dell'azienda (efficacia/servizio). Si pone quindi come prestazione _trasversale_, attivata ogni volta che il sistema deve uscire dal regime stazionario."

**Chiusura — trade-off:** "La flessibilità si paga sempre in qualcosa: tipicamente in efficienza. Un job shop è massimamente flessibile su tutte le dimensioni ma poco efficiente; un flow shop ha l'efficienza opposta. La scelta del sistema produttivo è un atto di posizionamento competitivo: quale flessibilità mi serve davvero, e quanta efficienza sono disposto a sacrificare per ottenerla."

---

## §7 Errori comuni

> [!warning] ❌ Errore 1 — Confondere flessibilità e versatilità **Cosa sbaglio:** usare i due termini come sinonimi, o dire "il sistema è flessibile perché ha macchine versatili". **Perché è sbagliato:** la versatilità riguarda **solo i macchinari**; la flessibilità riguarda il **sistema aziendale nel suo complesso**. La versatilità è necessaria ma non sufficiente: posso avere macchine riconfigurabili in 10 minuti e ciò nonostante essere lento e costoso a inserire un nuovo prodotto, perché il collo di bottiglia è altrove (industrializzazione, fornitori, IT). **Come evitarlo:** all'orale, quando ti chiedono di "definire la flessibilità", inizia _sempre_ citando "sistema aziendale nel suo complesso" e poi specifica che la versatilità è il sottoinsieme tecnico (di macchinari/impianti).

> [!warning] ❌ Errore 2 — Trattare la flessibilità come dimensione unica **Cosa sbaglio:** dire "questo sistema è più flessibile di quello" senza specificare _in che senso_. **Perché è sbagliato:** la flessibilità ha **4 dimensioni distinte** (mix, prodotto, volume, piano). Un sistema può essere altamente flessibile su una dimensione e rigido su un'altra. Un flow shop dedicato ha pessima flessibilità di mix e prodotto, ma può avere una buona elasticità di volume (basta aumentare i turni). Un job shop è alto su tutte ma penalizzato in efficienza. **Come evitarlo:** ogni volta che parli di flessibilità, specifica la dimensione. Memorizza l'elenco a 4 voci e collegalo al tipo di variazione che il mercato sta richiedendo.

> [!warning] ❌ Errore 3 — Ignorare il trade-off flessibilità ↔ efficienza **Cosa sbaglio:** parlare della flessibilità come di una qualità desiderabile in sé, "più ne ho meglio è". **Perché è sbagliato:** la flessibilità è **produttività in condizioni di transitorio**: ogni cambiamento ha un costo. Massimizzare la flessibilità su tutte le dimensioni significa accettare bassissima efficienza in regime stazionario. È il motivo per cui il job shop esiste _separato_ dal flow shop: sono due punti opposti del trade-off, e il [[Layout a celle|group technology]] è la via di mezzo. **Come evitarlo:** ricorda il trade-off ricorrente `flessibilità ↔ efficienza`. La scelta della configurazione produttiva è un atto di posizionamento, non un'ottimizzazione di una sola variabile.

---

## §8 Collegamenti

### Prerequisiti (devo sapere prima)

- [[Prestazioni dei sistemi di produzione]] — quadro generale in cui la flessibilità si inserisce
- [[Efficienza vs efficacia]] — la flessibilità si pone trasversalmente tra le due
- [[Livello di servizio]] — fornisce le metriche di tempo di risposta (prontezza)
- [[Produttività]] — fornisce le metriche di costo di risposta
- [[Contesto competitivo]] — perché la flessibilità è diventata centrale (riduzione time-to-market)

### Dipendenze (ciò che si appoggia su questa nota)

- [[Job Shop]] — caso di massima flessibilità su tutte le dimensioni
- [[Flow Shop]] — caso di minima flessibilità
- [[Layout a celle]] — compromesso flessibilità/efficienza
- [[Macchine general purpose vs specializzate]] — leva tecnica per la flessibilità di mix
- [[Polivalenza manodopera]] — leva organizzativa
- [[Mass customization]] — strategia di mercato basata su alta flessibilità di prodotto
- [[VRP - Variety Reduction Program]] — leva progettuale per ridurre il costo della flessibilità
- [[Postponement]] — leva di processo per la flessibilità di prodotto
- [[Concurrent Engineering]] — leva organizzativa per la flessibilità di prodotto

### Concetti correlati

- [[Set up e riattrezzaggi]] — incidono direttamente sulla flessibilità di mix
- [[Time to market]] — espressione di flessibilità di prodotto
- [[Elasticità produttiva]] — sinonimo di flessibilità di volume

---

## §9 Auto-verifica

1. **(Base)** Quali sono le 4 dimensioni della flessibilità di un sistema produttivo, e a quale tipo di variazione richiesta dal mercato risponde ciascuna?
2. **(Media)** Qual è la differenza tra flessibilità e versatilità, e perché la seconda è "necessaria ma non sufficiente" per la prima? Fai un esempio in cui c'è versatilità ma manca la flessibilità.
3. **(Profonda)** Perché la flessibilità è "difficilmente classificabile a priori come misura di efficienza o di efficacia"? Mostra come le sue metriche tocchino entrambe le dimensioni e spiega perché esiste un trade-off strutturale tra flessibilità ed efficienza, esemplificandolo con il confronto tra job shop e flow shop.

---

> [!note] Posizionamento nel sistema Questa nota fa parte del **Cap3 — Prestazioni dei sistemi di produzione**, nella sottosezione "misura delle prestazioni" insieme a [[Livello di servizio]] e [[Qualità di prodotto e qualità di servizio]]. La flessibilità è una delle prestazioni _esterne_ del sistema (percepibili indirettamente dal cliente), trasversale rispetto a efficienza ed efficacia, e si lega direttamente alle scelte di configurazione di Cap2 (job shop/cell/flow shop) e Cap6 (layout).