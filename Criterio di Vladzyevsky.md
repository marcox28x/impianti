---
aliases:
  - "Magazzini interoperazionali"
---
# Criterio di Vladzyevsky

> [!summary] In 10 secondi
> Il criterio di **Vladzyevsky** (§5.3.3) determina il **numero ottimo di magazzini interoperazionali** $MG^*$ lungo una linea. Più settori → meno propagazione delle avarie e migliore impiego dei tempi morti, ma più costi di movimentazione. L'ottimo bilancia i due effetti.

## §1 Perché i magazzini interoperazionali (§5.3.2)
Oltre al bilanciamento, due esigenze:
1. **sfruttare** la potenzialità non usata nei tempi di inattività ($TI_j$ → produzione);
2. **contenere** la propagazione delle avarie locali sull'intero flusso.

Tipi di scorta: **operativa** (WIP, bilancia i ritmi → no starving/blocking, vedi [[Legge di Little e WIP]]) e **di sicurezza** (copre il fabbisogno in caso di guasto, dimensionata sulla probabilità).

## §2 Le formule
Rendimento (impiego tecnico) della linea:
$$\eta = \frac{1}{1 + I}$$

Con $MG$ settori e aliquota $\delta$ trasferita a valle (↓ al crescere delle scorte), più movimentazione $I_M$:
$$I = \frac{\bar{I}}{MG}(1 + \delta) + I_M(MG - 1)$$

**Ottimo** ($dI/dMG = 0$):
$$\boxed{\; MG^* = \sqrt{\frac{\bar{I}}{I_M}\,(1 + \delta)} \;}$$

## §3 Lettura
- $\bar{I}/I_M$ **grande** (linea molto "inattiva", movimentazione economica) ⇒ **molti** settori, al limite un deposito a monte di **ogni** stazione.
- $\delta \to 0$ quando le scorte → ∞ (un magazzino capiente disaccoppia totalmente i settori).

## §4 Collegamenti
- [[Legge di Little e WIP]] — l'entità delle scorte operative (WIP)
- [[Bilanciamento delle linee]] — il bilanciamento riduce i $TI_j$ da "riempire"
- §5.3.2–5.3.3 di `Impianti_2026 - 05` · [[05 Cap5 - Configurazione dei sistemi di produzione]] · [[_Knowledge Graph v2]] §5.3.3
