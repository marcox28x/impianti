
**In 10 secondi:** Si classificano i sistemi produttivi guardando se il prodotto finito è _reversibile_ (smontabile nei suoi componenti) o no — questa singola proprietà fisica detta a cascata ciclo, flusso, layout e gestione.

---

## §1 Domanda fondamentale

> Dato un prodotto qualsiasi, qual è la proprietà _intrinseca_ che mi dice subito che tipo di impianto serve per realizzarlo — un'unica grande macchina a ciclo obbligato oppure una costellazione di stazioni flessibili?

La risposta sta in una domanda semplicissima: **il prodotto finito si può scomporre a ritroso?** Tutto il resto (continuità del flusso, vincolo del ciclo, layout, livello di WIP, gestione della manodopera) discende da qui.

---

## §2 Il problema concreto

**Rouge Atelier S.r.l.**, azienda cosmetica di Milano, sta progettando un nuovo stabilimento a Lodi per la propria linea di rossetti di lusso. Il direttore tecnico, Marta, si trova davanti due reparti che si chiama "produzione" ma che, all'occhio dell'ingegnere impiantistico, sembrano due mondi diversi:

- **Reparto A — formulazione bulk.** Il rossetto vero e proprio nasce qui: in un _turbomixer_ da 200 kg si fondono cere d'api, oli vegetali, pigmenti micronizzati e fragranze a 85 °C. Dopo la mescolatura, l'impasto cola in stampi cilindrici raffreddati. **Tempo ciclo: 6 ore continuative**, durante le quali l'impianto non si può fermare senza compromettere la stabilità della formula. Output: **800 kg/giorno** di stick.
- **Reparto B — assemblaggio astuccio.** Lo stick raffreddato viene inserito in un meccanismo a vite (lavorato per stampaggio plastico), incassato in un astuccio metallico dorato (lavorato per imbutitura), chiuso con tappo e siglato con etichetta. **Tempo ciclo per pezzo: 12 secondi**. Output: **15.000 pezzi/giorno**.

Marta deve scegliere il layout, la disposizione, la cadenza, il numero di operatori. Ma il consulente le dice: _"Stai progettando un solo impianto? No. Stai progettando due impianti che si scambiano semilavorati."_

**Il dilemma:** Marta non può applicare la stessa logica progettuale ai due reparti. Il reparto A è una _produzione di processo_ (la formula non si "smonta" in cere, oli e pigmenti), il reparto B è una _produzione di parti_ (se cade a terra, il rossetto si apre nei suoi componenti originari). Da questa distinzione discende ogni scelta progettuale successiva: tipo di ciclo, layout, flusso, modalità di gestione. Capire quale fosse quale era il primo passo, e solo i fondamentali della classificazione tecnologica glielo permettevano.

---

## §3 La definizione

**Classificazione per processi tecnologici** ≔ schema di classificazione dei sistemi di produzione che usa come **variabile discriminante la reversibilità del processo produttivo** (cioè la possibilità di scomporre a ritroso il prodotto finito nei componenti originari distinguibili).

Genera due macro-classi:

### Produzione di processo (o "a ciclo tecnologico obbligato")

Produzione **irreversibile**: il prodotto finito _"non può essere scomposto a ritroso"_, perché i componenti originari non sono più distinguibili o hanno cambiato natura.

- **Esempi canonici:** acciaio, carta, cemento, prodotti chimici, filati, prodotti farmaceutici (compresse, sciroppi), vetro, plastiche.
- **Variabile discriminante interna:** la tecnologia (processi chimici, siderurgici, ecc.).

### Produzione di parti (o manifatturiera)

