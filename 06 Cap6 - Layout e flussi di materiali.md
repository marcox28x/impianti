---
aliases:
  - "06 Cap6 - Layout"
  - "Layout dei sistemi di produzione"
  - "Layout e flussi di materiali"
---
## Domanda del capitolo
**Come dispongo nello spazio le risorse calcolate al Cap 5 — macchine, reparti, magazzini — per minimizzare trasporti e disturbi reciproci, e come dimensiono movimentazione e magazzini?**

## Mini-riassunto
Lo studio del layout (macro: edifici/reparti sul sito; micro: macchine dentro i reparti) procede in 3 fasi: analisi, disposizione di primo tentativo, configurazione effettiva. Quattro tipologie: **posizione fissa**, **per processo** (≡ job shop), **per prodotto** (≡ linea), **a celle**; la scelta processo vs prodotto si fa con l'**analisi CVP** (4 zone, volume critico q*). I flussi si analizzano con diagramma multiprodotto e matrice **origine-destinazione** (principi di centralità e vicinanza); quando il flusso non basta entra il **diagramma di Buff** (A-E-I-O-U-X) con la combinabilità dei processi. Il capitolo copre poi il **material handling** (UdC, mezzi di movimentazione) e i **magazzini**: 6 indici di prestazione, tipologie di immagazzinamento, criteri di progettazione (ABC delle giacenze, rischio di sottodimensionamento) e di allocazione delle scorte. Chiude l'**espansione**: piano regolatore d'impianto, vincolato dai magazzini MP/PF.

## Concetti trattati

### 6.1 Impostazione dello studio
- MACRO-layout vs MICRO-layout; 3 fasi: analisi → disposizione di primo tentativo → configurazione effettiva; dati necessari (prodotti+volumi, cicli, flussi, vincoli)

### 6.2 Le tipologie di configurazione
- 6.2.1 [[Layout a posizione fissa]] — le risorse vanno al prodotto (cantieri, prototipi)
- 6.2.2 [[Layout per processo]] — a reparti ≡ [[Job shop]]: flessibile, ma flussi complessi, ↑TA, ↑WIP
- 6.2.3 [[Layout per prodotto]] — in linea secondo il ciclo; varianti in serie / parallelo / misto; geometrie rettilineo / a U / zig-zag
- 6.2.4 [[Layout a celle]] — linea applicata a famiglie ≡ [[Group technology]]; ⚠️ il PF può attraversare più celle, anche più volte
- 6.2.5 [[Analisi CVP]] — confronto processo vs prodotto: ⚠️ **4 zone** (nessuna in utile · solo processo · entrambe ma processo > linea · oltre q* linea); tra BEP_linea e q* la linea si sceglie solo scommettendo sull'espansione

### 6.3 L'analisi dei flussi di materiali
- Obiettivo: min CT = ΣΣ qᵢⱼ·cᵢⱼ·dᵢⱼ
- [[Matrice origine-destinazione]] — righe = uscite, colonne = ingressi, diagonale = criticità; + diagramma multiprodotto (sequenze ripetute → suggerisce celle); principi di **centralità** e **vicinanza**
- Configurazione effettiva: aree, corridoi da normativa, **poligono d'ingombro funzionale** (ingombro + operatore + movimentazione/manutenzione + depositi)

#### 6.3.1 I rapporti tra le attività ⚠️ domanda d'esame
- [[Diagramma di Buff]] — relationship chart triangolare: importanza **A-E-I-O-U-X** + motivo del legame → diagramma dei rapporti
- **Combinabilità dei processi** (chiesta ×3): fattori di disturbo (polveri, vibrazioni, calore, infiammabilità, rumore) → stringhe alfanumeriche (genera / subisce) → confronto a coppie

#### 6.3.2 Definizione delle postazioni di lavoro
- Ergonomia + economia dei movimenti: angolo visivo, lunghezza braccio, postura, accessibilità materiali

