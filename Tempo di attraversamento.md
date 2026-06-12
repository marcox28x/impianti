---
aliases:
  - "Tempi di attraversamento"
  - "indice di flusso"
  - "Tempo di ciclo TCL"
  - "Tempo di ciclo linea (TCL)"
---
# Tempo di attraversamento

> [!summary] In 10 secondi
> Il **tempo di attraversamento** ($TA$, *flow/cycle/throughput time*) è il tempo perché un pezzo attraversi una macchina o stazione, misurato in **tempo per unità prodotta**. Insieme a $TVA$ (tempo a valore aggiunto), $TCL$ (tempo di ciclo della linea) e $IF$ (indice di flusso) è il linguaggio con cui si diagnostica dove un processo "perde tempo".

## §1 Definizioni (§3.2.2 del PDF)
| Simbolo | Nome | Significato |
|---|---|---|
| $TA$ | Tempo di attraversamento (= tempo standard $TS$) | tempo perché un pezzo attraversi una macchina/stazione [tempo/unità]. Es. auto ≈ 2 giorni |
| $TVA$ | Tempo a valore aggiunto | tempo di lavorazione **effettiva**, al netto di attese, code e trasporti |
| $TCL$ | Tempo di ciclo della linea | $TA$ della macchina **più lenta** = intervallo medio fra due uscite a regime |
| $IF$ | Indice di flusso | $IF = TA/TVA$ |

Il $TA$ **non** è fatto solo di lavorazione: il pezzo può **attendere** di essere spostato o stare **in coda** a una macchina occupata. La differenza tra $TA$ e $TVA$ è proprio il tempo "sprecato".

## §2 Indice di flusso (eq. 2)
$$IF = \frac{TA}{TVA} \qquad (\geq 1 \text{ sempre})$$

| Valori | Giudizio |
|---|---|
| 10 – 100 | tipici nelle aziende |
| 3 – 5 | buoni |
| 1 – 2 | ottimi |

## §3 Esempio canonico (5 stazioni in serie)
Tempi: 10', 20', 30', 10', 20'.
- $TVA = 10+20+30+10+20 = 90$ min.
- **1° pezzo**: $TA = 90$ min (trova sempre stazioni libere → $TA = TVA$).
- **A regime**: $TA = 120$ min (blocking a monte del collo) → $IF = 120/90 = 1{,}33$ (ottimo).
- **Potenzialità** = ritmo del collo di bottiglia = 1 pezzo / 30 min = **2 pz/h**.

> [!note] Analisi a segmenti
> La linea si spezza in segmenti chiusi dalla rispettiva stazione lenta. Segmento 1 (st.1-2-3, collo 30'): $TA = 30 \cdot 3 = 90$. Segmento 2 (st.4-5): alimentato ogni 30', mai saturo → $TA = TVA = 30$. Totale $90+30 = 120$ ✓.

## §4 Trappole d'esame ⚠️
> [!warning] Doppio uso di TA e TS
> $TA$ = tempo di **attraversamento** (qui) **≠** $TA$ = tempo di **apertura** (gerarchia OEE, [[Quadro sinottico tempi]]). $TS$ = tempo **standard** $=1/P$ (qui) **≠** $TS$ = tempo **solare** (8760 h). Dichiarare sempre quale si usa.

> [!warning] $P \neq 1/TA$ in generale
> Vale solo per macchina isolata senza starving/blocking. In linea: legge di Little $WIP = P \cdot TA$.

## §5 Collegamenti
- [[Potenzialità produttiva]] — il collo determina P; TA e P sono duali
- [[Quadro sinottico tempi]] — attenzione al doppio uso del simbolo TA
- [[Capacità produttiva (CP)]] — $CP = P \cdot TA \cdot TEEP$
- [[Job shop]] / [[Flow shop]] — il job shop ha TA e IF alti, il flow shop bassi
- §3.2.2 di `Impianti_2026 - 03` · [[03 Cap3 - Prestazioni dei sistemi di produzione]] · [[_Knowledge Graph v2]] §3.2.2
