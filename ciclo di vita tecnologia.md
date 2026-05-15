
# Ciclo di vita di un processo produttivo o di una tecnologia

> [!info]+ Classificazione **QUALITATIVO** — framework descrittivo a fasi, nessuna formula. La struttura segue la logica metodologia operativa + domanda aperta.

> [!tldr] In 10 secondi Ogni impianto/tecnologia attraversa **4 fasi** (concepimento → avviamento → regime → chiusura/riconfigurazione), in analogia al ciclo di vita del prodotto. Serve a sapere **quando** investire, ammodernare, riconfigurare o dismettere — prima di subire l'obsolescenza.

## §1 Domanda fondamentale

Quando devo investire in un nuovo impianto, quando ammodernarlo, e quando dichiararlo finito? E come faccio a capirlo **prima** che il mercato me lo dica con numeri rossi?

## §2 Il problema concreto

**Scenario.** Pensiamo a un grande produttore coreano di pannelli per televisori. Nel 2010 investe circa 5 miliardi di dollari per costruire una fab LCD di ultima generazione, dimensionata per ~24 milioni di pannelli/anno, con piano di ammortamento a 10 anni. La linea va a regime, satura, fa utili.

Nel 2017 entra prepotentemente l'OLED: rese cromatiche superiori, contrasto infinito, prezzi che iniziano a essere competitivi nel segmento premium. Nel 2019 i prezzi medi degli LCD sono crollati di circa il 30% e l'azienda annuncia una conversione parziale della fab a OLED, con un costo aggiuntivo di alcuni miliardi e mesi di down-time.

**Il dilemma.** La fab LCD nel 2015 stava ancora producendo a pieno regime, con margini positivi. Quando esattamente avrebbe dovuto l'azienda iniziare a pensare alla chiusura/riconfigurazione?

- Se aspetti i numeri rossi → è già tardi, la riconversione richiede 18+ mesi, i concorrenti sono già a regime sulla nuova tecnologia.
- Se spingi sull'OLED nel 2013 quando è ancora immaturo → bruci cash su una scommessa non necessariamente vincente.

→ il ciclo di vita ti dà un framework per **diagnosticare in che fase ti trovi** e quindi **quale decisione è coerente** con quella fase.

## §3 La definizione

> [!definition] Ciclo di vita di un processo/tecnologia Sequenza di **4 fasi** che descrive la vita di un sistema produttivo (o di una tecnologia di prodotto/processo) dalla sua ideazione fino alla dismissione o riconversione.

**Le quattro fasi:**

1. **Concepimento e progettazione** — dall'idea al collaudo
2. **Avviamento** — messa in marcia e calibrazione contro il progetto
3. **Regime** — esercizio normale, feedback dal mercato, monitoraggio tecnologico
4. **Chiusura o riconfigurazione** — riconoscimento dell'obsolescenza e decisione sul futuro

