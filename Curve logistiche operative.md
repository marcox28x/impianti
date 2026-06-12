# Curve logistiche operative

> [!summary] In 10 secondi
> Le **curve logistiche operative** (Hopp & Spearman, §5.3.4) modellano la relazione fra **WIP, potenzialità (P) e tempo di attraversamento (TA)** a WIP costante in linea. Tre curve di riferimento delimitano le prestazioni possibili: **caso migliore**, **caso peggiore** e **massima casualità** (il "caso pratico peggiore").

## §1 Il contesto
La [[Legge di Little e WIP|legge di Little]] $WIP = P \cdot TA$ è una equazione in tre incognite → infinite soluzioni. Le curve logistiche fissano il comportamento di P e TA al variare del WIP $w$, dati $P_b$ (collo) e $WIP_c = P_b \cdot TVA$.

## §2 Caso migliore (§5.3.4.2)
Ipotesi: linea **perfettamente bilanciata**, 1 macchina/stazione, tempi **deterministici**, CONWIP.
$$TA_{best} = \begin{cases} TVA & w \leq WIP_c \\ w/P_b & w > WIP_c \end{cases} \qquad P_{best} = \begin{cases} w/TVA & w \leq WIP_c \\ P_b & w > WIP_c \end{cases}$$
⚠️ con linea bilanciata e 1 macch/staz, $WIP_c$ = numero di macchine.

## §3 Caso peggiore (§5.3.4.3)
Ipotesi: **lotti** = valore conwip, tempi sbilanciati al limite. **Deterministico** (limite teorico, non concreto).
$$TA_{worst} = w \cdot TVA \qquad P_{worst} = \frac{1}{TVA}$$

## §4 Massima casualità (§5.3.4.4) — "caso pratico peggiore"
Ipotesi: linea bilanciata, 1 macch/staz, tempi **casuali ~ esponenziale** (senza memoria), stati equiprobabili.
$$TA_{maxcas} = TVA + \frac{w-1}{P_b} \qquad P_{maxcas} = \frac{w \cdot P_b}{WIP_c + w - 1}$$

## §5 Le aree del diagramma
Separate dalla curva di massima casualità:
- **area POSITIVA** (tra massima casualità e caso migliore) → buone prestazioni;
- **area NEGATIVA** (verso il caso peggiore) → margini di miglioramento.

> [!warning] ⚠️ Controintuitivo
> Il caso **peggiore** è **deterministico** (lotti, nessuna casualità); la massima casualità è il caso *pratico* peggiore. Un impianto reale ben gestito sta in area positiva.

## §6 Incremento prestazioni (§5.3.4.6)
- **Potenziare il collo** (↑$P_b$): curve si alzano, WIP invariato, ma investimenti ingenti.
- **Potenziare i non-colli** (↓$TVA$ → ↓$WIP_c$): conviene per **piccoli** valori di WIP.

## §7 Collegamenti
- [[Legge di Little e WIP]] — la base $WIP = P \cdot TA$ e $WIP_c$
- [[Numero di risorse]] — collo e bilanciamento determinano $P_b$ e $TVA$
- esempio **Gagghi Anchia** ($P/P_{maxcas}=68\%$, area negativa) in [[Legge di Little e WIP]]
- §5.3.4.2–5.3.4.6 di `Impianti_2026 - 05` · [[_Knowledge Graph v2]] §5.3.4
