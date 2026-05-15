**In 10 secondi:** Sono le sei famiglie di inefficienza in cui Nakajima (TPM, 1988) ha classificato tutto ciò che fa sì che una macchina non produca al massimo. Sono raggruppate in **3 macro-categorie** (perdite di tempo misurabili, di velocità, da difetti) e mappano direttamente sui **3 coefficienti dell'[[OEE]]** (Disponibilità, Efficienza prestazioni, Qualità).

---

## §1 Domanda fondamentale

Dove se ne va davvero il tempo della mia macchina? E come posso classificare le inefficienze in modo da sapere _dove_ agire — sulla manutenzione, sull'organizzazione del setup, o sul controllo qualità?

---

## §2 Il problema concreto

**Pharmadose S.p.A.**, casa farmaceutica di Parma, ha una linea di compressione per tablet di ibuprofene: comprimitrice rotativa a 36 punzoni, capacità di targa **200.000 tablet/h**.

A fine mese il direttore di stabilimento guarda i numeri:

- Linea aperta 24/7 → 720 h/mese, ma programmata per produrre = **600 h** (TC)
- Output reale del mese = **70 milioni di tablet**
- Output teorico se sempre alla nominale per 600 h: 200.000 × 600 = **120 milioni**

Mancano **50 milioni di tablet**. Dove sono finiti? Il direttore convoca i responsabili e ognuno dice la sua:

- Il responsabile manutenzione: _"abbiamo avuto 3 guasti grossi al gruppo punzoni"_.
- Il caporeparto: _"abbiamo perso un sacco di tempo nei cambi tra ibuprofene 200 mg e 400 mg"_.
- Il QC: _"abbiamo scartato 2 lotti perché la durezza era fuori specifica"_.
- L'operatore: _"la macchina ogni tanto rallenta perché si surriscalda, ma non l'ho mai segnalato"_.

Senza una **classificazione strutturata**, i 50 milioni di tablet persi rimangono un mistero collettivo: ognuno parla di un pezzo del problema, nessuno ha la mappa intera, e il direttore non sa quale leva tirare per prima (assumere un manutentore? rivedere le ricette? comprare una macchina nuova?).

→ Le sei grandi perdite servono esattamente a tradurre "abbiamo perso 50 milioni di tablet" in **6 caselle ben definite**, a ciascuna delle quali corrisponde una contromisura specifica.

---

## §3 La definizione

**Definizione formale:**

> Le **sei grandi perdite** (six big losses) sono le sei famiglie di inefficienze identificate da Nakajima (1988) nell'ambito del [[TPM]] (Total Productive Maintenance). Tutte rappresentano un **uso imperfetto del tempo a disposizione** dell'impianto e sono raggruppabili in **3 macro-gruppi** in base alla loro natura.

**Scomposizione in 3 gruppi e 6 perdite:**

|Gruppo|Perdite incluse|Caratteristica|
|---|---|---|
|**A. Perdite di tempo misurabili**|1. Guasti<br>2. Setup e regolazioni|Si possono contare con dati storici/contabili: ogni evento ha un report, un costo, una durata.|
|**B. Perdite di velocità** _(tempo non misurabili)_|3. Tempi morti / micro-fermate<br>4. Riduzione di velocità|Non vengono registrate in alcun documento aziendale; sfuggono al controllo diretto, vanno stimate.|
|**C. Perdite da difetti**|5. Scarti<br>6. Rilavorazioni|La macchina ha lavorato, ma il prodotto non è conforme: il tempo speso non genera valore.|

**Dettaglio delle 6 perdite:**

1. **Guasti** → fermi non pianificati per rotture meccaniche, elettriche, software.
2. **Setup e regolazioni** → cambio prodotto, riattrezzaggio utensili, tarature.
3. **Tempi morti / micro-fermate** → attese materiali, code alla macchina, piccole pause (non documentate).
4. **Riduzione di velocità** → la macchina gira sotto la nominale (rallentamenti per surriscaldamento, allentamenti, transitori).
5. **Scarti** → pezzi prodotti ma scartati al QC o danneggiati irrimediabilmente in lavorazione.
6. **Rilavorazioni** → pezzi difettosi recuperabili tramite una seconda lavorazione (recupero materiale, ma tempo macchina perso due volte).

