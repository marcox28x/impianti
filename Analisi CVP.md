---
aliases:
  - "Break Even Point"
  - "Volume critico q*"
  - "Layout per processo vs per prodotto"
---

# Analisi CVP (Costo–Volume–Profitto) — §6.2.5

Confronto economico tra [[Layout per processo]] (reparti) e [[Layout per prodotto]] (linea), nei casi in cui la scelta **non è obbligata** (non vale per impianti di processo o prodotti ingombranti/inamovibili → [[Layout a posizione fissa]]).

## Le rette

Costi totali lineari nel volume q: `CT = CF + cv·q`

| | CF (intercetta) | cv (pendenza) | perché |
|---|---|---|---|
| **per PROCESSO** (reparti) | minore | **maggiore** | meno investimenti; ↑trasporti interni, ↑WIP |
| **per PRODOTTO** (linea) | **maggiore** | minore | macchinari, sistemi di trasporto, automazione |

Ricavi: `R = p·q` (ipotesi: **tutta la quantità prodotta si vende**).

Due intersezioni R–CT → due **break-even point**: BEP_processo < BEP_linea (i CF minori del processo lo portano in utile prima). L'intersezione tra le **due rette di costo** definisce il **volume critico q***.

## Le 4 zone ⚠️

> Il PDF dice "tre zone significative" ma poi ne descrive una quarta oltre q* → ai fini d'esame contarle come **4** (forma del KG v2).

1. `q < BEP_processo` — **nessuna** configurazione genera utile.
2. `BEP_processo < q < BEP_linea` — **solo il processo** genera utili.
3. `BEP_linea < q < q*` — **entrambe in utile, ma processo > linea**. ⚠️ La linea qui si sceglie solo scommettendo su una **futura espansione** delle vendite: si rinuncia a utile iniziale in cambio di maggiore redditività quando i volumi cresceranno.
4. `q > q*` — la **linea** genera utili maggiori, costantemente.

**Volume critico q*** ≔ quantità oltre la quale conviene passare da una disposizione per processo a una per prodotto.

`q* = (CF_linea − CF_processo) / (cv_processo − cv_linea)`

Nota: q* è l'intersezione delle rette di **costo** → non dipende da p. Il prezzo serve invece per i BEP e quindi per le zone 1–3: l'analisi completa è di costo *e* di ricavo.

## Esempio numerico (analogia: automazione vs manuale)

Stessa struttura del confronto processo/linea — robot ≈ linea (CF alti, cv basso), operatore ≈ reparti (CF ≈ 0, cv alto). Assemblaggio schede:

- Robot: CF = 500.000 €/anno (ammortamento), cv = 0,50 €/pz
- Manuale: CF ≈ 0, cv = 5 €/pz

`q* = 500.000 / (5 − 0,50) ≈ 111.000 pz/anno`

- a 10.000 pz/anno: robot 50,5 €/pz vs manuale 5 €/pz → vince il manuale
- a 1.000.000 pz/anno: robot 1 €/pz vs manuale 5 €/pz → vince il robot

Il meccanismo è "assorbire" il costo fisso: il costo unitario del robot è `CF/q + cv`, e il termine `CF/q` crolla al crescere di q. Ciò che ripaga l'investimento è il risparmio per pezzo (cv_man − cv_robot) **moltiplicato per il volume**. Stesso trade-off del Cap 4 (costi di investimento ↔ costi di produzione, [[Elementi di progettazione]]) e delle [[economia di scala|economie di scala]].

## Trappole d'esame ⚠️

- **Zona 3**: tra BEP_linea e q* entrambe le configurazioni sono in utile ma il **processo rende di più** — errore tipico: "sopra il BEP della linea conviene la linea". Falso: conviene solo oltre q*.
- q* è l'intersezione dei **costi**, i BEP sono intersezioni costi–**ricavi**: non confonderli.
- Ipotesi forte: tutto il prodotto si vende (R = p·q senza invenduto).
- Con **più di un prodotto** il volume da solo non basta: confronto più articolato su costi e prestazioni (Figura 12: posizionamento dei layout nel piano ampiezza mix × volumi → coerente con la [[Matrice Prodotto-Processo]]).

## Collegamenti

- ← [[06 Cap6 - Layout e flussi di materiali]] (§6.2.5)
- ← [[Layout per processo]] · [[Layout per prodotto]] — le due alternative confrontate
- → [[Matrice Prodotto-Processo]] — versione "di mercato" dello stesso trade-off
- → [[economia di scala]] — ↑volumi → ↓costo unitario nelle soluzioni capital intensive
- → [[Elementi di progettazione]] — trade-off investimento ↔ costi di produzione (Cap 4)
