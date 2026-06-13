---
aliases:
  - "Sistemi di movimentazione"
  - "Movimentazione interna"
  - "Unità di carico (UdC)"
---
# Material handling

> [!summary] In 10 secondi
> Il **material handling** (§6.4) è la movimentazione interna dei materiali: trasporto, picking, sorting, merging, dispatching, feeding. Obiettivo: la giusta quantità del giusto materiale nel posto giusto, nei tempi richiesti, a **costo minimo**. Si organizza intorno alle **unità di carico (UdC)** e a una gamma di mezzi.

## §1 Attività e principi
**Attività**: trasporto · stoccaggio · **picking** (prelievo frazionato) · **sorting** (smistamento) · **merging** (raggruppamento) · **dispatching** (indirizzamento) · **feeding** (alimentazione macchine).

**Principi**: min numero di movimentazioni e riprese · min distanze · UdC a dimensioni **standard** (trasportare unità intere) · traiettorie **lineari** (le curve causano blocchi) · **bidirezionalità** (no viaggi a vuoto) · sfruttare la **gravità** (rulli, scivoli) · **meccanizzazione** dell'attività ripetitiva senza valore aggiunto.

## §2 Unità di carico (UdC, §6.4.2)
Raggruppamento movimentabile con mezzi meccanici che **uniforma** presa-trasporto-rilascio. 3 livelli di imballaggio:
- **primario** (vendita al consumatore: scatole, bottiglie);
- **secondario** (raggruppa unità di vendita: cartoni, cassette) — ⚠️ spesso è l'**UdC interna** movimentata in impianto;
- **per il trasporto** (pallet, casse, roll).

Requisiti: **accatastabilità** + **forcolabilità** (presa coi carrelli a forca) → **pallet** standard.

## §3 Tipologie di mezzi (§6.4.3)
| Mezzo | Caratteristica |
|---|---|
| **Transpallet** | sollevamento ~13 cm, trasferimento orizzontale, 2000–3000 kg |
| **Carrelli a forche** | corridoi >3 m, ~3 m/s, 2500–9000 kg, altezze 6–11 m |
| **Commissionatori** | per il picking, operatore a bordo forche, fino ~9 m |
| **AGV** | percorso predefinito (guide) ma riprogrammabile |
| **AMR** | autonomo, sensori + telecamere, senza infrastrutture fisse |
| **Trasportatori fissi** | rulli / rotelle (il mezzo non accompagna il carico) |
| **Trasportatori mobili** | vassoi, nastro, tapparelle, aerei a catena |
| **Sollevatori pesanti** | gru, carroponte, montacarichi |

## §4 Collegamenti
- [[Matrice origine-destinazione]] — i flussi che il handling deve servire
- Magazzini (indici, allocazione) — vedi [[06 Cap6 - Layout e flussi di materiali]]
- §6.4 di `Impianti_2026 - 06` · [[_Knowledge Graph v2]] §6.4
