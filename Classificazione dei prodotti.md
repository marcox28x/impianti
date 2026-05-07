

> **In 10 secondi:** i prodotti si classificano per **aggregazione** (a che livello li guardo), **complessità gestionale** (quanto è incasinata la distinta base) e **modularità** (i pezzi sono intercambiabili o no) e ognuna di queste tre risposte vincola le scelte di sistema a valle.

---

## §1 Domanda fondamentale

**Quali caratteristiche di un prodotto devo descrivere per poter decidere come produrlo?**

Detto in altro modo: prima di scegliere il sistema produttivo (CODP, layout, processi), mi serve un linguaggio per parlare del prodotto stesso. Senza questo linguaggio non riesco a giustificare nessuna scelta di sistema.

---

## §2 Il problema concreto

Sei il responsabile pianificazione di un'azienda di **smartphone**. Sul catalogo hai:

- 8 modelli (base, Plus, Pro, Pro Max × 2 generazioni)
- 5 tagli di memoria
- 6 colori
- 4 mercati con SKU diversi per imballo e accessori

Totale: ~960 SKU attivi. Su ognuno devi decidere quanti pezzi fare, dove tenerli a stock, quali componenti ordinare. Tre cose ti tormentano subito:

1. **A che livello pianifico?** Sui 960 SKU? Impossibile fare previsioni a 12 mesi a quel dettaglio. Ma per dire al magazzino "spedisci 200 pezzi del Pro 256GB nero a Milano" il livello SKU mi serve eccome.
2. **Quanto è complicato il prodotto da coordinare?** Il Pro Max ha display OLED, doppia fotocamera, modulo 5G, batteria custom — ognuno con i suoi fornitori, i suoi lead time, i suoi rischi. Il modello base ne ha la metà.
3. **I pezzi sono intercambiabili?** Se lo schermo del Pro va su tutte le varianti Pro, posso tenerne uno solo a stock e configurare alla fine. Se ogni modello ha schermo proprio, devo previsionare ogni variante singolarmente.

→ Tre dilemmi diversi. Servono **tre criteri diversi** per descriverli. Da qui il capitolo.

---

## §3 La definizione

I prodotti si classificano lungo **tre criteri indipendenti** (un prodotto va etichettato su tutti e tre):

### Criterio 1 — Aggregazione

A che livello di dettaglio guardo il prodotto?

|Livello|Cosa è|Quando lo uso|
|---|---|---|
|**Codice / item / SKU**|Lo specifico prodotto, distinguibile per ogni attributo (colore, taglia, imballo)|Controllo produzione e logistica|
|**Famiglia / modello**|Set di codici accomunati da affinità produttiva (stessi attrezzaggi, set-up brevi tra codici della famiglia)|Pianificazione di medio periodo|
|**Tipo / tipologia**|Gruppo di famiglie con costi simili e domanda con stesse caratteristiche (stagionalità, mercato)|Previsioni e piani di lungo periodo|

### Criterio 2 — Complessità (gestionale)

Quanto è difficile **coordinare** le attività produttive del prodotto? Si misura sulla **distinta base**:

- **profondità** = numero di livelli della distinta (semilavorati, sottoassiemi, sotto-sottoassiemi…)
- **ampiezza** = numero di codici diversi presenti a uno stesso livello

→ **Prodotto semplice**: distinta piatta, pochi componenti. Spesso detto "ricetta". Tipico delle produzioni di processo. → **Prodotto complesso**: distinta profonda _e_ ampia. Tante fasi in sequenza, tanti oggetti diversi che convergono.

### Criterio 3 — Modularità

I componenti del prodotto sono **moduli con interfacce standardizzate**?

- **Modulare**: i moduli si combinano liberamente. Ogni modulo si progetta e si gestisce indipendentemente. La sincronizzazione resta confinata all'**assemblaggio finale**.
- **Integrale**: niente moduli standard. Si lavora "prodotto per prodotto", la complessità non si abbatte.

---

## §4 Come funziona

> **Una frase:** le tre classificazioni rispondono a tre domande non sovrapponibili — _a che zoom guardo? quanto è incasinata la struttura? i pezzi sono intercambiabili?_ — e ogni risposta tocca una leva di sistema diversa.

### Diagramma logico