> [!info] Doppia analogia (importante per l'orale)
> 
> 1. È **analogo al ciclo di vita del prodotto** (sviluppo → introduzione → crescita → maturità → declino), ma applicato all'**impianto** invece che al prodotto.
> 2. L'**evoluzione tecnologica** segue la stessa curva ad S: prima affermazione lenta → rapida diffusione → maturità → obsolescenza, con tecnologie sostitutive (B sostituisce A, C sostituisce B...) — Figura 6 del testo.

## §4 Come funziona

**Cuore del concetto.** Ogni fase richiede decisioni diverse: non si gestisce una fab in regime come una in avviamento, e non si decide su un impianto vicino alla chiusura come uno appena progettato. La fase determina **cosa è coerente fare**.

**Diagramma logico (flusso a fasi con loop di feedback):**

```
  ┌─────────────────────────────────────────────────────┐
  │  CONCEPIMENTO E PROGETTAZIONE                       │
  │  fattibilità → finanziamento → prog. massima        │
  │  → prog. esecutiva → acquisizione risorse           │
  │  → realizzazione e collaudo                         │
  └────────────────────────┬────────────────────────────┘
                           ▼
  ┌─────────────────────────────────────────────────────┐
  │  AVVIAMENTO                                         │
  │  messa in esercizio → raccolta dati                 │
  │  → analisi comparativa vs progetto                  │
  │  ─── (gap troppo grande) ──► riprogettazione mirata │
  └────────────────────────┬────────────────────────────┘
                           ▼
  ┌─────────────────────────────────────────────────────┐
  │  REGIME                       ◄────────┐            │
  │  feedback mercato                      │ loop       │
  │  → ricerca nuove tecnologie            │ continuo   │
  │  → analisi convenienza rinnovo ────────┘            │
  └────────────────────────┬────────────────────────────┘
                           ▼  (obsolescenza identificata)
  ┌─────────────────────────────────────────────────────┐
  │  CHIUSURA O RICONFIGURAZIONE                        │
  │  verifica obsolescenza                              │
  │  → analisi alternative                              │
  │     ├─► riconfigurazione totale ──► nuovo ciclo     │
  │     └─► dismissione definitiva                      │
  └─────────────────────────────────────────────────────┘
```

**Cosa accade se...**

- _...non chiudi correttamente l'avviamento_: l'impianto va a regime con problemi non diagnosticati → bassa OEE cronica, scarti che vengono interpretati come "intrinseci al processo" quando in realtà sono solo non corretti in fase di calibrazione.
- _...tratti il regime come fase passiva_: arrivi alla chiusura senza esserti preparato → la tecnologia sostitutiva non l'hai studiata in anticipo, e quando ti serve devi partire da zero mentre i concorrenti sono già a regime.
- _...riconfiguri troppo tardi_: perdi quote di mercato non recuperabili — è il caso del nostro produttore di LCD nello scenario.
- _...riconfiguri troppo presto_: bruci capitale su tecnologia immatura.

**L'innovazione può riguardare:**

- **solo il prodotto** (es. nuovo chip nello smartphone, ma stessa linea di assemblaggio)
- **solo il processo** (es. stesso prodotto di largo consumo realizzato con tecniche più economiche)
- **entrambi** (es. passaggio LCD → OLED: prodotto diverso E processo diverso)

## §5 Applicazione pratica — Metodologia operativa

### Step 1 — Diagnosi della fase attuale

Fai queste domande all'impianto (in quest'ordine):

1. **Escono prodotti finiti regolarmente?** No → sei ancora in concepimento o avviamento. Sì → passa al punto 2.
2. **I dati di prestazione (OEE, scarti) sono allineati al progetto?** No → ancora in avviamento (calibrazione non chiusa). Sì → passa al punto 3.
3. **I margini stanno calando e i concorrenti hanno tecnologie migliori?** No → sei a regime. Sì → stai entrando in chiusura/riconfigurazione.

### Step 2 — Identifica le attività dovute alla fase

|Fase|Attività chiave|Output atteso|
|---|---|---|
|Concepimento|Studio di fattibilità, prog. di massima ed esecutiva, acquisizione risorse, realizzazione e collaudo|Impianto pronto all'avvio|
|Avviamento|Messa in esercizio, raccolta dati, confronto con progetto, eventuale riprogettazione|Impianto stabile sulle specifiche|
|Regime|Feedback mercato, monitoraggio tecnologie sostitutive, analisi investimenti incrementali|Permanenza competitiva|
|Chiusura|Verifica obsolescenza, scelta tra modifica parziale e ricostruzione totale|Decisione: dismettere o ricominciare il ciclo|

### Step 3 — Tieni d'occhio le tecnologie sostitutive (anche durante il regime!)

Il punto cruciale che differenzia un'azienda lungimirante da una reattiva: la tecnologia B che sostituirà la tua tecnologia A va studiata **mentre A è ancora a regime**, non quando è già obsoleta. Quando A diventa obsoleta, B deve già essere pronta — anche solo a livello di studio di fattibilità.

### Checklist per non sbagliare

