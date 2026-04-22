## Domanda del capitolo
**Come dimensiono gli impianti ausiliari (energia, acqua, aria compressa, vapore, gas) che alimentano le utenze produttive?**

## Mini-riassunto
Gli impianti di servizio sono trasversali a tutto il sistema produttivo. Prima scelta: **centralizzato vs decentralizzato** (oppure misto) — il centralizzato ha economie di scala e rendimenti di targa maggiori ma paga costi e perdite di rete e concentra il rischio di guasto. Seconda scelta: **frazionamento** — suddividere la potenzialità totale in n unità uguali aumenta elasticità e disponibilità e riduce la riserva necessaria. Terza scelta: **accumulatore polmone** — un serbatoio tra generatore e utenze permette di dimensionare il generatore sulla domanda media anziché sul picco; la domanda si stima come q = Σ P_i · f_CO,i · f_CA,i quando non si hanno diagrammi di carico. Il dimensionamento ottimo minimizza CT_generatore + CT_accumulatore, con q_opt > q_media.

## Concetti trattati

### 7.1 Centralizzazione vs decentralizzazione
- [[Impianto centralizzato]]
- [[Impianto decentralizzato]]
- [[Tipologie di rete]] (aperta, a cascata, chiusa/anello)
- [[Perdite di linea]]

### 7.2 Frazionamento e riserva
- [[Frazionamento della potenzialità]]
- [[Unità di riserva]]
- [[Elasticità e disponibilità]]
- [[Ottimizzazione n + r]]

### 7.3 Dimensionamento con accumulatore
- [[Accumulatore polmone]]
- [[Stima della domanda senza diagrammi di carico]]
- [[Fattore di contemporaneità]]
- [[Fattore di carico]]
- [[Dimensionamento ottimo del generatore]]

## Formule chiave
- $q = \sum_i P_i \cdot f_{CO,i} \cdot f_{CA,i}$
- $\min\ CT_{sist} = CT_{gen}(q_G) + CT_{acc}(q_G)$ con $q_{opt} > q_m$

## Punti chiave per l'esame
- Tabella pro/contro **centralizzato vs decentralizzato** (scala, perdite, rischio guasto).
- Perché il frazionamento **riduce la riserva** necessaria a parità di disponibilità.
- Logica dell'accumulatore: **carica quando q_utenze < q_gen, scarica quando >**, permette di dimensionare il generatore sulla media.
- Distinguere **fattore di contemporaneità** (prob. di funzionamento simultaneo) da **fattore di carico** (prob. di richiesta max).

## Collegamenti
- ← [[06 Cap6 — Layout e flussi]]: le utenze sono quelle disposte nel layout
- ← tutti i capitoli precedenti: il servizio è al servizio del sistema
- (capitolo di chiusura)