```
            PRODOTTO
                │
   ┌────────────┼────────────┐
   │            │            │
AGGREGAZIONE  COMPLESSITÀ   MODULARITÀ
   │            │            │
 (zoom)      (struttura)  (architettura)
   │            │            │
   ▼            ▼            ▼
livello di   forma della    presenza di
dettaglio    distinta base  interfacce
                            standard
   │            │            │
   ▼            ▼            ▼
 incide su    incide su      incide su
 pianifica-   coordinamento  postponement
 zione vs     e program-     e CODP
 controllo    mazione        (ATO!)
```

### Cosa accade se...

- **...l'azienda è monoprodotto?** Il criterio aggregazione collassa: c'è un solo SKU, niente famiglie, niente tipi.
- **...la distinta è cortissima ma il processo è infernale?** Hai un prodotto **gestionalmente semplice ma tecnologicamente complesso**. È la trappola classica → vedi §7.
- **...hai prodotti modulari ma l'organizzazione non lo è?** Spreco la leva: i moduli ci sono, ma se non hai team dedicati per modulo e supply chain coerente, il vantaggio resta sulla carta.
- **...hai un prodotto integrale e provi a fare ATO?** Non puoi. ATO presuppone modularità: senza moduli standard non c'è niente da assemblare al volo.

---

## §5 Applicazione pratica (metodologia)

Quando devi classificare un prodotto in un esercizio o in un caso, segui questi step **in ordine**:

### Step 1 — Identifica il livello di aggregazione utile alla domanda

Chiediti: _"per cosa sto classificando?"_

- Previsione di vendita 18 mesi → livello **tipo**
- Piano di produzione trimestrale → livello **famiglia**
- Schedulazione settimanale + magazzino → livello **SKU**

### Step 2 — Apri la distinta base e misura

- Conta i **livelli** sotto al prodotto finito → profondità
- Conta i **codici** al primo livello (e a quelli intermedi) → ampiezza
- Classifica: distinta corta e magra → **semplice**; distinta lunga e/o larga → **complesso**

⚠️ Stai parlando di **complessità gestionale**. Non guardare il processo tecnologico in questo step.

### Step 3 — Cerca le interfacce standard

- I componenti chiave sono intercambiabili tra varianti?
- I fornitori producono moduli "a catalogo" o pezzi customizzati per ogni prodotto?
- Si assemblano in tempi brevi senza coordinamento intensivo?

→ Sì = **modulare**. No = **integrale**.

### Checklist anti-errore

- [ ] Ho separato i 3 criteri (sono indipendenti, non scegli "uno solo")?
- [ ] Sulla complessità, ho distinto **gestionale** vs **tecnologica**?
- [ ] Sull'aggregazione, ho legato il livello allo **scopo** (controllo vs pianificazione)?
- [ ] Sulla modularità, ho cercato **interfacce standard** e non solo "tante varianti"?
- [ ] Ho pensato alle **conseguenze sul sistema** (CODP, layout)?

---

## §6 Domanda tipo esame

> **"Illustra i criteri di classificazione dei prodotti e spieghi perché tali classificazioni non sono indipendenti dalle scelte di classificazione dei sistemi produttivi."**

### Traccia di risposta strutturata

**1. Premessa (30 secondi)** Inquadra: la classificazione del prodotto precede e vincola quella del sistema. Tre criteri indipendenti tra loro: aggregazione, complessità, modularità.

**2. Aggregazione** Spiega i tre livelli (SKU, famiglia, tipo) legandoli allo scopo: SKU per controllo operativo, famiglia per pianificazione tattica (criterio: comunanza di attrezzaggio / set-up brevi), tipo per pianificazione strategica e previsioni.

**3. Complessità (qui il prof drizza le orecchie)** Definisci la complessità come **gestionale**, misurata sulla distinta base con due dimensioni: profondità e ampiezza. → **Esempio anti-confusione**: la carta. Distinta semplicissima (cellulosa, acqua, additivi) → gestionalmente semplice. Ma il processo tecnologico richiede una macchina continua con controllo serrato di temperatura, pressione, umidità → tecnologicamente complessa. **Le due dimensioni sono ortogonali.**

**4. Modularità** Definisci modulare vs integrale. Cita l'esempio di Dell: modularità del PC → supply chain con fornitori indipendenti dei moduli → assemblaggio finale rapido in pochi giorni → consegna su ordine. Aggancia il concetto di "organizzazione modulare" (team divisi per modulo).

**5. Collegamento ai sistemi (chiusura, qui prendi i punti)** Mostra le tre catene tipiche:

