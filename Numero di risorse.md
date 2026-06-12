---
aliases:
  - "Saturazione e coefficiente di utilizzazione"
  - "Saturazione e Coefficiente di utilizzazione"
  - "Numero di macchine necessarie"
  - "Numero di macchine (Nj)"
  - "Coefficiente di utilizzazione (Uj)"
  - "Saturazione di linea"
  - "Saturazione macchine"
  - "Saturazione e numero macchine"
  - "Rendimento di produzione"
  - "Andamento dente di sega della saturazione"
  - "Coefficiente di scarto K1"
---
# Numero di risorse

> [!summary] In 10 secondi
> Il primo aspetto della configurazione (§5.2): **quante macchine** servono per i volumi e la varietà richiesti. Si parte dal **rendimento** $\eta = K_1 \cdot K_2 \cdot K_3 \cdot K_4$ (potenzialità effettiva/nominale), si propaga la **cascata degli scarti**, si calcola il **numero teorico** $M'_{ij}$, lo si arrotonda a $M_j$ e si misura l'**utilizzo** $u_j$ e $U$.

## §1 Rendimento di una risorsa
$$\eta = \frac{Q_u}{Q} = K_1 \cdot K_2 \cdot K_3 \cdot K_4 \;<\; 1$$

| Coeff. | Nome | Cosa cattura |
|---|---|---|
| $K_1$ | scarto | difetti + rilavorazioni (tolleranze di lavorazione) |
| $K_2$ | disponibilità | tempo attivo netto guasti/soste/manutenzioni |
| $K_3$ | rendimento operatore | curva di apprendimento, condizioni ambientali |
| $K_4$ | utilizzo | capacità della **programmazione** di mettere la risorsa in condizione di operare |

> [!note] Gemelli dell'OEE
> $K_1 \approx Q$, $K_2 \approx A_p$, $K_3+K_4 \approx E_p \cdot L$: stessa logica dell'[[OEE]], ma in **prospettiva di dimensionamento**.

## §2 Cascata degli scarti ⚠️
A ritroso dal fabbisogno a valle, fra due controlli successivi:
$$Q_{monte} = \frac{Q_{valle}}{\prod_k (1 - p_k)}$$

> [!warning] Scarti in serie MOLTIPLICATIVI
> Non si **sommano** le percentuali. Le risorse comprese **tra due controlli successivi** hanno la stessa potenzialità.

## §3 Numero di macchine
$$M'_{ij} = \frac{Q_{ij}}{(1/T_{ij}) \cdot N_{ij}} \qquad M_j = \left\lceil \sum_i M'_{ij} \right\rceil \qquad u_j = \frac{M'_j}{M_j}$$

- $Q_{ij}$ produzione richiesta · $T_{ij}$ tempo medio effettivo · $N_{ij}$ ore disponibili.
- **Riserva**: con domanda/capacità incerte si può installare $M >$ minimo (fronteggiare guasti).

**Utilizzo della linea**: $U = \dfrac{\sum_j (u_j \cdot M_j)}{\sum_j M_j}$ (variante economica: pesi = costo macchina $C_j$).

## §4 Dente di sega di $u(Q)$ ⚠️
$u$ cresce **lineare** da 0 a 100% fino alla saturazione, poi si aggiunge 1 macchina → **salto in giù** da $M/M$ a $M/(M+1)$, poi risale.
- M=1→2: 100%→50% · M=2→3: 100%→66,7% · M=3→4: 100%→75%…
- ⚠️ L'ampiezza del salto dipende **solo da M**, **non** dalla potenzialità della macchina.

## §5 Collegamenti
- [[Bilanciamento delle linee]] — il secondo aspetto della configurazione (organizzare le risorse)
- [[OEE]] — i coefficienti gemelli K1–K4
- [[Capacità produttiva (CP)]] — il target di volume per cui si dimensiona
- §5.2 di `Impianti_2026 - 05` · [[05 Cap5 - Configurazione dei sistemi di produzione]] · [[_Knowledge Graph v2]] §5.2
