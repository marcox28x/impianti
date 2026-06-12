---
aliases:
  - "MTBF"
  - "MTTR"
---
# MTBF e MTTR

> [!summary] In 10 secondi
> **MTBF** (*Mean Time Between Failures*) e **MTTR** (*Mean Time To Repair*) sono i parametri affidabilistici da cui si stima **ex-ante** la [[Disponibilità (Ap)]] di una macchina, prima ancora di avere dati storici di esercizio.

## §1 Definizioni
- **MTBF** = tempo medio fra due guasti successivi (più alto = più affidabile).
- **MTTR** = tempo medio per riparare (più basso = più manutenibile).

## §2 Disponibilità limite
$$A_p^{lim} = \frac{MTBF}{MTBF + MTTR}$$

È la stima **da targa** della [[Disponibilità (Ap)]], usata nel **primo dimensionamento** quando manca uno storico aziendale (vedi [[Capacità produttiva (CP)]], dove OEE/L/Ap/Ep/Q si prendono da impianti simili).

> [!warning] ⚠️ Affidabilità nel materiale 2026
> Il trattamento completo dell'affidabilità (R(t), λ, Weibull, RBD, FTA) è presente in `domande_impianti` ma **assente dal PDF Cap3 2026**. MTBF/MTTR compaiono però come stima della disponibilità. Vedi lo [[CLAUDE|schema]].

## §3 Collegamenti
- [[Disponibilità (Ap)]] — il coefficiente OEE che MTBF/MTTR stimano ex-ante
- [[Sei grandi perdite (six big losses)]] — i guasti che MTBF misura
- [[_Knowledge Graph v2]] §3.2.4 (e §⚠️ n.21)