- prodotto **semplice** + ricetta → produzione di processo → spesso **MTS** (cemento, carta)
- prodotto **complesso integrale** → produzione di parti, job shop → tipicamente **ETO/MTO** (cantieri, macchine speciali)
- prodotto **complesso modulare** → produzione di parti con assemblaggio finale → **ATO** (auto, PC) → abilita il **postponement**

Conclusione: senza la classificazione del prodotto, le scelte di CODP, layout e processi sarebbero arbitrarie.

---

## §7 Errori comuni

> [!warning] ❌ Errore 1 — Confondere complessità gestionale e tecnologica **Cosa sbaglio:** dire "la carta è semplice" o "lo smartphone è complesso" senza specificare di quale complessità parlo. **Perché:** il prof usa la carta proprio per beccare chi confonde i due piani. La carta ha distinta cortissima (gestionalmente semplice) ma processo tecnologicamente sofisticatissimo. Sono due assi indipendenti. **Come evitarlo:** quando dici "complesso", aggiungi sempre l'aggettivo. _"Gestionalmente complesso, perché la distinta base ha profondità X e ampiezza Y."_

> [!warning] ❌ Errore 2 — Confondere modularità con varietà **Cosa sbaglio:** pensare che 1000 SKU diversi = prodotto modulare. **Perché:** la varietà è il numero di prodotti finiti a catalogo. La modularità è la **presenza di interfacce standard tra componenti**. Zara ha tantissime SKU ma i prodotti non sono modulari (un cappotto non si "assembla" da moduli intercambiabili). Dell ha meno SKU ma è altamente modulare. **Come evitarlo:** chiediti _"posso ricombinare i componenti senza riprogettarli?"_ Se sì, è modulare.

> [!warning] ❌ Errore 3 — Trattare l'aggregazione come pura tassonomia commerciale **Cosa sbaglio:** dire "famiglia = stesso brand", "tipo = stesso scaffale". **Perché:** in produzione la famiglia si definisce per **affinità produttiva** (stessi attrezzaggi, set-up brevi tra codici della famiglia), non per criterio di marketing. Lo stesso prodotto può stare in famiglie diverse a seconda dello scopo (commerciale vs produttivo). **Come evitarlo:** specifica sempre il criterio di aggregazione (_"famiglia in senso produttivo, basata su comunanza di attrezzaggio"_).

---

## §8 Collegamenti

### Prerequisiti (cosa devo sapere prima)

- [[01 Cap1 - Introduzione ai sistemi di produzione]] — cos'è un sistema produttivo, attività di trasformazione
- Concetto di **distinta base** (livelli, codici, sottoassiemi)

### Conseguenze (cosa abilita)

- [[02 Cap2 - Classificazione sistemi di produzione]] — i 4 criteri di sistema (CODP, processi, layout, lavoro) si appoggiano alla classificazione del prodotto
- [[CODP - Customer Order Decoupling Point]] — la modularità del prodotto sposta il CODP a destra (verso ATO)
- [[Postponement]] — abilitato dalla modularità + aggregazione gestita per famiglia
- [[Variety Reduction Program|Variety Reduction Program (VRP)]] — agisce su modularità e commonality per ridurre complessità gestionale
- [[06 Cap6 — Layout e flussi]] — la complessità del prodotto guida la scelta job shop vs flow shop

---

## §9 Auto-verifica

Rispondi senza guardare la nota. Dalla più semplice alla più profonda:

1. **Quali sono i 3 criteri di classificazione del prodotto e cosa misurano?** _(Suggerimento: zoom, struttura, architettura.)_
    
2. **Perché un foglio di carta è gestionalmente semplice ma tecnologicamente complesso? Cosa cambia tra le due dimensioni?** _(Devi tirare fuori: distinta corta vs processo che richiede controllo continuo di parametri fisici.)_
    
3. **Un'azienda fa prodotti integrali (no moduli standard). Può adottare un'architettura ATO con assemblaggio finale su ordine? Perché sì o perché no? E cosa cambierebbe se passasse a un design modulare?** _(Risposta che il prof vuole: no, perché ATO presuppone moduli pre-prodotti combinabili al volo. Senza interfacce standard ogni ordine richiederebbe coordinamento punto a punto. Passando a modulare → si può anticipare la produzione dei moduli a stock e confinare la sincronizzazione al solo assemblaggio finale → leva il **postponement**.)_
    

---

#impianti #classificazione #prodotto #cap2