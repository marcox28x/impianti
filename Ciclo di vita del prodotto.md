
**In 10 secondi**: ogni prodotto nasce, cresce, invecchia e muore — e il sistema produttivo deve cambiare con lui. Il ciclo di vita del prodotto (PLC) è la mappa che ti dice in che fase sei e cosa fare di conseguenza.

---

## §1 Domanda fondamentale

Perché un'azienda non può progettare il suo sistema produttivo "una volta e per sempre"? Perché il prodotto che produce non è eterno: cambiano i volumi venduti, cambia la concorrenza, cambia il margine. Il **Product Life Cycle** ti dà un linguaggio per **anticipare questi cambiamenti** e decidere con quale sistema produttivo accompagnarli.

---

## §2 Il problema concreto

Pensa al mercato delle **fotocamere digitali compatte** (le "point-and-shoot"). Nel 2010 il mondo ne vendeva circa **120 milioni di pezzi/anno**. Canon, Nikon, Sony, Panasonic avevano tutti grandi stabilimenti dedicati, linee di assemblaggio automatizzate, contratti pluriennali con fornitori di sensori CMOS, magazzini distribuiti su tre continenti.

Poi è successa una cosa: lo **smartphone** ha integrato una fotocamera "abbastanza buona" per il 95% degli usi quotidiani. Nel 2020 quelle stesse fotocamere compatte vendevano circa **8 milioni di pezzi/anno** — un crollo del **93%** in dieci anni.

Il dilemma:
- chi nel 2012-2013 ha continuato a investire in capacità produttiva si è ritrovato con linee sovradimensionate, magazzini pieni di scorte invendibili, personale in esubero;
- chi ha disinvestito troppo presto avrebbe perso anni di profitti durante la fase di maturità.

→ Capire **dove sei nel ciclo di vita** è la differenza tra strategia industriale e disastro.

---

## §3 La definizione

Il **ciclo di vita del prodotto** descrive l'evoluzione di un prodotto da **due prospettive complementari** (entrambe vanno citate).

**Prospettiva di mercato** — andamento di vendite e profitti nel tempo:

| Fase | Cosa succede | Volumi | Margini |
|---|---|---|---|
| Sviluppo prodotto | Ideazione, progettazione, prototipi, test | 0 | < 0 (investimenti R&S) |
| Introduzione | Lancio sul mercato, promozione, distribuzione | Bassi | Bassi (costi unitari alti) |
| Crescita | Primi successi, economie di scala, nuovi concorrenti | In rapida crescita | In aumento |
| Maturità | Saturazione mercato, differenziazione, guerra prezzi | Alti ma stabili | In riduzione |
| Declino | Sostituti tecnologici, calo domanda, abitudini cambiate | In calo | Sempre più stretti |

**Prospettiva fisica (spazio-tempo)** — viaggio del prodotto da risorsa a rifiuto:

| Fase | Attività |
|---|---|
| Acquisizione risorse | Approvvigionamento materie prime e componenti |
| Produzione | Trasformazione e assemblaggio |
| Distribuzione | Logistica e immagazzinamento fino al cliente |
| Utilizzo | Vita del prodotto presso l'utente, servizi accessori (manutenzione, garanzia) |
| Fine vita | Riutilizzo, riciclo, smaltimento |

> Le due prospettive **non sono alternative**: la prima ti dice *quando* fare cosa, la seconda *cosa* succede al prodotto a livello fisico (e ha un peso crescente per la sostenibilità ambientale).

---

## §4 Come funziona

**Il cuore del concetto**: ogni fase del ciclo richiede un **sistema produttivo diverso**, perché cambiano i vincoli (volumi, varietà, costi target, time-to-market richiesto). Il PLC non è un dato osservativo passivo — è uno strumento che guida le decisioni progettuali.

**Diagramma logico** (prospettiva di mercato):

```
   Sviluppo  →  Introduzione  →  Crescita  →  Maturità  →  Declino
      |             |              |            |            |
      v             v              v            v            v
  R&S, proto-   promozione,    aumento      automaz.,    disinvest.,
  tipi, time-   bassi vol.,    capacità,    differenz.,  riconvers.,
  to-market     costi alti     eco. scala   prezzi giù   ammodernam.

  vendite:   /\
            /  \________
           /            \____
          /                  \____
         /                        \___
   _____/                             \_____  →  tempo
```

**Casi limite e varianti** (questi vanno citati per dimostrare comprensione, non meccanico ripasso):

