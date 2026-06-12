---
tags: [impianti, cap3, esercizio]
tipo: esercizio-svolto
capitolo: "[[03 Cap3 - Prestazioni dei sistemi di produzione]]"
---
# Esercizio svolto — OEE linea di stampaggio

> [!tldr] In 10 secondi
> Caso narrativo sull'[[OEE]]: il collega che dice "siamo al 55%" ha calcolato (senza saperlo) il **[[TEEP]]** — un numero aggregato che **non dice dove intervenire**. La scomposizione L·Ap·Ep·Q localizza le perdite: qui il problema più grosso è **L** (impianto scarico), poi **Ep** (rallentamenti).

## Situazione
Linea di stampaggio, mese di 30 giorni. Il direttore: *"Abbiamo mancato il target di 1.700 pezzi. Dove li abbiamo persi? Compro un'altra macchina? Formo gli operatori? Cambio fornitore? Riorganizzo i turni?"*

Dati:
- Tempo solare TS = 720 h · impianto aperto TA = 400 h
- Fermate pianificate + cause esterne (manutenzione programmata, mancanza ordini, sciopero): 80 h
- Guasti + set-up (fermate misurabili): 40 h
- Ritmo di targa P = 60 pz/h → tempo standard = 1/60 h/pz
- Usciti 14.000 pz: conformi 13.300 · scarti 500 · rilavorati 200
- Target: 15.000 conformi

## Il "55%" del collega
400 h × 60 pz/h = 24.000 pz teorici; 13.300/24.000 = **55,4%**. È esattamente TOVA/TA = **TEEP**: vero, ma inutilizzabile da solo — aggrega quattro cause diverse che richiedono **terapie diverse**. ⚠️ Con quel numero non si risponde a *nessuna* delle domande del direttore.

## Scomposizione (gerarchia dei tempi, §3.2.4)
```
TA  = 400 h
TC  = 400 − 80  = 320 h    → L  = 320/400 = 80%
TO  = 320 − 40  = 280 h    → Ap = 280/320 = 87,5%
TON = (1/60)·14.000 = 233,3 h → Ep = 233,3/280 = 83,3%
TOVA= (1/60)·13.300 = 221,7 h → Q  = 13.300/14.000 = 95%

OEE  = Ap·Ep·Q = 0,875·0,833·0,95 = 69,3%   (= TOVA/TC ✓)
TEEP = L·OEE  = 0,80·0,693      = 55,4%    (= il "55%" del collega ✓)
```

## Dove sono finiti i 24.000 − 13.300 = 10.700 pezzi
| Causa | Tempo | Pezzi persi | Leva |
|---|---|---|---|
| L — fermate pianificate/cause esterne | 80 h | 4.800 | commerciale/organizzativa (ordini, turni) — NON è inefficienza produttiva |
| Ap — guasti + set-up | 40 h | 2.400 | manutenzione ([[TPM]]), SMED |
| Ep — rallentamenti, microfermate | 46,7 h | 2.800 | formazione operatori, attese materiali |
| Q — scarti + rilavorazioni | 11,7 h | 700 | qualità/fornitore MP |

## Risposte al direttore
- **Macchina nuova? NO** — l'impianto è già scarico: L = 80% (80 ore senza produzione programmata). Comprare capacità con l'impianto non saturo è la risposta sbagliata. ⚠️ L è invisibile all'OEE: si vede solo nel TEEP.
- **Riorganizzo i turni?** — agisce su L/TA: utile solo se ci sono ordini da soddisfare in quelle ore.
- **Formo gli operatori? SÌ, prima priorità interna** — Ep = 83,3% è il coefficiente più debole dentro il TC (2.800 pezzi).
- **Cambio fornitore?** — Q = 95% è il coefficiente migliore (700 pezzi): ultima priorità.
- Verifica col target: CP = P·TC·OEE = 60·320·0,693 = 13.300 ✓. Per 15.000 conformi a parità di TC servirebbe OEE = 78% — raggiungibile recuperando Ep e metà delle fermate misurabili.

## Collegamenti
- [[OEE]] · [[TEEP]] · [[Quadro sinottico tempi]] · [[Capacità produttiva (CP)]]
- [[Efficienza di carico (L)]] · [[Disponibilità (Ap)]] · [[Efficienza prestazioni (Ep)]] · [[Tasso di qualità (Q)]]
- [[Sei grandi perdite (six big losses)]] — la classificazione delle perdite usata qui
- [[_Knowledge Graph v2]] §3.2.4 e §⚠️ trappola n.6 (L invisibile all'OEE)
