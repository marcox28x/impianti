
> Atomic note · Fonte: `Impianti_2026.pdf`, Cap 1 §1.2.1, pp. 17-20

---

## 1. DOMANDA

Come faccio a offrire tanti prodotti diversi al cliente **senza farmi esplodere i costi** dovuti alla varietà?

---

## 2. IL PROBLEMA

Immagina un'azienda di orologi. Il mercato vuole **50 modelli diversi**: sportivi, eleganti, subacquei, da donna, edizioni limitate, smart, analogici. Fino a ieri, i progettisti per ogni modello disegnavano tutto da zero: cassa, meccanismo, quadrante, lancette, cinturino, ghiera, fibbia.

Facciamo i conti: 50 modelli × ~10 parti significative = **500 codici** diversi da progettare, acquistare, stoccare, assemblare, documentare, manutenere come ricambio. Moltiplica per costi di progettazione, fornitori, magazzini, setup macchina a ogni cambio lotto.

**Il dilemma che emerge:**

- Se **standardizzi tutto** → vendi un solo orologio tutto uguale → il cliente scappa dal concorrente che personalizza.
- Se **personalizzi tutto** → i costi di varietà ti soffocano → margini zero → fuori mercato nel medio periodo.

Serve una terza via.

---

## §3 LA DEFINIZIONE

**VRP (Variety Reduction Program)** = tecnica di progettazione _integrata e trasversale_ di un'intera gamma di prodotti, con l'obiettivo di **ridurre numero e varietà dei componenti** necessari, senza sacrificare la differenziazione percepita dal cliente.

La filosofia: non progettare un prodotto alla volta, ma **pensare la gamma intera come sistema**.

Si concretizza in **4 azioni**:

1. **Scomposizione parti** → ogni componente è fisso, semi-variabile, o variabile
2. **Combinazione** → moduli standard aggregati in modi diversi (principio LEGO)
3. **Multifunzionalità e integrazione** → "fare di più con meno"
4. **Range** → un componente con ampio intervallo d'uso al posto di N componenti specifici

---

## §4 COME FUNZIONA

**Il cuore in una frase:** _separa quello che deve restare uguale da quello che può cambiare, e progetta la famiglia intera — non il singolo prodotto — attorno a quella separazione._

### Diagramma logico (esempio orologio)

```
        FAMIGLIA DI PRODOTTI (es. orologi)
                     │
         ┌───────────┼───────────┐
         │           │           │
      PARTI       PARTI        PARTI
      FISSE    SEMI-VARIAB.   VARIABILI
         │           │           │
   meccanismo      ghiera,    quadrante,
   interno      fibbia cint.   cinturino
         │           │           │
  "core product"  caratter.   differenziano
   (invisibile)  accessorie   (il cliente
     al cliente    non basic    sceglie QUI)
         │       da sole)         │
         │                        │
   ↑ volume ↑                  ↑ varietà ↑
   ↓ costo unit ↓              ↓ volume ↓
   (economie scala)             (mix alto)
```

L'analisi è **verticale**: parti dal basso della BOM e spingi verso l'alto più componenti possibili nella categoria "fissa". Quello che resta nelle semi-var e var è il minimo indispensabile per mantenere la percezione di scelta.

### Cosa accade se…

|Scenario|Conseguenza|
|---|---|
|Sposti troppe parti tra le FISSE|Prodotti percepiti tutti uguali → calo vendite|
|Lasci troppo nelle VARIABILI|Costi varietà esplodono di nuovo → VRP fallito|
|Classifichi male una parte variabile come fissa|Stai standardizzando il differenziatore → disastro commerciale|
|Applichi VRP gradualmente|Riduzione costi senza perdita di soddisfazione cliente ✓|
|Applichi VRP di colpo|Cliente percepisce perdita di varietà → reazione negativa|

---

## §5 APPLICAZIONE PRATICA

### Formula

Non c'è una formula matematica chiusa — VRP è una **metodologia**, non un calcolo. Esistono però indicatori che puoi tracciare:

```
Indice di commonality = N_componenti_condivisi / N_componenti_totali   ↑ meglio
% riduzione codici   = 1 − (codici_post / codici_pre)                  ↑ meglio
Time-to-market       (tempo idea → lancio)                             ↓ meglio
```

### Passo passo

1. **Raggruppa** i prodotti in famiglie (stessa funzione di base, stesso mercato target)
2. **Analisi verticale della BOM**: per ogni componente chiedi _"il cliente lo vede? lo sceglie? se non ci fosse se ne accorgerebbe?"_
3. **Classifica** ogni componente: FISSA / SEMI-VAR / VARIABILE
4. **Applica le 4 azioni in sequenza**:
    - **Scomposizione** → massimizza le parti FISSE → nasce il _core product_
    - **Combinazione** → progetta i non-fissi come moduli combinabili su più livelli
    - **Multifunzionalità** → riprogetta per fare lo stesso con meno pezzi (nuovi materiali, integrazione funzioni)
    - **Range** → un componente con range 1-10 sostituisce dieci componenti con range 1-1
