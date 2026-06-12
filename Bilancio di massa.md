---
tags: [impianti, cap4, esame]
tipo: atomic-note
capitolo: "[[04 Cap4 - Progettazione dei sistemi di produzione]]"
aliases:
  - "Diagramma quantitativo"
  - "Materie prime e ausiliarie"
---
# Bilancio di massa

> [!tldr] In 10 secondi
> Il **diagramma quantitativo** del processo (§4.2.2): quantifica materie prime, semilavorati e prodotti in ingresso/uscita. ⚠️ Domanda d'esame classica: *gli elementi in uscita sono **8*** — 3 a valore (prodotti, sottoprodotti, cascami) + 5 da valorizzare (scarti, sfridi/ritagli, boccami, rottami, perdite/cali/rifiuti).

## INPUT
```
MP PRINCIPALI ≔ oggetto del processo
  definite   [forma già orientata al PF: getti, fucinati, tranciati, estrusi]
  indefinite [forma commerciale: lingotti, barre, lamiere, lastre]
PARTI COMPONENTI ≔ entrano nel PF SENZA lavorazione
MP AUSILIARIE ≔ concorrono alla trasformazione
  dirette   [restano nel PF, imputabili: colle, primer]
  indirette [non nel PF → ripartizione costi: oli, lubrorefrigeranti]
```

## OUTPUT — 8 voci totali ⚠️
**A valore (3):**
- **prodotti** — scopo principale
- **sottoprodotti** — stesse caratteristiche di utilità ma secondari per intenzione [glicerina nei saponi; gas nelle cokerie]
- **cascami** — residui inevitabili a valore inferiore [sanse dell'olio]

**Da valorizzare (5):**
- **scarti** → rilavorazione ∨ declassificazione ∨ (rottami/rifiuti)
- **sfridi e ritagli** → riutilizzo diretto ∨ recupero materia [spuntature, bavature, rifilature, trucioli]
- **boccami** → appendici funzionali del processo [colatoi, materozze, maschere]
- **rottami** → materiale indefinito → recupero materia
- **perdite, cali, rifiuti** → non recuperabili

## Dove si colloca
È una delle rappresentazioni del processo (§4.2.2), insieme a:
- diagramma **qualitativo** (a blocchi / descrittivo / annidato → "schema d'impianto")
- diagramma **sequenziale** (+ simbologia ASME: ○ operazione, □ controllo, ⇒ trasporto, D attesa, ▽ immagazzinamento, con tempi/quantità/distanze)
- diagramma di **Sankey** (frecce ∝ flusso, processi continui)
- schemi di **lavorazione e montaggio** (convergenza componenti → assiemi)

## Trappole d'esame
- ⚠️ Sottoprodotto ≠ cascame: il sottoprodotto ha **stesse caratteristiche di utilità** (è secondario solo per intenzione); il cascame ha **valore inferiore**.
- ⚠️ MP ausiliarie dirette restano **nel** prodotto finito (imputabili); le indirette no (costi da ripartire).
- ⚠️ Le quantità del bilancio di massa alimentano i flussi qij dell'analisi dei flussi di layout ([[Matrice origine-destinazione]]).

## Collegamenti
- PRIMA: [[Ciclo di lavorazione]], [[Distinta base (BOM)]] (coefficienti di impiego e scarto)
- CONSEGUE: [[Matrice origine-destinazione]] — i flussi quantificati entrano nello studio del layout
- [[04 Cap4 - Progettazione dei sistemi di produzione]] · [[_Knowledge Graph v2]] §4.2.2