- [ ] Ho identificato la fase guardando i **dati**, non l'età anagrafica dell'impianto?
- [ ] Le decisioni che propongo sono **coerenti con la fase** (es. non sto chiedendo riprogettazione completa per un impianto in regime con prestazioni nominali)?
- [ ] Sto monitorando **contemporaneamente**: prestazioni interne (OEE, scarti) **+** evoluzione tecnologica esterna (concorrenti, brevetti, standard)?
- [ ] Ho mappato come il ciclo di vita dei **prodotti** realizzati su questo impianto interagisce con il ciclo di vita del **processo**?
- [ ] Ho definito un orizzonte temporale per la decisione di chiusura/riconfigurazione, invece di aspettare i numeri rossi?

## §6 Domanda tipo esame

> **Domanda (orale o scritto)**: «Descriva il ciclo di vita di un processo produttivo o di una tecnologia, evidenziando l'analogia con il ciclo di vita del prodotto e spiegando perché un'azienda dovrebbe mantenere monitorate contemporaneamente entrambe le curve.»

**Traccia di risposta strutturata** (ordine consigliato):

**1) Apertura (~30 sec)**

> Il ciclo di vita di un processo produttivo descrive l'evoluzione di un impianto industriale dalla sua ideazione alla sua dismissione, attraverso quattro fasi sequenziali. È costruito in analogia al ciclo di vita del prodotto, perché le due curve sono interconnesse e si influenzano reciprocamente.

**2) Le quattro fasi (~2 min)** — descriverle in ordine, almeno un'attività chiave per ciascuna:

- _Concepimento e progettazione_: fattibilità → progettazione di massima → esecutiva → acquisto risorse → realizzazione e collaudo.
- _Avviamento_: messa in esercizio + raccolta info + analisi vs progetto + eventuale riprogettazione mirata.
- _Regime_: feedback dal mercato, ricerca nuove tecnologie sostitutive, analisi della convenienza al rinnovo.
- _Chiusura/riconfigurazione_: verifica obsolescenza, scelta tra modifica parziale, ricostruzione totale, o trasferimento geografico.

**3) L'analogia con il ciclo del prodotto (~1 min)** — mostrare la corrispondenza:

- Sviluppo prodotto ↔ Concepimento processo
- Introduzione/crescita ↔ Avviamento (volumi crescenti, calibrazione)
- Maturità ↔ Regime
- Declino ↔ Chiusura
- Stessa forma a S anche per l'evoluzione tecnologica.

**4) Perché monitorare entrambe (~1 min)** — qui sta il punto critico:

- Un prodotto in declino può essere sostituito mantenendo lo stesso processo (innovazione di prodotto).
- Un processo obsoleto può rendere non competitivo sui costi anche un prodotto vincente (innovazione di processo).
- Le risorse produttive sono **condivise** tra più prodotti: la decisione su un singolo prodotto impatta tutti gli altri realizzati sullo stesso impianto.
- La tecnologia sostitutiva B va studiata mentre A è ancora in regime, non quando è già obsoleta — altrimenti si perdono quote di mercato non recuperabili.

**5) Chiusura forte (~15 sec)**

> In sintesi, il ciclo di vita del processo è uno strumento di **anticipazione strategica**: non descrive solo cosa succede, ma indica quando è il momento giusto per agire.

> [!tip] Variante: «Differenza tra ciclo di vita del prodotto e del processo?» Inverti l'ordine: parti dalle differenze (orizzonti temporali tipicamente più lunghi per l'impianto; per il prodotto domina il mercato, per l'impianto la combinazione tecnologia + mercato), poi mostra le interconnessioni.

## §7 Errori comuni