5. **Ridisegna la BOM di famiglia** con la nuova struttura
6. **Introduci gradualmente** nella gamma esistente, monitorando reazione clienti

### Checklist per non sbagliarsi

- [ ] Sto ragionando sulla **famiglia intera**, non sul singolo prodotto?
- [ ] Le parti classificate "fisse" sono davvero invisibili/non-differenzianti per il cliente?
- [ ] Le parti variabili sono ancora abbastanza per mantenere la percezione di scelta?
- [ ] L'introduzione è **graduale**, non shock?
- [ ] Ho quantificato il beneficio atteso (codici, costi, time-to-market)?
- [ ] Ho coinvolto marketing, non solo progettazione? (rischio di standardizzare il differenziatore)

---

## §6 ERRORI COMUNI

❌ **Confondere VRP con "fare un solo prodotto"** → _Perché è sbagliato:_ VRP non elimina la varietà percepita dal cliente, solo quella nascosta nel back-end. Sono due cose diverse. → _Come evitarlo:_ tieni a mente il principio guida — la varietà **resta** per il cliente (quadrante, cinturino), **sparisce** dove non guarda (meccanismo).

❌ **Classificare come "fissa" una parte che il cliente usa per scegliere** → _Perché è sbagliato:_ stai standardizzando proprio il differenziatore. Risultato: il cliente non percepisce più differenze tra i modelli e se ne va dal concorrente. → _Come evitarlo:_ regola empirica — _"se la parte compare sul materiale di marketing o in vetrina, è variabile"_. Se il marketing team la cita nelle brochure, non toccarla.

❌ **Applicare VRP a un singolo prodotto isolato** → _Perché è sbagliato:_ VRP ha senso solo con una **gamma** di prodotti correlati. Su un singolo prodotto stai facendo semplice Design for Manufacturing, non VRP. → _Come evitarlo:_ parti sempre da almeno una famiglia di 3+ prodotti che condividono funzione di base e mercato.

---

## §7 COLLEGAMENTI

### Cosa devo sapere PRIMA (prerequisiti)

- [[Mass customization]] → il problema che VRP risolve: personalizzazione su linea di massa
- [[Distinta base]] / [[BOM]] → l'oggetto che VRP ristruttura
- [[Economie di scala vs Economie di scopo]] → le leve che VRP sfrutta (parti fisse ad alto volume = scala; gamma condivisa = scopo)
- [[Ciclo di vita del prodotto]] → il contesto che rende urgente ridurre time-to-market
- [[Standardizzazione e personalizzazione]] → il trade-off che VRP gestisce

### Cosa ne consegue (dipendenze)

- [[Concurrent engineering]] → evoluzione naturale: progettare prodotto+processo insieme, su tutta la gamma
- [[Design modulare]] / [[Prodotti modulari vs integrali]] → formalizzazione della azione "Combinazione"
- [[Postponement]] → la personalizzazione VRP spostata il più a valle possibile nel processo
- [[Group Technology]] → lo stesso principio "famiglie" applicato al layout di fabbrica
- [[Distinta base di ordinazione]] → beneficia di VRP perché riduce codici di acquisto, lotti minimi, fornitori

---

## §8 NOTA PERSONALE

### Cosa mi è difficile

Distinguere "semi-variabile" da "variabile" nei casi reali. Sulla carta (ghiera vs quadrante) è ovvio, ma in prodotti complessi il confine è **sfumato**. La regola empirica che mi aiuta: _"il cliente lo menziona quando descrive il prodotto a un amico?"_ → se sì, è **variabile**; se no, è semi-var o fissa.

### Come lo ricordo

**Trucco mnemonico** → le 4 azioni stanno sull'acronimo **S-C-M-R**:

- **S**componi (fisse/semi/var)
- **C**ombina (moduli)
- **M**ultifunzionalizza (meno pezzi, più funzioni)
- **R**angia (allarga il range)

**Immagine mentale** → l'**orologio**. Se ti ricordi:

- meccanismo → fisso
- ghiera/fibbia → semi-var
- quadrante/cinturino → variabile

…hai in tasca il 70% della teoria. Il restante 30% sono le 4 azioni.

### Dubbi rimasti

- Quanto costa _implementare_ VRP? Il testo parla solo di benefici, ma la transizione organizzativa (riprogettazione di BOM esistenti, rinegoziazione con fornitori, formazione) deve essere consistente. Non c'è una stima.
- Esistono **metriche standard** accettate per misurare il successo di un VRP (indice di commonality, ecc.) o ogni azienda si fa le sue?
- Come si concilia VRP con mercati dove la **personalizzazione estrema è il valore** (alta moda, sartoriale, lusso)? Sembra un'eccezione strutturale.
- Relazione con il [[CODP]]: VRP sposta il punto di disaccoppiamento più a valle? O agisce su un asse ortogonale?

---

**📚 Fonte dal documento:**

> `Impianti_2026.pdf`, Cap 1 "Introduzione ai sistemi di produzione", §1.2.1 "Standardizzazione e personalizzazione", **pp. 17-20**