---

## §4 Come funziona

**Cuore del meccanismo:** ogni perdita "consuma" una porzione del tempo disponibile, e la sequenza in cui si "mangiano" le porzioni segue la **gerarchia dei tempi OEE**: dal Tempo di Carico al Tempo Operativo a Valore Aggiunto.

```
TC  Tempo Carico
 ↓ — Gruppo A: guasti + setup           ⇒ riducono Disponibilità (Ap)
TO  Tempo Operativo
 ↓ — Gruppo B: tempi morti + ↓velocità  ⇒ riducono Efficienza (Ep)
TON Tempo Operativo Netto
 ↓ — Gruppo C: scarti + rilavorazioni   ⇒ riducono Qualità (Q)
TOVA Tempo Operativo a Valore Aggiunto
```

**Differenza chiave tra i 3 gruppi:**

- **Gruppo A — misurabili "grandi"**: ogni evento è documentato (un guasto genera un work-order in CMMS, un setup ha un orario di inizio e fine nel MES). Sono **visibili**, e per questo è il gruppo che le aziende attaccano per primo.
- **Gruppo B — non misurabili "piccole"**: nessuno scrive un report ogni volta che la macchina rallenta perché un sensore si è imbrattato; nessuno cronometra le micro-pause dell'operatore. Sono **invisibili** e quindi insidiose.
- **Gruppo C — visibili sul prodotto**: la perdita non è sul tempo della macchina (che ha lavorato), ma sul **valore** generato: il pezzo è da buttare o da rifare.

**Casi limite (per intuirne la logica):**

- **Solo perdite di gruppo C, zero A e B**: macchina sempre accesa, sempre alla nominale, ma metà output da buttare. È un problema di **processo** (ricetta, materia prima, taratura).
- **Solo perdite di gruppo A**: quando lavora produce perfettamente, ma è ferma metà del tempo per guasti. È un problema di **affidabilità** (manutenzione).
- **Solo perdite di gruppo B**: la macchina è quasi sempre disponibile e produce conforme, ma va a metà velocità. È il caso più subdolo, perché si fatica anche solo ad accorgersi del problema.

→ La diagnosi giusta orienta la cura giusta. Senza il framework, si rischia di "comprare un manutentore" quando il vero problema sono gli scarti, o viceversa.

---

## §5 Applicazione pratica

**Metodologia operativa step-by-step** per classificare le perdite di un impianto:

1. **Definisci il perimetro temporale**. Prendi un periodo significativo (es. 1 mese) e identifica il **TC** (tempo carico = ore programmate per produrre, già al netto delle fermate pianificate).
2. **Misura il TOVA reale**: pezzi conformi prodotti × tempo standard per pezzo.
3. **Calcola il "tempo perso totale"** = TC − TOVA. È il "buco" che le sei perdite devono spiegare integralmente.
4. **Quantifica il gruppo A** (guasti + setup): scarica i dati da CMMS, MES, log macchina. Per ogni evento avrai durata e tipo.
5. **Stima il gruppo C** (scarti + rilavorazioni): da QC reports, conta pezzi scartati e rilavorati, moltiplica per il tempo standard di produzione.
6. **Il gruppo B è il residuo**: tempo perso totale − gruppo A − gruppo C. È la "perdita di velocità", visibile solo come differenza.
7. **Per ogni perdita identifica la contromisura specifica:**

|Perdita|Contromisura tipica|
|---|---|
|1. Guasti|Manutenzione preventiva, ridondanza, analisi MTBF|
|2. Setup|[[SMED]] (Single Minute Exchange of Die), standardizzazione attrezzaggi|
|3. Tempi morti|5 perché sulle micro-fermate, video-analisi, kanban materiali|
|4. Riduzione velocità|Confronto velocità reale vs targa, sensoristica IoT, condition monitoring|
|5. Scarti|SPC (Statistical Process Control), Pareto delle cause di non conformità|
|6. Rilavorazioni|Poka-yoke, qualità integrata in linea, controllo a monte|

**Checklist anti-errore:**

