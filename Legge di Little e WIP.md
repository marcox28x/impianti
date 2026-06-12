---
aliases:
  - "WIP"
  - "WIP - Work In Process"
  - "Buffer interoperazionali"
  - "Scorte interoperazionali"
  - "Magazzini interoperazionali"
---
# Legge di Little e WIP

> [!summary] In 10 secondi
> Il **WIP** (*Work In Process*) è la quantità di materiali presenti **nel processo** in attesa delle lavorazioni successive. La **legge di Little** ($WIP = P \cdot TA$) lega WIP, potenzialità e tempo di attraversamento: una sola equazione in tre incognite, usata come **check di coerenza** e base delle **curve logistiche operative**.

## §1 WIP e WIP critico (§5.3.4)
- **WIP** influenza: ① l'alimentazione delle stazioni (no starving/blocking) ② i tempi di attraversamento.
- **$WIP_c$** (WIP **critico**) ≔ il valore di WIP per cui la linea produce **al ritmo più alto** ($P = P_b$, potenzialità del collo) **e** con **TA minimo** ($TA = TVA$). È il punto di massima efficienza delle scorte circolanti.

$$WIP_c = P_b \cdot TVA \qquad (30)$$

> [!warning] ⚠️ $WIP_c$ = numero di macchine?
> Solo se la linea è **bilanciata con 1 macchina per stazione**. Se non bilanciata → $WIP_c <$ n. macchine. Se $WIP_c$ non è intero → **nessun** $w$ garantisce contemporaneamente $P_b$ e $TVA$.

## §2 Legge di Little (1961)
$$\boxed{\;WIP = P \cdot TA\;} \qquad (29)$$

> [!warning] ⚠️ $P \neq 1/TA$ in generale
> Vale solo per macchina isolata **senza starving** (polmone a monte mai vuoto) e **senza blocking** (polmone a valle mai pieno). I buffer (WIP) **allungano** il TA: es. macchina in linea con polmone d'ingresso da 2 semilavorati → $TA = 30''+30''+1/P = 90''$.

Una equazione, tre incognite → infinite coppie $(P, TA)$ per ogni WIP → si usano le **curve logistiche operative** (Hopp & Spearman): caso **migliore**, **peggiore**, **massima casualità** (vedi [[_Knowledge Graph v2]] §5.3.4).

## §3 Diagramma di throughput
Due cumulate del contenuto di lavoro nel tempo (in **ingresso** e in **uscita**):
- $TA$ = distanza **orizzontale** fra le cumulate · $WIP$ = distanza **verticale** · $P$ = **pendenza**.

## §4 Logiche a cartellino (WIP costante)
- **KANBAN** (看板, cartellino): su **contenitore**, applicato alla **singola macchina**; n. cartellini limitato → controllo del flusso in tempo reale [tipico del Just in Time].
- **CONWIP** (*CONstant WIP*): cartellino agganciato al **pezzo** per l'**intera linea**; entrano solo pezzi col cartellino → $WIP$ = n. cartellini.

## §5 Esempio Gagghi Anchia
$P=71{,}8$ pz/h, $TA=663$ h, $P_b=114$, $TVA=34$ h → $WIP_c = 114 \cdot 34 = 3876$. Little: $WIP = 71{,}8 \cdot 663 \approx 47.600$ ✓ (coerente col misurato). $P/P_{maxcas}=68\%$, $WIP \sim 7{,}4\times$ il necessario → impianto in **area negativa**, ampi margini di miglioramento.

## §6 Collegamenti
- [[Bilanciamento delle linee]] — precede il dimensionamento delle scorte
- [[Tempo di attraversamento]] · [[Potenzialità produttiva]] — le altre due variabili di Little
- [[Job shop]] — alto WIP/TA per programmazione difficile
- §5.3.4 di `Impianti_2026 - 05` · [[05 Cap5 - Configurazione dei sistemi di produzione]] · [[_Knowledge Graph v2]] §5.3.4