### 6.4 I sistemi di movimentazione interna
- [[Material handling]] — attività (trasporto, picking, sorting, merging, dispatching, feeding) e principi (min riprese, UdC standard, gravità, bidirezionalità)
- **Unità di carico**: 3 livelli di imballaggio (primario / secondario ⚠️ spesso è l'UdC interna / per il trasporto); accatastabilità, forcolabilità → pallet
- Mezzi: transpallet · carrelli a forche · commissionatori · AGV vs AMR · trasportatori fissi (rulli, rotelle) e mobili (nastro, tapparelle, aerei) · gru, carroponte, montacarichi

### 6.5 Magazzini ⚠️ domande d'esame frequenti
- [[Magazzini]] — ragioni delle scorte vs costi; ⚠️ MP e PF comunicano con l'esterno (vincolante)
- **6 indici di prestazione**: selettività · rotazione · saturazione superficiale · saturazione volumetrica · manodopera · potenza (chiesti ×4)
- Tipologie di immagazzinamento: sovrapposizione diretta · scaffalature (a gravità FIFO, passanti drive-in/through, compattabili, alti scaffali con trasloelevatori) · colli (rotanti, classificatori verticali) · prodotti speciali (cantilever, caselle)
- Criteri di progettazione (§6.5.4): giacenze + flussi; arrivi sui picchi, collaudo sulla media (free-pass); **ABC delle giacenze**; serie storica Gmin/Gm/Gmax (Gm → terziarizzazione); **rischio di sottodimensionamento** (curva cumulata) → G ottimo
- Criteri di allocazione (§6.5.5): posti **condivisi** vs **dedicati** vs **misti** (zone × classi; ⚠️ dimensionare sul numero **medio** di celle per codice); spettro grigio
- Movimenti **congiunti** (trasloelevatori, isocrone triangolari) vs **disgiunti** (carrelli retrattili)

### 6.6 Espansione dell'impianto
- Non sovradimensionare; prevedere le aree di ampliamento sin dal primo progetto
- **Piano regolatore di impianto** — destinazione anche delle aree non edificate; ⚠️ vincolato dai magazzini MP/PF (non spostabili)

## Formula chiave
$$ CT_{trasp} = \sum_i \sum_j q_{ij} \cdot c_{ij} \cdot d_{ij} $$

## Punti chiave per l'esame
- **CVP con le 4 zone** (non 3): tra BEP_linea e q* entrambe in utile ma il processo rende di più — la linea lì è una scommessa sull'espansione.
- Costruire una **matrice origine-destinazione** e leggere le criticità dalla diagonale; primo tentativo con centralità + vicinanza.
- **Diagramma di Buff**: scala A-E-I-O-U-X con i significati + il motivo del legame; saper impostare la **combinabilità** con le stringhe dei fattori di disturbo.
- I **6 indici di prestazione dei magazzini** con le definizioni esatte (selettività = Mu/Mt; rotazione alta ↔ costi operativi, bassa ↔ obsolescenza).
- **Allocazione**: pro/contro condivisi vs dedicati; nella mista, zone dimensionate sul numero **medio** di celle per codice.
- Dimensionamento col rischio: istogramma per classi di giacenza → curva cumulata → trade-off costi di sottodimensionamento vs costi diretti.
- Layout a celle: il prodotto può attraversare **più celle, più volte**.

## Collegamenti
- ← [[02 Cap2 - Classificazione dei sistemi di produzione]]: job shop ↔ reparti, GT ↔ celle, flow shop ↔ linea; la [[Matrice Prodotto-Processo]] è la versione "di mercato" del CVP
- ← [[04 Cap4 - Progettazione dei sistemi di produzione]]: il [[Bilancio di massa]] dà le quantità qᵢⱼ; l'[[Analisi ABC (Pareto 80-20)]] torna sulle giacenze
- ← [[05 Cap5 - Configurazione dei sistemi di produzione]]: Mj e TCL definiscono *cosa* si posiziona; i magazzini interoperazionali ([[Criterio di Vladzyevsky]]) diventano depositi nel poligono d'ingombro
- ⚠️ Cap7 (impianti di servizio) è **rimosso** dal materiale 2026 — nessun collegamento a valle