- [ ] Ho **escluso** dalle sei perdite le fermate pianificate (manutenzione preventiva, festività, mancanza ordini)? Quelle stanno tra TA e TC, non sono perdite.
- [ ] Ho considerato anche i setup "piccoli" tra prodotti simili, oltre ai cambi maggiori?
- [ ] Sto quantificando il gruppo B come **residuo**? È l'unica via, perché non è misurato direttamente.
- [ ] Ho contato separatamente scarti e rilavorazioni? Le rilavorazioni "costano" il tempo macchina due volte.
- [ ] Sto attribuendo le perdite alla macchina giusta? (Un blocco a valle può fermare quella a monte: di chi è la perdita?)

---

## §6 Domanda tipo esame

**Domanda (stile orale):**

> Spiega cosa sono le "sei grandi perdite" introdotte da Nakajima nel contesto del TPM. Discuti la loro classificazione in 3 gruppi e mostra come ciascun gruppo si lega ai coefficienti dell'OEE. Fai un esempio in cui due perdite di gruppi diversi si manifestano nella stessa giornata produttiva.

**Traccia di risposta strutturata** (in che ordine toccare i punti):

1. **Origine e contesto.** Concetto introdotto da Nakajima negli anni '70 dall'Istituto Giapponese di Manutenzione Impianti, nell'ambito del [[TPM]] (Total Productive Maintenance), e portato negli USA nel 1988. La metodologia OEE nasce per misurare in modo integrato l'efficacia complessiva di un impianto, e le sei grandi perdite sono il framework concettuale alla sua base.
    
2. **Principio unificante.** Tutte le perdite sono **uso imperfetto del tempo** disponibile. Per questo l'analisi parte sempre dalla scomposizione gerarchica dei tempi: TS → TA → TC → TO → TON → TOVA.
    
3. **Le 6 perdite e i 3 gruppi.**
    
    - **Gruppo A — Perdite di tempo misurabili**: (1) guasti, (2) setup e regolazioni. Misurabili da dati aziendali: ogni guasto ha un report, un costo, una durata; ogni setup ha un orario di inizio e fine.
    - **Gruppo B — Perdite di velocità**: (3) tempi morti / micro-fermate, (4) riduzione di velocità. Non registrate in alcun documento, vanno stimate (tipicamente come residuo).
    - **Gruppo C — Perdite da difetti**: (5) scarti, (6) rilavorazioni. La macchina ha lavorato, ma il prodotto non è conforme.
4. **Mappatura sui coefficienti OEE.**
    
    - Gruppo A → riducono **Disponibilità** (Ap = TO/TC).
    - Gruppo B → riducono **Efficienza prestazioni** (Ep = TON/TO).
    - Gruppo C → riducono **Tasso di qualità** (Q = TOVA/TON).
    - OEE = Ap · Ep · Q → ogni perdita "morde" un fattore distinto, e i tre si combinano moltiplicativamente.
5. **Esempio integrato.** Linea di compressione di tablet farmaceutiche, turno di 8 h.
    
    - Si fanno 30 minuti di setup tra ibuprofene 200 mg e 400 mg → **gruppo A, perdita 2** (riduce Ap).
    - Durante la produzione la comprimitrice rallenta del 10% per surriscaldamento dei punzoni → **gruppo B, perdita 4** (riduce Ep). Nessuno l'ha registrato: lo scopro solo confrontando l'output reale con il teorico.
    - 2.000 tablet scartati per durezza fuori specifica → **gruppo C, perdita 5** (riduce Q).
    - Tre eventi indipendenti che colpiscono Ap, Ep, Q rispettivamente, e si combinano nell'OEE finale.
6. **Considerazioni critiche di chiusura.**
    
    - Il gruppo B è il più subdolo: se non lo cerco attivamente, lo "scopro" solo come residuo nei conti.
    - Le contromisure sono diverse per gruppo (manutenzione vs SMED vs SPC): la classificazione serve proprio a indirizzare le azioni.
    - L'OEE da solo dà il punteggio totale (es. 75%); le sei perdite spiegano il **perché** di quel punteggio.

**Variante** ("e se cambiasse X?"):

> _E se l'azienda avesse OEE = 60% con Ap = 95%, Ep = 70%, Q = 90%?_

