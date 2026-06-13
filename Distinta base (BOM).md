---
aliases:
  - "Concurrent engineering"
  - "Concurrent Engineering"
  - "Coefficiente di impiego"
  - "Coefficiente di scarto"
  - "Esplosione dei fabbisogni - MRP"
  - "DB di progetto - produzione - ordinazione"
  - "Lead time nella DB"
  - "Validità temporale nella DB"
  - "Codifica item"
  - "Archivi tecnici"
  - "Distinta base di ordinazione"
---
> **In 10 secondi:** elenco gerarchico-strutturale degli item che compongono un prodotto, con coefficienti che dicono _quanti pezzi figli servono per un padre_ — è la ricetta numerica che permette di calcolare quanti materiali ordinare, quanti semilavorati produrre, quando e in che ordine.

---

## §1 Domanda fondamentale

**Come faccio a sapere, in modo automatico e tracciabile, quante materie prime devo comprare e quanti sottoassiemi devo produrre per realizzare un prodotto finito complesso — tenendo conto degli sfridi e dei tempi di assemblaggio?**

In altre parole: dato che voglio costruire X unità di prodotto finito, qual è la lista esatta di tutto quello che mi serve a ogni livello della struttura?

---

## §2 Il problema concreto

Immagina **Pegasus Mobili**, produttore italiano di **librerie modulari componibili**. Catalogo: 30 modelli, ognuno con varianti di colore e finitura. Mese tipo: 1.200 librerie totali, di cui 100 del modello "Tellus" (best-seller).

Una singola libreria Tellus contiene:

- 2 montanti laterali (pannelli MDF verticali)
- 5 ripiani regolabili (pannelli MDF orizzontali)
- 1 schienale (pannello MDF sottile)
- 32 viti M5
- 20 tasselli di sostegno
- 4 piedini antiscivolo
- 1 fascetta cablaggio per LED opzionali

Ma ogni montante è a sua volta ricavato da un **pannello grezzo MDF di formato standard 244×122 cm**, tagliato — con uno **sfrido del 5%**. Lo stesso vale per ripiani e schienali, con materiali diversi e sfridi diversi. Le viti arrivano in confezioni da 200. I tasselli da 500.

**Il dilemma operativo:**

- Magazzino lamenta che spesso mancano i pannelli quando servono → produzione si ferma.
- Ufficio acquisti lamenta che spesso compra troppo e il pannello resta fermo per mesi → capitale immobilizzato.
- Ufficio tecnico ha modificato il modello Tellus tre volte in due anni (cambio cerniere, nuova versione schienale) → magazzino ha ancora pezzi vecchi che non sa se usare.
- Quando un componente cambia (es. nuova versione del tassello), non è chiaro su quali altri prodotti del catalogo abbia impatto.

Servirebbe un **documento strutturato** che risponda automaticamente a queste domande. Quel documento è la distinta base.

---

## §3 La definizione

> **Distinta base (Bill of Materials, BOM):** elenco organizzato di tutti gli item che compongono un prodotto finito, strutturato secondo una gerarchia ad albero rovesciato che riflette la struttura fisica del prodotto. Per ogni legame padre→figlio sono specificati il coefficiente di impiego, il coefficiente di scarto, la validità temporale e il lead time.

### Scomposizione in parti

**1. Struttura gerarchica per livelli**

```
Livello 0  : Prodotto Finito (PF)         — la radice
Livello 1  : assiemi/sottoassiemi diretti
Livello n+1: item necessari per realizzare gli item di livello n
Livello max: materie prime e parti acquistate
```

Ogni item ha un **codice identificativo univoco** + eventuale **simbologia** che ne specifica la natura (assieme, sottoassieme, componente, materia prima).

⚠️ Il **numero di livelli non è fisso**: è quello "ritenuto significativo dalla singola azienda e congruente con il proprio processo produttivo" — la profondità della DB è una scelta di modellazione, non una proprietà fisica del prodotto.

**2. Tre rappresentazioni equivalenti**

```
DB a livelli    : albero rovesciato, grafica
DB scalare      : tabella, una riga per nodo; il livello è reso con
                  l'indentatura (convenzione a punti: B → .J → ..a)
DB riepilogata  : tabella con le quantità TOTALI di impiego per item
                  → sacrifica l'informazione strutturale a vantaggio
                  di una visione complessiva (stima fabbisogni)
```

