---
aliases:
  - "Efficienza prestazioni"
  - "Efficienza delle prestazioni"
  - "Efficienza delle prestazioni Ep"
  - "Efficienza prestazioni - Ep"
  - "Efficienza prestazioni Ep"
---
# Efficienza prestazioni (Ep)

> [!summary] In 10 secondi
> L'**efficienza delle prestazioni** ($E_p$, *Efficiency Performance*) misura la **velocità reale** di un centro di lavoro come **percentuale della sua velocità di progetto**. È uno dei tre fattori dell'[[OEE]] ($OEE = A_p \cdot E_p \cdot Q$) e cattura le perdite di **velocità**: rallentamenti e micro-fermate.

## §1 Definizione (§3.2.4 del PDF, eq. 15–17)
$$E_p = \frac{T_{ON}}{T_O} \qquad (15)$$

dove $T_{ON}$ = tempo operativo **netto** e $T_O$ = tempo operativo (vedi gerarchia in [[Quadro sinottico tempi]]).

È un **numero puro** che esclude gli effetti della **qualità** ([[Tasso di qualità (Q)]]) e della **disponibilità** ([[Disponibilità (Ap)]]): isola la sola componente di **velocità**.

## §2 Perché si calcola in modo indiretto (⚠️ chiave d'esame)
Il tempo perso per **rallentamenti e fermate non misurabili** non è rilevabile direttamente → $T_{ON}$ non è noto a priori. Si ricorre allora ai **tempi standard**:

$T_{ON}$ è il tempo destinato a realizzare prodotti — **conformi, scarti e rilavorazioni**. Lo si ottiene moltiplicando il tempo standard $TS = 1/P$ (distanza fra due uscite, reciproco di [[Potenzialità produttiva]]) per la quantità globale realizzata:

$$E_p = \frac{TS \cdot (Q_c + Q_s + Q_r)}{T_O} \qquad (17)$$

> [!note] Multiprodotto
> Nel caso di più prodotti si usa $TS = 1/P_{mix}$ (vedi [[Potenzialità di mix]]).

## §3 Valori tipici
| Layout | $E_p$ tipica |
|---|---|
| **Linea** | 0,80 – 0,95 |
| **Reparti** (job shop) | 0,65 – 0,80 |

## §4 Trappola: rilavorazioni ignote ⚠️
Spesso $Q_r$ (rilavorazioni) non è tracciata. Si usa l'approssimazione **per difetto**:
$$E_p^* = \frac{TS \cdot (Q_c + Q_s)}{T_O} < E_p \qquad (26)$$

Specularmente $Q^* = \frac{Q_c}{Q_c+Q_s} > Q$ (per eccesso). Il punto cruciale:
$$E_p^* \cdot Q^* = E_p \cdot Q \;\Rightarrow\; \boxed{OEE \text{ INVARIATO}}$$

Gli errori si **compensano esattamente**. Errore tipico d'esame: affermare che "senza $Q_r$ l'OEE è sbagliato" → **falso**.

## §5 Collegamenti
### Prerequisiti
- [[Potenzialità produttiva]] — fornisce $TS = 1/P$
- [[Quadro sinottico tempi]] — definisce $T_{ON}$ e $T_O$ nella gerarchia $TS \to TA \to TC \to TO \to TON \to TOVA$
- [[Sei grandi perdite (six big losses)]] — le perdite di velocità che $E_p$ cattura

### Fratelli (gli altri fattori OEE)
- [[Disponibilità (Ap)]] — $A_p = T_O/T_C$ (fermate misurabili)
- [[Tasso di qualità (Q)]] — $Q = T_{OVA}/T_{ON}$ (scarti e rilavorazioni)
- [[Efficienza di carico (L)]] — $L = T_C/T_A$ (visibile solo nel [[TEEP]])

### Conseguenze
- [[OEE]] — $OEE = A_p \cdot E_p \cdot Q$
- [[Capacità produttiva (CP)]]

### Vedi anche
- §3.2.4 di `Impianti_2026 - 03` (eq. 15–17, 26) · [[_Knowledge Graph v2]] §3.2.4
