---
aliases:
  - "04 Cap4 - Progettazione"
  - "Progettazione dei sistemi di produzione"
---
## Domanda del capitolo
**Quando e come si progetta (o riprogetta) un sistema produttivo, con quali archivi tecnici e strumenti di rappresentazione, e come si raccordano progettazione di prodotto e di processo?**

## Mini-riassunto
Progettare impianti = **comporre elementi** rispondendo a obiettivi e vincoli, con visione olistica. Le occasioni sono l'ex-novo (raro) e — molto più spesso — la riprogettazione (conversione, riconversione, ammodernamento, ampliamenti, sicurezza). Il progetto si analizza su **5 sotto-progetti** (finanziario, prodotto, processo, architettonico, commerciale) e si articola in **studio di fattibilità** (11 fasi) → progetto di **massima** → **definitivo** → **esecutivo**, con trade-off costi di investimento ↔ costi di produzione. Gli archivi tecnici sono la **distinta base**, il **ciclo di lavorazione** e il **foglio di lavoro**; il processo si rappresenta con 4 diagrammi (qualitativo, sequenziale ASME, quantitativo, Sankey) e si chiude col **bilancio di massa** (8 voci in uscita). Cerniera prodotto↔processo è l'**ingegnerizzazione**, che minimizza il **costo della complessità** via analisi ABC e make-or-buy.

## Concetti trattati

### 4.1 Elementi di progettazione
- [[Elementi di progettazione]] — comporre, non disegnare macchine; sistema = scatola nera in un contesto più ampio; progettazione **immanente** all'esercizio

#### 4.1.1 Le occasioni di progettazione
- [[Occasioni di progettazione]] — ex-novo vs riprogettazione (conversione · riconversione · ammodernamento · ampliamento orizzontale/verticale · interventi di sicurezza)
- ⚠️ marginalità: CP impianto = saturazione del fattore a più bassa capacità → l'ampliamento sfrutta prima i fattori non saturi

#### 4.1.2 Le dimensioni di analisi
- 5 sotto-progetti: **finanziario** (CP + costo max ammissibile) · **prodotto** · **processo** · **architettonico** · **commerciale** → ciclo iterativo con verifiche di congruenza (in [[Elementi di progettazione]])

#### 4.1.3 Articolazione del progetto
- [[Studio di fattibilità]] — "business plan interno", 11 fasi che convergono sul piano finanziario; si interrompe appena emersa l'inopportunità
- Progetto di **massima** (alternative + schemi) → **definitivo** (autorizzazioni di legge) → **esecutivo** (ogni elemento con prezzo)
- Trade-off investimento ↔ costi di produzione; la capacità di influire sui costi **decresce** all'evolvere del progetto

### 4.2 I processi produttivi
- [[Processo produttivo]] — 5 attività (operazioni, trasporti, controlli, attese, immagazzinamenti); progettazione = scelta tra varianti note; macchine **specializzate** vs **general purpose**; automazione

#### 4.2.1 Gli archivi tecnici
- [[Distinta base (BOM)]] — padre→figli; rappresentazioni (albero, scalare, riepilogata); **esplosione** (fabbisogni, ricambi) vs **implosione** (modifiche, esaurimento scorte); dati di legame (coefficiente di impiego, coefficiente di scarto, validità, lead time); DB di progetto → produzione → ordinazione → concurrent engineering
- [[Ciclo di lavorazione]] — sequenza operazioni con reparto/macchina/tempi; + **foglio di lavoro** (parametri tecnologici per singola operazione)

#### 4.2.2 Ulteriori rappresentazioni dei processi
- Diagramma **qualitativo** (schema d'impianto) · **sequenziale** (simboli ASME: ○ □ ⇒ D ▽) · **quantitativo** · **Sankey** (frecce ∝ flusso) · schemi di lavorazione e montaggio
- [[Bilancio di massa]] — input (MP principali definite/indefinite · parti componenti · MP ausiliarie dirette/indirette) e **8 voci in uscita**: 3 a valore (prodotti, sottoprodotti, cascami) + 5 da valorizzare (scarti, sfridi/ritagli, boccami, rottami, perdite/cali/rifiuti)

### 4.3 L'ingegnerizzazione
- [[ingegnerizzazione|Ingegnerizzazione]] — raccordo progettazione prodotto ↔ processo; iter: programma → famiglie per similitudine tecnologica → ABC → make-or-buy → cicli
- [[Costo della complessità]] — varia con la diversità, non coi volumi; 4 livelli: unit / batch / product / facility
- [[Analisi ABC (Pareto 80-20)]] — fascia A ≈ 80% del valore → ciclo in dettaglio; B → analisi di convenienza; C → candidata a eliminazione
- [[Make or buy]] — principio guida = standardizzazione: parti **unificate** (UNI/EN/ISO) · **da catalogo** · **da normazione aziendale**

## Punti chiave per l'esame
- Le **occasioni di progettazione** in ordine di complessità decrescente, con la trappola della marginalità.
- I **5 sotto-progetti** e l'**articolazione** massima → definitivo → esecutivo (cosa produce ciascun livello).
- Saper **disegnare una distinta base** a 2-3 livelli con i coefficienti; **esplosione vs implosione** e i rispettivi usi.
- Differenza **scarto** (non conforme, forse rilavorabile) vs **sfrido** (residuo tecnologico inevitabile); gli **8 elementi in uscita** dal bilancio di massa (domanda d'esame esplicita).
- I **5 simboli ASME** e la lettura di un diagramma sequenziale.
- **Ingegnerizzazione**: definizione + iter; i 4 livelli del costo della complessità con esempi.
- Saper **costruire un'analisi ABC** (istogramma decrescente + cumulato → fasce A/B/C) — chiesta ×4 in `domande_impianti`, anche come esercizio.
- Le 3 categorie di standardizzazione nel make-or-buy.

## Collegamenti
- ← [[01 Cap1 - Introduzione ai sistemi di produzione]]: VRP e ciclo di vita motivano l'ingegnerizzazione; [[Ubicazione impianto]] è la fase 6 dello studio di fattibilità
- ← [[03 Cap3 - Prestazioni dei sistemi di produzione]]: OEE e CP definiscono i target del progetto
- → [[05 Cap5 - Configurazione dei sistemi di produzione]]: **DB + ciclo di lavorazione** sono gli input degli elementi minimi TPi del bilanciamento
- → [[06 Cap6 - Layout e flussi di materiali]]: il **bilancio di massa** dà le quantità qij dell'analisi dei flussi; ABC giacenze (§6.5.4) = stesso strumento dell'ABC famiglie; similitudine tecnologica → [[Layout a celle]]