Esempio del PDF (Figura 3): nella scalare la parte `a` compare in più rami con coefficienti diversi; nella riepilogata appare una sola volta con la quantità aggregata (40). È esattamente l'operazione di "aggrega" dello Step 4 in §5.

**3. Informazioni di legame** (i 4 attributi del legame padre→figlio)

```
- coefficiente di impiego : quantità del figlio per UNA unità di padre [netto]
- coefficiente di scarto  : % extra-consumo, di due nature:
                            · scarto di PROCESSO (dovuto al montaggio su
                              uno specifico padre)
                            · sfridi TECNOLOGICI non eliminabili — il caso
                              più frequente (taglio di bobine di carta, lamiere)
- validità temporale      : intervallo di date in cui il legame è valido
                            → tracciabilità + gestione "ad esaurimento"
- lead time               : correzione temporale del fabbisogno
                            → allinea fabbisogno al ciclo di assemblaggio
```

**Perché il coefficiente di impiego va tenuto al netto** (doppia motivazione del PDF): (a) facilita la gestione *contabile* dell'extra-consumo, separato dal fabbisogno netto; (b) permette di intervenire *direttamente sul dato sfrido* quando innovazioni tecnologiche o interventi organizzativi migliorano la resa del processo.

**Doppia utilità della validità temporale**: (a) traccia storica delle modifiche → gestione ricambi e tracciabilità (dalla data di produzione dell'assieme risalgo al componente effettivamente montato); (b) politiche "ad esaurimento": le proposte d'ordine del componente vecchio/nuovo sono elaborate in funzione della data prevista di esaurimento, memorizzata come data di validità del legame.

*Nota:* il PDF cita anche la **provenienza** tra le informazioni che caratterizzano i legami, senza però svilupparla (rimanda alla DB di ordinazione: make/buy, fornitori).

**4. Processi opposti**

```
ESPLOSIONE  : top-down. Dato il PF, scompongo nei suoi item
              → usi: stima fabbisogni · cataloghi delle versioni di prodotto
                · assistenza tecnica e predisposizione parti di RICAMBIO
IMPLOSIONE  : bottom-up. Dato un item, trovo gli impieghi DIRETTI e
              INDIRETTI su assiemi e PF di livello superiore
              → usi: valutare modifiche (effetti di eliminazione/sostituzione
                in termini di Δcosto e impatto sulla progettazione)
                · esaurimento scorte da mancata consegna → quali prodotti
                e quali COMMESSE risultano interessate
```

**5. Evoluzione durante l'ingegnerizzazione**

```
DB_progetto    → traduce specifiche cliente in requisiti tecnici
                 (vista del "cosa funziona idealmente")
DB_produzione  → DB_progetto adattata ai sistemi produttivi disponibili
                 (materiali, cicli, compatibilità con macchine reali)
DB_ordinazione → DB_produzione + info di approvvigionamento
                 (make/buy, costi standard, lotti minimi, anagrafica fornitori)

→ Con il concurrent engineering le tre tendono a convergere in un'unica DB:
  le scelte di progettazione sono fatte tenendo conto delle ricadute su
  produzione, acquisti e tutte le fasi del ciclo di vita del prodotto
```

**A cosa servono i dati della DB nei processi gestionali** (dal PDF): procedure di pianificazione e programmazione della produzione · gestione contabile del magazzino · gestione di fornitori e contoterzisti.

---

## §4 Come funziona

**Il cuore:** la distinta base è una **ricetta strutturata e quantitativa**. Non ti dice solo _cosa serve_, ma _quanto_ serve, _quando_ serve e _cosa succede se cambi un pezzo_.

Come le parti si connettono:

- La **gerarchia** dice quali item compongono quali altri item.
- I **coefficienti** dicono in che quantità.
- Il **lead time** dice quando il fabbisogno si manifesta lungo il ciclo di assemblaggio.
- La **validità** dice quale versione del legame è in vigore in una certa data.
- L'**esplosione** percorre l'albero dall'alto al basso moltiplicando coefficienti e tenendo conto degli scarti, restituendo la lista totale dei materiali necessari.
- L'**implosione** percorre l'albero dal basso all'alto.

**Cosa accade se...**

- **...il prodotto ha pochi livelli (≤ 1)?** Si parla di **prodotto semplice** e la BOM diventa una _ricetta_. Tipico delle produzioni per processo (cemento, acciaio, carta, alimentari).
- **...il prodotto ha decine di livelli?** È un **prodotto complesso**: la BOM ha grande _profondità_ (numero livelli) e _ampiezza_ (numero codici). La complessità qui è "di sistema" (coordinamento di tante fasi), non necessariamente "di processo".
- **...una scheda elettronica monta un nuovo componente con stesse interfacce ma ingombro diverso?** Non serve ricodificare tutto l'assieme: si chiude la **validità** del legame con il vecchio componente in una certa data e si apre quella del nuovo. La BOM mantiene la storia.
- **...il ciclo di assemblaggio non rispetta l'ordine strutturale della BOM?** È il caso tipico dei quadri elettrici: la scheda elettronica è "in fondo" alla struttura ma si monta per ultima per ragioni di cablaggio. Si risolve assegnando un **lead time** al legame, che sposta nel futuro il fabbisogno di quella scheda allineandolo al ciclo reale.
- **...un fornitore non consegna un componente?** Si fa **implosione** per identificare tutti i prodotti e tutte le commesse impattate.

---

## §5 Applicazione pratica (formule + procedura)

### Formula chiave: esplosione di un legame

Per ogni legame padre→figlio:

$$Q_{figlio} = Q_{padre} \cdot c_{impiego} \cdot (1 + c_{scarto})$$

dove:

- $Q_{padre}$ = quantità richiesta dell'item padre [pz]
- $c_{impiego}$ = quantità _netta_ di figlio per 1 unità di padre
- $c_{scarto}$ = percentuale extra-consumo (sfridi, scarti di processo)

Per un'**esplosione multi-livello** si applica la formula ricorsivamente, partendo dal livello 0 (PF) e scendendo fino alle MP.

### Procedura passo-passo per esplodere una BOM

**Step 1 — Stabilisci la quantità di PF da produrre** $$Q_0 = \text{quantità prodotto finito richiesta}$$

**Step 2 — Identifica i legami diretti (livello 0 → livello 1)** Per ogni item figlio $i$ al livello 1: $$Q_i^{(1)} = Q_0 \cdot c_{imp,i} \cdot (1 + c_{scarto,i})$$

**Step 3 — Scendi al livello successivo** Tratta ogni item del livello 1 come nuovo "padre" e ripeti la formula sui suoi figli. Itera fino alle materie prime.

**Step 4 — Aggrega** Se lo stesso item compare in più rami dell'albero, somma le quantità per ottenere il fabbisogno totale (è proprio il contenuto della **DB riepilogata**).

**Step 5 — Correggi temporalmente con il lead time** Per la pianificazione, sposta la data del fabbisogno di ciascun item di un $\Delta t = LT$ rispetto alla data di completamento del padre.

**Step 6 — Sottrai le giacenze (se calcoli il fabbisogno netto)** $$F_{netto} = F_{lordo} - \text{giacenza disponibile} - \text{ordini in arrivo}$$

### Checklist per non sbagliare

- [ ] Sto usando il coefficiente di impiego _netto_? (gli sfridi vanno solo in $c_{scarto}$)
- [ ] Ho considerato gli scarti a ogni livello, non solo all'ultimo?
- [ ] Se un item compare in più rami, ho aggregato le quantità?
- [ ] Sto usando la versione della BOM **valida nella data** di produzione?
- [ ] Ho applicato il lead time corretto a ogni livello?
- [ ] Sto distinguendo fabbisogno lordo (totale teorico) da fabbisogno netto (da approvvigionare)?
- [ ] La BOM in uso è quella di **produzione** (non di progetto)?

---

## §6 Esercizio tipo esame

> **Pegasus Mobili** deve produrre **100 librerie modello Tellus** per il mese di novembre. La distinta base (di produzione) è la seguente:
> 
> ```
> Libreria Tellus (PF) - liv. 0
> ├── Montante laterale [c_imp=2, c_scarto=0%]              - liv. 1
> │   └── Pannello MDF tipo M [c_imp=1, c_scarto=5%]         - liv. 2
> ├── Ripiano [c_imp=5, c_scarto=0%]                         - liv. 1
> │   └── Pannello MDF tipo R [c_imp=1, c_scarto=3%]         - liv. 2
> ├── Schienale [c_imp=1, c_scarto=0%]                       - liv. 1
> │   └── Pannello MDF tipo S [c_imp=1, c_scarto=2%]         - liv. 2
> ├── Vite M5 [c_imp=32, c_scarto=2%]                        - liv. 1
> └── Tassello [c_imp=20, c_scarto=4%]                       - liv. 1
> ```
> 
> Determinare:
> 
> 1. Il **fabbisogno lordo** di ogni materia prima (livello 2) e di viti/tasselli (livello 1).
> 2. Se in magazzino sono disponibili **20 pannelli MDF tipo M** e **400 viti M5**, calcolare il **fabbisogno netto** di questi due item.

### Soluzione passo-passo

**Step 1 — Quantità PF** $Q_0 = 100$ librerie.

**Step 2 — Esplosione livello 0 → livello 1**

|Item liv. 1|Calcolo|Quantità|
|---|---|---|
|Montante|$100 \cdot 2 \cdot (1+0) = 200$|**200 pz**|
|Ripiano|$100 \cdot 5 \cdot (1+0) = 500$|**500 pz**|
|Schienale|$100 \cdot 1 \cdot (1+0) = 100$|**100 pz**|
|Vite M5|$100 \cdot 32 \cdot (1+0{,}02) = 3.264$|**3.264 pz**|
|Tassello|$100 \cdot 20 \cdot (1+0{,}04) = 2.080$|**2.080 pz**|

**Step 3 — Esplosione livello 1 → livello 2** (solo MP a livello 2)

|MP liv. 2|Calcolo|Fabbisogno lordo|
|---|---|---|
|Pannello MDF tipo M|$200 \cdot 1 \cdot (1+0{,}05) = 210$|**210 pannelli**|
|Pannello MDF tipo R|$500 \cdot 1 \cdot (1+0{,}03) = 515$|**515 pannelli**|
|Pannello MDF tipo S|$100 \cdot 1 \cdot (1+0{,}02) = 102$|**102 pannelli**|

**Step 4 — Fabbisogni netti**

- Pannelli MDF tipo M: $F_{netto} = 210 - 20 = \mathbf{190 \text{ pannelli da approvvigionare}}$
- Viti M5: $F_{netto} = 3.264 - 400 = \mathbf{2.864 \text{ viti da approvvigionare}}$

**Risposta finale:** Pegasus deve ordinare 190 pannelli M, 515 pannelli R, 102 pannelli S, 2.864 viti M5, 2.080 tasselli.

### Variante d'esame ("e se cambiasse X?")

> _E se il fornitore di pannelli M migliorasse la lavorazione, riducendo il coefficiente di scarto dal 5% al 2%?_

Ricalcolo solo quel ramo: $$F_{lordo,M} = 200 \cdot 1 \cdot (1+0{,}02) = 204 \text{ pannelli}$$ $$F_{netto,M} = 204 - 20 = \mathbf{184 \text{ pannelli}}$$

Risparmio: 6 pannelli per ciclo da 100 librerie → **72 pannelli/anno** se la produzione è costante a 1.200 librerie/anno.

> _E se le librerie da produrre raddoppiassero a 200?_

Tutti i fabbisogni raddoppiano in modo proporzionale (la formula è lineare in $Q_0$). Esempio: pannelli M passano da 210 a 420 lordi.

---

## §7 Errori comuni

> [!warning] ❌ Errore 1 — Confondere coefficiente d'impiego e coefficiente di scarto
> **Cosa sbaglio:** sommare i due coefficienti, o moltiplicare l'impiego per lo scarto come se fossero la stessa categoria.
> **Perché è sbagliato:** sono **due informazioni distinte**. Il $c_{impiego}$ dice _quanti pezzi netti servono_; il $c_{scarto}$ è il _moltiplicatore correttivo_ (1+%) che tiene conto del materiale buttato. Il libro raccomanda esplicitamente di mantenere il $c_{impiego}$ al netto degli sfridi: facilita la gestione contabile dell'extra-consumo e permette di intervenire direttamente sul dato sfrido quando il processo migliora.
> **Come evitarlo:** ricorda la formula scomposta: $Q_{figlio} = Q_{padre} \cdot c_{imp} \cdot (1 + c_{scarto})$. Tre fattori distinti, ognuno con un significato preciso.

> [!warning] ❌ Errore 2 — Trattare la BOM come oggetto statico
> **Cosa sbaglio:** parlare di "_la_ distinta base" come se fosse un documento unico, immutabile, identico tra progettazione e produzione.
> **Perché è sbagliato:** la BOM ha (a) un'**evoluzione** lungo l'ingegnerizzazione (progetto → produzione → ordinazione, ognuna con informazioni aggiuntive), e (b) una **storia temporale** governata dalla validità dei legami. Lo stesso prodotto può avere versioni diverse di BOM in tempi diversi. La BOM di progetto può essere tecnicamente perfetta ma non realizzabile con le macchine disponibili — per questo viene poi adattata in BOM di produzione.
> **Come evitarlo:** all'orale, quando ti chiedono "cos'è la distinta base", parti sempre citando le tre fasi evolutive e l'attributo di validità. Mostra che sai che è un oggetto vivo nel tempo.

> [!warning] ❌ Errore 3 — Dimenticare il lead time (la "trappola del cablaggio")
> **Cosa sbaglio:** assumere che l'ordine di approvvigionamento dei figli sia sempre coerente con l'ordine strutturale della BOM (più "in basso" nella struttura = prima da comprare).
> **Perché è sbagliato:** è il classico caso del quadro elettrico (schede montate in cassetti o rack). La scheda elettronica strutturalmente è "in fondo" (livello alto), e _sembrerebbe_ il primo componente da approvvigionare. Ma il ciclo di assemblaggio reale la monta **per ultima** per facilitare il cablaggio senza interferire con i componenti già montati. Se ordini la scheda in anticipo, occupa magazzino inutilmente; se la pianifichi senza correzione, hai un'incongruenza tra struttura BOM e ciclo reale.
> **Come evitarlo:** ricorda che il **lead time** sul legame è proprio il termine correttivo che sposta nel futuro il fabbisogno di un item per allinearlo al ciclo di assemblaggio. La BOM resta gerarchica e "strutturale", ma il lead time risolve il disallineamento temporale.

---

## §8 Collegamenti

### Prerequisiti (devo sapere prima)

- Archivi tecnici (§4.2.1) — la BOM è uno dei due pilastri (insieme al ciclo di lavorazione); rispondono all'esigenza di *formalizzare* processi e prodotti: miglioramento del processo, formazione delle risorse umane, predisposizione dei materiali
- [[Ingegnerizzazione]] — il processo che fa evolvere la BOM nelle sue tre forme
- [[Classificazione dei prodotti|Prodotti semplici vs complessi]] — la profondità della BOM definisce la complessità gestionale

### Dipendenze (ciò che si appoggia su questa nota)

- [[Ciclo di lavorazione]] — affianca la BOM, descrive _come_ si trasforma ciò che la BOM elenca (la BOM non dice nulla sulle operazioni)
- Esplosione dei fabbisogni (MRP) — applicazione operativa della formula vista in §5
- [[Make or buy]] — decisione che si annota nella BOM di ordinazione
- [[Bilancio di massa]] — il diagramma quantitativo usa i dati di BOM
- [[Numero di risorse|Coefficiente di scarto K1]] (cfr. anche [[OEE]]) — la cascata degli scarti del §5.2 è la stessa logica del $c_{scarto}$, vista lato dimensionamento

### Concetti correlati

- Tracciabilità del prodotto — la validità dei legami è alla base
- Gestione ricambi e assistenza — usa esplosione di BOM storiche
- [[Lead time]] — concetto chiave in più contesti, qui in versione "termine correttivo del legame"

---

## §9 Auto-verifica

1. **(Base)** Quali sono le tre rappresentazioni della distinta base, e in cosa si differenziano in termini di informazioni mostrate?
2. **(Media)** Spiega la differenza tra coefficiente d'impiego e coefficiente di scarto. Perché è importante mantenerli separati anche dal punto di vista organizzativo?
3. **(Profonda)** Cosa significa che la BOM evolve durante l'ingegnerizzazione? Descrivi le tre fasi e spiega perché, in regime di concurrent engineering, queste tendono a convergere in una sola BOM. Cosa cambia, da un punto di vista organizzativo, in questa convergenza?

---

> [!note] Posizionamento nel sistema
> Questa nota fa parte degli **archivi tecnici** (§4.2.1), insieme a [[Ciclo di lavorazione]] e [[Foglio di lavorazione]]. La BOM è il documento "statico-strutturale" del prodotto; il ciclo è il documento "dinamico-procedurale" del processo. Insieme descrivono il sistema produttivo dal punto di vista informativo, e alimentano la pianificazione (Cap1) e il dimensionamento dei magazzini (Cap6).