- **Prodotti senza vero declino**: benzina, pane, cemento — domanda quasi anelastica nel tempo, il PLC è "schiacciato" sulla maturità per decenni.
- **Rinascite (revival)**: dischi in vinile, orologi meccanici di lusso, fotocamere istantanee Polaroid — prodotti dichiarati morti che tornano per nicchie ad alto margine. Il PLC non è strettamente monotono.
- **Cicli accelerati**: nella moda fast-fashion (Zara, H&M) un prodotto attraversa tutte le fasi in 6-12 settimane.
- **Cicli paralleli**: la stessa azienda gestisce contemporaneamente prodotti in fasi diverse → portfolio bilanciato (un prodotto in declino finanzia uno in introduzione).

**Collegamento con il ciclo di vita del processo produttivo** (sezione §1.2.2 dedicata): anche le tecnologie produttive seguono un loro PLC (affermazione → diffusione → maturità → obsolescenza). L'azienda lungimirante introduce la **tecnologia sostitutiva B** mentre la **tecnologia A** è ancora in maturità, così quando A diventa obsoleta B è già pronta per garantire continuità di business.

---

## §5 Applicazione pratica

**Metodologia step-by-step** — come usare il PLC nella progettazione/riprogettazione di un sistema produttivo:

1. **Posiziona il prodotto sulla curva**. Guarda andamento storico delle vendite (almeno 3-5 anni), numero di concorrenti, evoluzione dei margini, presenza di prodotti sostitutivi. Stabilisci la fase corrente.
2. **Identifica le leve critiche di quella fase** (vedi tabella sotto).
3. **Confronta con il sistema produttivo attuale**: è coerente con la fase? Esempio classico di errore: una linea ultra-rigida e iper-automatizzata è giustificata in maturità ma è suicida in introduzione (volumi bassi, specifiche che cambiano ancora).
4. **Pianifica la transizione alla fase successiva**. Se sei in crescita avanzata, inizia già a pensare a come gestirai la maturità (probabilmente ↑automazione, ↓costi unitari).
5. **Mantieni un occhio sul ciclo di vita del processo**. Quando arriva la tecnologia sostitutiva? Hai un piano B?

**Tabella operativa fase → priorità del sistema produttivo**:

| Fase | Priorità | Sistema produttivo tipico |
|---|---|---|
| Sviluppo | Time-to-market, flessibilità progettuale | [[Concurrent engineering]], prototipazione rapida |
| Introduzione | Flessibilità, capacità di modificare specifiche | Layout per processo, [[Job shop]] |
| Crescita | Aumento capacità, economie di scala | Investimento in automazione, transizione verso linee |
| Maturità | Efficienza, costi, qualità | [[Flow shop]], [[Group technology]], [[Just-in-time]] |
| Declino | Disinvestimento controllato, conversione | [[Riprogettazione]] (conversione/riconversione/ammodernamento) |

> [!check] Checklist per applicare il PLC senza sbagliare
> - [ ] Ho dati di vendita su almeno 3-5 anni?
> - [ ] Ho considerato concorrenti e prodotti sostitutivi?
> - [ ] Ho un'ipotesi sul trend (curva), non solo sulla fase istantanea?
> - [ ] Ho distinto la prospettiva di mercato da quella fisica/spazio-tempo?
> - [ ] Ho mappato la fase del **prodotto** *e* quella del **processo produttivo**?
> - [ ] Ho pensato alle azioni di **transizione** verso la fase successiva, non solo a quelle di gestione del presente?

---

## §6 Esercizio / domanda tipo esame

> **Domanda (orale o scritto aperto)**:
> "Spiega il concetto di ciclo di vita del prodotto, distinguendo le due prospettive con cui viene declinato, e discuti come la fase del ciclo di vita influenzi le scelte progettuali del sistema di produzione. Porta un esempio concreto."

**Traccia di risposta strutturata** — punti da toccare e in quest'ordine:

1. **Apertura — perché serve**. I sistemi produttivi devono evolvere perché i prodotti non sono eterni: cambiano volumi, concorrenza, margini. Il PLC è lo strumento concettuale per leggere e anticipare questa evoluzione.

2. **Doppia prospettiva** (è il punto su cui i prof tendono a insistere):
   - *rispetto al mercato*: 5 fasi (sviluppo → introduzione → crescita → maturità → declino), con il loro andamento di vendite e profitti;
   - *rispetto allo spazio-tempo*: 5 fasi (acquisizione → produzione → distribuzione → utilizzo → fine vita), focus su trasformazioni fisiche e impatti ambientali.

3. **Implicazioni progettuali per fase**:
   - in **sviluppo/introduzione** il sistema deve essere **flessibile** (specifiche instabili, bassi volumi) → layout per processo, job shop;
   - in **crescita/maturità** prevalgono **efficienza e scala** → automazione, linee, [[Flow shop]];
   - in **declino** entrano in gioco le scelte di [[Riprogettazione]] (conversione, riconversione, ammodernamento).