Il problema è chiaramente nel **gruppo B** (Ep più basso). Investire in più manutenzione (gruppo A) sarebbe poco efficace: Ap è già al 95%. Conviene cercare le micro-fermate e i rallentamenti — probabilmente con sensoristica e analisi del cycle-time reale vs nominale.

---

## §7 Errori comuni

> [!warning] ❌ Errore 1 — Confondere fermate pianificate con perdite del gruppo A Le fermate pianificate (manutenzione preventiva programmata, festività, mancanza ordini, scioperi) sono già state tolte tra TA e TC: **NON** fanno parte delle sei perdite. I "guasti" del gruppo A sono solo le fermate **non pianificate**. **Come evitarlo:** chiediti sempre "questa fermata era a calendario?". Se sì → riduce TC ma non è una delle sei perdite; se no → è perdita 1 del gruppo A.

> [!warning] ❌ Errore 2 — Trattare le perdite di gruppo B come misurabili direttamente Tempi morti e riduzione di velocità non sono registrati in alcun documento. Cercare di "misurarli direttamente" porta a sottostime sistematiche, perché l'operatore non documenta i piccoli rallentamenti o le micro-pause. Il gruppo B si ottiene per **differenza** (tempo perso totale − gruppo A − gruppo C) o per stime tecnologiche (es. velocità nominale × tempo − pezzi prodotti). **Come evitarlo:** accetta che il gruppo B sia il residuo. Se ti viene zero, probabilmente non lo stai cercando bene.

> [!warning] ❌ Errore 3 — Trattare scarti e rilavorazioni come la stessa perdita Gli **scarti** sono pezzi buttati: tempo macchina perso una volta, materiale perso. Le **rilavorazioni** recuperano il pezzo, ma sottraggono tempo macchina **due volte** (la prima produzione difettosa + la lavorazione di recupero), e il materiale invece si recupera. Trattarle uguali sottostima sistematicamente l'impatto delle rilavorazioni. **Come evitarlo:** conta separatamente i due flussi nei dati QC e calcola l'impatto sul tempo per entrambi (con tempi standard diversi se necessario).

---

## §8 Collegamenti

**Cosa devo sapere PRIMA (prerequisiti):**

- [[Quadro sinottico tempi]]— TS, TA, TC, TO, TON, TOVA. Senza questa scala, le sei perdite non hanno una "casa" gerarchica in cui collocarsi.
- [[TPM]] — Total Productive Maintenance: il quadro filosofico in cui Nakajima propone questo framework.
- [[Sistemi di produzione]] — il contesto generale (perché vogliamo misurare le inefficienze di un impianto).

**Cosa ne consegue (dipendenze):**

- [[OEE]] — Overall Equipment Effectiveness: i tre coefficienti Ap, Ep, Q sono la **traduzione quantitativa** dei 3 gruppi di perdite.
- [[TEEP]] — estende OEE includendo l'efficienza di carico L; le sei perdite restano le stesse.
- [[Disponibilità (Ap)]] (Ap) — riduzione causata dal gruppo A.
- [[Efficienza prestazioni]] (Ep) — riduzione causata dal gruppo B.
- [[Tasso di qualità]] (Q) — riduzione causata dal gruppo C.
- [[SMED]] — tecnica per ridurre la perdita 2 (setup).
- [[Manutenzione preventiva]] / [[Manutenzione su condizione]] — strumenti per ridurre la perdita 1 (guasti).
- [[MTBF]] / [[MTTR]] — indicatori usati per stimare la disponibilità limite e dimensionare l'impatto della perdita 1.

---

## §9 Auto-verifica

1. **(facile)** Quali sono i 3 gruppi in cui si raggruppano le sei grandi perdite, e quali perdite contiene ciascun gruppo?
2. **(media)** Spiega perché il gruppo B (perdite di velocità) è chiamato "non misurabile" e come si quantifica in pratica. Cosa rischia un'azienda che lo trascura?
3. **(profonda)** Una linea di assemblaggio elettronica ha OEE = 60%, di cui Ap = 95%, Ep = 70%, Q = 90%. Senza fare conti, quale gruppo di perdite sta dominando? Che tipo di intervento priorizzeresti, e perché un intervento sui guasti (manutenzione) sarebbe in questo caso meno efficace?