Produzione **reversibile**: il prodotto può essere montato e smontato. _(Eccezione formale: l'assemblaggio per saldatura, forzatura o cucitura non rompe la classificazione — resta produzione di parti anche se in pratica non si può smontare.)_

- **Esempi canonici:** automobili, elettrodomestici, apparecchiature elettroniche, scarpe, giocattoli, mobili.
- **Si scompone sempre in due fasi:**
    - **Fabbricazione** = lavorazioni che modificano forma, dimensioni o stato superficiale di parti singole (è la quota _irreversibile_ dentro un sistema reversibile)
    - **Montaggio** = giustapposizione di parti singole per formare un assieme

---

## §4 Come funziona

**Il cuore in una frase:** la reversibilità è una proprietà fisica del prodotto, ma agisce come **DNA progettuale dell'impianto** — una sola informazione (reversibile/irreversibile) detta a cascata sei o sette decisioni impiantistiche.

**La cascata di conseguenze**

```
reversibilità del prodotto
        │
        ├─► tipo di ciclo tecnologico
        │       processo  → ciclo OBBLIGATO (sequenza unica, vincolante)
        │       parti     → ciclo NON OBBLIGATO (molte varianti possibili)
        │
        ├─► natura del flusso produttivo
        │       processo  → CONTINUO (materiale fluisce, stati conversione/trasporto indistinguibili)
        │       parti     → INTERMITTENTE (carichi/scarichi delle macchine, impianto improduttivo durante)
        │
        ├─► caratterizzazione dell'impianto
        │       processo  → "un'unica grande macchina", progettata sulle peculiarità tecnologiche
        │       parti     → "costellazione di macchine" eterogenee, ognuna con cicli alternativi
        │
        ├─► fermate
        │       processo  → previste solo per manutenzione/ripristino
        │       parti     → strutturali (cambi prodotto, setup, attese)
        │
        └─► flessibilità
                processo  → bassa (impianto monoprodotto tendenziale)
                parti     → alta (mix produttivo, cicli alternativi)
```

**Cosa accade se... (casi limite e varianti)**

- **Saldatura, cucitura, forzatura.** Un'auto saldata o una scarpa cucita non si smontano in pratica. _La classificazione non cambia_: restano produzioni di parti. Il discrimine è la natura _concettuale_ della reversibilità, non la fattibilità materiale.
- **Prodotti ibridi (cosmetica, farmaceutico, elettronica).** Quasi sempre coesistono nello stesso stabilimento un tratto di processo (formulazione bulk, fabbricazione PCB nudo, sintesi principio attivo) e un tratto di parti (assemblaggio astuccio, montaggio componenti SMT, blistering). Vanno classificati e progettati **separatamente** come due sotto-impianti.
- **Ciclo obbligato ma non continuo.** Esiste: una produzione farmaceutica a lotti (granulazione → compressione → rivestimento) ha ciclo obbligato ma opera _a batch_, non in continua. La corrispondenza "obbligato ↔ continuo" è tipica del _monoprodotto_; per multiprodotto può rompersi.
- **Ciclo non obbligato che di fatto è obbligato.** Per alcuni prodotti manifatturieri esiste in pratica un'unica sequenza sensata (es. assemblaggio auto). Resta classificazione "di parti": è la _possibilità teorica_ di varianti che conta.

---

## §5 Applicazione pratica

### Metodologia operativa step-by-step

Dato un sistema produttivo da analizzare:

1. **Identifica il prodotto finito.** Non i semilavorati, non gli input: il prodotto che esce dallo stabilimento.
2. **Applica il test di reversibilità.** Chiediti letteralmente: _"Posso smontarlo nei componenti originari, e questi componenti sono ancora distinguibili e identificabili?"_
3. **Decidi la macro-classe.**
    - **NO → produzione di processo.** Vai allo step 4a.
    - **SÌ → produzione di parti.** Vai allo step 4b.
4. **Caratterizza la sotto-classe.**
    - **4a (processo):** identifica la tecnologia dominante (chimica, siderurgica, farmaceutica, alimentare-trasformativa…). Aspettati ciclo obbligato, flusso continuo, impianto monoprodotto, fermate solo per manutenzione.
    - **4b (parti):** scomponi il processo in **fabbricazione** + **montaggio**. Aspettati ciclo non obbligato, flusso intermittente, mix produttivo, layout per reparti o per famiglie.
5. **Verifica l'ibridazione.** Se l'azienda fa entrambe le cose (è frequentissimo), classifica **ogni segmento separatamente** e progetta come due sotto-sistemi che si scambiano semilavorati attraverso un magazzino di disaccoppiamento.
6. **Deriva le implicazioni a cascata** (vedi §4): da macro-classe → ciclo → flusso → layout target → modalità di gestione.

### Checklist anti-errore

- [ ] Ho guardato il **prodotto finito**, non un semilavorato
- [ ] Ho considerato la reversibilità **concettuale**, non quella pratica (la saldatura non conta)
- [ ] Se è ibrido, ho **segmentato** i due tratti invece di forzarli in un'unica categoria
- [ ] Non sto confondendo "produzione di processo" con "produzione continua" — sono concetti distinti (vedi §7)
- [ ] Non sto confondendo "produzione di parti" con "produzione discreta a lotti" — può essere anche di massa
- [ ] Per la produzione di parti, ho identificato **separatamente** la fase di fabbricazione e quella di montaggio

---

## §6 Domanda tipo esame

> **Traccia (orale/scritto).** Si illustri la classificazione dei sistemi di produzione in base ai processi tecnologici. In particolare, si discuta il criterio discriminante adottato, si descrivano le due macro-classi che ne derivano, si motivi la corrispondenza con il concetto di "ciclo tecnologico obbligato" e si forniscano esempi concreti che evidenzino le implicazioni impiantistiche.

### Traccia di risposta strutturata (5 punti, in ordine)

**1. Premessa — perché classificare.** Esordire chiarendo che non esiste un sistema di gestione della produzione universale: ogni tipologia richiede approcci progettuali e gestionali diversi. La classificazione per processi tecnologici è il primo strumento per orientare le scelte impiantistiche.

**2. Criterio discriminante — la reversibilità.** Enunciare il criterio chiave: _un prodotto è scomponibile a ritroso nei suoi componenti originari distinguibili?_ Da questa singola proprietà fisica discendono tutte le altre. Specificare l'eccezione formale: saldatura, forzatura, cucitura non rompono la classificazione (restano "di parti").

**3. Le due macro-classi.**

- **Produzioni di processo (irreversibili):** elencare esempi tipici (acciaio, carta, cemento, chimico, filati, farmaceutico). Sottolineare: componenti originari non più distinguibili o cambiano natura.
- **Produzioni di parti / manifatturiere (reversibili):** elencare esempi (auto, elettrodomestici, elettronica, scarpe). Sottolineare la decomposizione in **fabbricazione** (lavorazioni che modificano forma/dimensioni/stato di parti singole, è la quota irreversibile _interna_) e **montaggio** (giustapposizione per formare un assieme).

**4. Corrispondenza con il ciclo tecnologico e con il flusso.** Spiegare:

- produzione di processo ↔ ciclo _obbligato_ ↔ flusso tipicamente _continuo_: l'impianto è progettato sulle peculiarità tecnologiche del prodotto (T, p, atmosfere), la sequenza è predefinita, gli stati di conversione e di trasporto sono pressoché indistinguibili, le fermate sono solo per manutenzione.
- produzione di parti ↔ ciclo _non obbligato_ ↔ flusso _intermittente o a lotti_: macchine eterogenee con cicli alternativi, carichi/scarichi che rendono l'impianto improduttivo, dimensioni dei lotti variabili fase per fase.

**5. Implicazioni progettuali (chiusura).** Concludere mostrando come la classificazione _orienta_ — non determina, ma orienta — la scelta di layout (per processo vs per prodotto), di gestione (MTS vs MTO), di manodopera (parcellizzata vs ricomposta), di scorte (WIP basso continuo vs WIP alto intermittente). Se possibile, citare un caso ibrido (cosmetica, farmaceutica, elettronica) per mostrare che molte aziende reali sono _somma_ di sotto-impianti di tipologie diverse, e questa è essa stessa una scelta progettuale.

---

## §7 Errori comuni

> [!warning]+ ❌ Confondere "produzione di processo" con "produzione continua" **Errore:** dire che una farmaceutica a lotti (batch) non è "di processo" perché non è continua. **Perché succede:** il libro spesso accoppia i due concetti perché la corrispondenza è frequente. **Come evitarlo:** sono due classificazioni _diverse_. "Processo vs parti" guarda la **reversibilità del prodotto**; "continua vs discreta" guarda la **modalità temporale di produzione**. Una compressa farmaceutica è prodotta di processo _e_ a lotti. Acciaio in colata continua è di processo _e_ continuo. Sono assi indipendenti.

> [!warning]+ ❌ Considerare la saldatura come confine tra processo e parti **Errore:** classificare un'auto saldata, o due lamiere unite per forzatura, come "produzione di processo" perché non si smontano. **Perché succede:** si applica il test di reversibilità in modo letterale e pratico, anziché concettuale. **Come evitarlo:** la definizione del libro dice esplicitamente che saldatura, forzatura, cucitura non rompono la classificazione. Resta produzione di parti. Il criterio è _concettuale_: i componenti originari erano distinguibili al momento dell'unione? Se sì, è di parti.

> [!warning]+ ❌ Forzare un'azienda ibrida in una sola categoria **Errore:** classificare l'intera Rouge Atelier come "produzione di parti" (perché il prodotto finito è un astuccio assemblato) ignorando il bulk a monte. **Perché succede:** si guarda solo il prodotto-uscita-stabilimento. **Come evitarlo:** segmentare il processo. Quasi tutta la cosmetica, la farmaceutica e l'elettronica sono **ibridi processo+parti**, e progettare richiede di trattarli come due sotto-impianti distinti collegati da un magazzino di disaccoppiamento.

---

## §8 Collegamenti

**Prerequisiti** (da padroneggiare _prima_)

- [[Sistema di produzione]] — cos'è un sistema produttivo e quali sono i suoi confini
- [[Classificazione dei prodotti]] — prodotti semplici vs complessi: la base che apre la classificazione tecnologica
- [[Processo produttivo]] — successione di operazioni, trasporti, controlli, attese, immagazzinamenti
- [[Ciclo tecnologico]] — definizione di sequenza ordinata di operazioni

**Conseguenze** (cosa abilita)

- [[Ciclo obbligato vs non obbligato]] — discende direttamente da questa classificazione
- [[Soluzioni impiantistiche — Job shop, Group Technology, Flow shop]] — il layout target dipende dalla macro-classe
- [[Layout per processo vs per prodotto]] — la scelta tipica si appoggia su questo schema
- [[Classificazione per volumi — discreta e continua]] — asse indipendente ma fortemente correlato
- [[Matrice Prodotto-Processo]] — sintesi finale che incrocia tutte le classificazioni del Cap2
- [[CODP e modalità di risposta al mercato]] — MTS/MTO/ATO/ETO trovano congruenze tipiche con le macro-classi (es. processo+continua+MTS)

---

## §9 Auto-verifica

1. **(base)** In una frase: qual è la variabile discriminante della classificazione per processi tecnologici, e quali sono le due macro-classi che genera?
2. **(intermedia)** Una linea di produzione di **scarpe sportive** comprende: stampaggio della suola in gomma, taglio della tomaia in tessuto tecnico, cucitura suola+tomaia, applicazione di lacci. È produzione di processo o di parti? Giustifica usando il test di reversibilità e identifica le sotto-fasi.
3. **(profonda)** Perché la corrispondenza "produzione di processo ↔ ciclo obbligato ↔ flusso continuo" è particolarmente forte nelle produzioni _monoprodotto_, e cosa la indebolisce nelle produzioni a più prodotti? Costruisci un controesempio plausibile in cui si rompe.