4. **Ciclo di vita del processo produttivo**: legame con l'evoluzione tecnologica, importanza di avere la tecnologia sostitutiva pronta prima che quella corrente diventi obsoleta.

5. **Esempio concreto**: fotocamere compatte → produzione di massa in maturità (~2010, 120 mln pz/anno) → disinvestimento progressivo e riconversione verso fotocamere mirrorless di alta gamma in fase di declino (post-2015, ~8 mln pz/anno nel 2020).

6. **Chiusura — collegamenti**: il PLC è alla base della logica di [[Time to market]], della [[VRP|Variety Reduction Program]] e delle decisioni di posizionamento del [[CODP]] sul flusso produttivo.

> [!example] Variante: "E se il prodotto avesse un revival?"
> Risposta breve: il PLC non è una legge fisica, è un modello descrittivo. Casi come vinile, Polaroid, orologi meccanici mostrano che un prodotto in apparente declino può rientrare in fase di crescita su segmenti di nicchia ad alto margine. La conseguenza pratica per il sistema produttivo è importante: si passa da produzione di massa a produzione **artigianale o per piccoli lotti** (job shop, layout flessibili). La curva del PLC, in questi casi, va ripensata **per segmento di mercato**, non per il prodotto in assoluto.

---

## §7 Errori comuni

> [!warning] ❌ Errore 1 — Confondere o dimenticare una delle due prospettive
> Pensare al PLC solo come "sviluppo → declino" (curva di mercato) ignorando la prospettiva spazio-tempo (acquisizione → fine vita). All'esame **vanno presentate entrambe**: sono complementari, non alternative.
> *Come evitarlo*: ricordati che la prima è una **curva sul tempo** (vendite/profitti), la seconda è una **sequenza di trasformazioni fisiche** del prodotto.

> [!warning] ❌ Errore 2 — Trattare il PLC come una "legge di natura"
> Considerare le fasi come inevitabili e con durate fisse. La realtà ha molte eccezioni: prodotti senza declino (commodity), revival, cicli accelerati (fast fashion), cicli che durano decenni (farmaceutici sotto brevetto).
> *Come evitarlo*: presenta il PLC come **modello descrittivo qualitativo**, non come previsione esatta. Specifica sempre il settore di riferimento.

> [!warning] ❌ Errore 3 — Non collegare il PLC al sistema produttivo
> Spiegare le 5 fasi e fermarsi lì. Ma il punto del capitolo è proprio che il PLC **guida le scelte di progettazione del sistema**: quale layout, quale livello di automazione, quanta capacità installare, quando riprogettare.
> *Come evitarlo*: chiudi sempre con la frase "in questa fase il sistema produttivo deve…". Senza questo passaggio la risposta resta nozionistica.

---

## §8 Collegamenti

**Prerequisiti** (cosa devo sapere prima):
- [[Sistema di produzione]] — definizione di base e obiettivi del sistema
- [[Contesto competitivo]] — perché il ciclo di vita si è compresso (globalizzazione, evoluzione consumatore, innovazione tecnologica)
- [[Time to market]] — leva critica nella fase di sviluppo

**Conseguenze / dipendenze** (cosa deriva dal PLC):
- [[VRP]] — strategia per gestire la varietà di prodotti in fasi diverse del ciclo
- [[Mass customization]] — risposta produttiva alla compressione del PLC
- [[Servitization]] — estensione del PLC tramite servizi accessori (allunga la fase di utilizzo)
- [[Concurrent engineering]] — riduce la fase di sviluppo, anticipa l'introduzione
- [[Riprogettazione]] — interventi sul sistema produttivo nelle fasi di maturità/declino (conversione, riconversione, ammodernamento, ampliamento orizz./vert.)
- [[CODP]] — la fase del PLC influenza il posizionamento del decoupling point (un prodotto giovane spesso parte ETO/MTO, in maturità diventa MTS)
- [[Postponement]] — leva progettuale per gestire varietà in fase di maturità

---

## §9 Auto-verifica

1. **Base**: quali sono le cinque fasi del ciclo di vita del prodotto rispetto al mercato? Cosa caratterizza ciascuna in termini di volumi e margini?

2. **Intermedia**: perché il PLC ha **due prospettive** e non una sola? Cosa aggiunge la prospettiva fisica (spazio-tempo) rispetto a quella di mercato? In quali decisioni progettuali pesa di più ciascuna delle due?

3. **Profonda**: un'azienda di elettronica di consumo ha un prodotto in **fase di maturità avanzata**, con margini in compressione e un concorrente che ha appena lanciato un sostituto innovativo. Quali decisioni di progettazione/riprogettazione del sistema produttivo metti sul tavolo, e come motivi le scelte alla luce del PLC del **prodotto** *e* del PLC del **processo produttivo**?