> [!warning] ❌ Errore 1: Confondere ciclo di vita del prodotto e del processo Sono **due curve distinte ma interconnesse**. Il prodotto ha fasi di mercato (sviluppo/introduzione/crescita/maturità/declino), il processo ha fasi tecnico-realizzative (concepimento/avviamento/regime/chiusura). Un impianto in regime può produrre prodotti in declino, e un nuovo prodotto può richiedere un processo ancora in avviamento. **Come evitarlo**: tieni mentalmente separate le due curve (con orizzonti temporali diversi: mesi-anni per il prodotto, anni-decenni per l'impianto), poi cerca le intersezioni.

> [!warning] ❌ Errore 2: Pensare che il «regime» sia una fase passiva Il regime **non è** "lasciar girare l'impianto e contare i pezzi". Le attività del regime sono attive e strategiche: feedback dal mercato, ricerca di tecnologie sostitutive, valutazione continua di convenienza al rinnovo. **Come evitarlo**: ricorda che la riconfigurazione tardiva è uno dei principali motivi di perdita di competitività. Il principio "studiare la tecnologia B mentre A è ancora a regime" è il cuore di tutto il framework.

> [!warning] ❌ Errore 3: Trattare la chiusura come un evento, non come una decisione anticipata La chiusura/riconfigurazione richiede di identificare l'obsolescenza **per tempo**, non quando i numeri sono già negativi. Aspettare le perdite economiche significa aver già perso quote di mercato non recuperabili. **Come evitarlo**: nelle risposte d'esame sulla chiusura, sottolinea sempre il concetto di **anticipo** e collegalo alla curva di evoluzione tecnologica (Figura 6 del testo: la tecnologia sostitutiva deve essere già pronta quando quella attuale diventa obsoleta).

## §8 Collegamenti

**Prerequisiti** (da sapere PRIMA):

- [[Sistema di produzione]] — definizione base e gerarchia ISA-95
- [[Pianificazione Programmazione Scheduling]] — i tre orizzonti temporali del controllo
- [[Ciclo di vita del prodotto]] — la curva analoga, fondamentale per cogliere le interconnessioni
- [[Time to market]] — concetto chiave nella fase di concepimento

**Conseguenze** (cosa ne deriva):

- [[Occasioni di progettazione]] — Cap 4: ex-novo, conversione, riconversione, ammodernamento, ampliamento orizzontale/verticale (operativizzano le decisioni della fase di chiusura/riconfigurazione)
- [[Studio di fattibilità]] — primo elaborato della fase di concepimento
- [[OEE]] — strumento di misura usato in regime per identificare deriva delle prestazioni
- [[Servitization]] — vendere servizio invece del prodotto cambia gli orizzonti del ciclo
- [[VRP - Variety Reduction Program]] — strumento di razionalizzazione tipicamente applicato in fase di regime

## §9 Auto-verifica

1. _(semplice)_ Quali sono le 4 fasi del ciclo di vita di un processo produttivo, in ordine, e qual è l'attività principale di ciascuna?
2. _(intermedia)_ Perché lo studio dell'evoluzione tecnologica è fondamentale **durante** la fase di regime, e non solo nella fase di chiusura? Cosa succederebbe se aspettassi la chiusura per iniziare a valutare le tecnologie sostitutive?
3. _(profonda)_ Spiega con un esempio concreto come una decisione presa nel ciclo di vita del **prodotto** (es. introduzione di un nuovo modello da parte di un concorrente) possa **forzare un anticipo** della fase di chiusura/riconfigurazione del ciclo di vita del **processo**. Quali interconnessioni stai usando, e perché le risorse condivise tra più prodotti rendono la decisione ancora più delicata?

---

_Fonte: `Impianti_2026.pdf`, Cap. 1 §1.2.2 «Il ciclo di vita del prodotto e del processo produttivo», pp. 25–31._

---

Un paio di note per te:

- Per il diagramma in §4 ho usato ASCII art dentro un code block: in Obsidian si renderizza pulito a font monospace, e a differenza di Mermaid non rischi che si rompa se cambi tema.
- Il caso LG/LCD→OLED in §2 è basato su dinamiche reali del settore (l'azienda esiste, l'investimento miliardario in fab Paju c'è stato, la transizione OLED è in corso) ma i numeri specifici sono illustrativi — vanno benissimo per ragionare in fase di studio, non citarli come dato esatto in esame.