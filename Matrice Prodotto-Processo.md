# Matrice Prodotto-Processo

> [!summary] In 10 secondi
> La **Matrice Prodotto-Processo** (§2.2, Figura 6) è la **sintesi del Cap2**: incrocia le caratteristiche del **mercato/prodotto** (mix × volumi, da *specialty* a *commodity*) con la **continuità del flusso produttivo** (da frammentario a continuo). Lungo la **diagonale** stanno le configurazioni **fisiologiche** (coerenti); fuori diagonale le **patologie** (oneri ingiustificati o opportunità perse).

## §1 Domanda fondamentale
Le classificazioni del Cap2 (prodotti, CODP, soluzioni impiantistiche, volumi) non sono indipendenti. **Quale soluzione impiantistica è "naturale" per un dato tipo di prodotto/mercato?** E cosa succede quando si sceglie quella sbagliata?

## §2 Gli assi
- **Asse mercato/prodotto** (verticale): dall'**esemplare unico e irripetibile** (*specialty*) → attraverso progressiva standardizzazione e crescita dei volumi → alla **commodity** (prodotto generico, grandi volumi).
- **Asse flusso produttivo** (orizzontale): da **frammentario** → a crescente **continuità** e **automazione**.

## §3 La diagonale fisiologica
Le realtà coerenti giacciono lungo la diagonale dal vertice alto-sinistra al basso-destra:

| Mercato/prodotto | Flusso | Soluzione fisiologica | Risposta domanda |
|---|---|---|---|
| Specialty, esemplare unico | Frammentario | [[Job shop]] | ETO / PTO |
| Volumi ↑, flussi quasi lineari | Discontinuo lineare | [[Group technology]] | MTO |
| Volumi alti | Lineare | [[Flow shop]] a lotti | ATO |
| Commodity, grandi volumi | Continuo automatizzato | Impianti di **processo** | MTS (su previsioni) |

→ Lungo la diagonale la modalità di risposta passa da **MTS** (continuo, alto volume, standardizzato) verso **ATO → MTO → PTO → ETO** (massima personalizzazione, quantità limitata). Vedi [[CODP - Customer Order Decoupling Point]].

## §4 Le patologie (fuori diagonale) ⚠️
Nei vertici **opposti** alla diagonale stanno collocazioni incoerenti, con sintomi di **oneri ingiustificati** (maggiori costi effettivi o perdita di opportunità):

> [!warning] Patologia 1 — Processo continuo per gamma ampia a bassi volumi
> Si chiede a un processo continuo di lavorare molti prodotti diversi in volumi contenuti → **fermi macchina, set-up, maggiori scarti, minore saturazione**.

> [!warning] Patologia 2 — Grandi volumi omogenei su attrezzature generiche
> Si producono grandi volumi di prodotto omogeneo con macchine general-purpose → si **rinuncia** ai vantaggi di efficienza e capacità produttiva.

## §5 Lettura dinamica
Le tipologie sono **archetipi dell'iter di sviluppo** di un sistema produttivo. Spostandosi lungo la diagonale da **job shop → flow shop** cambiano in modo sistematico prodotto, processo, materiali, manodopera e organizzazione (i "trend" del §2.2):

- **Prodotto**: ↓ numero prodotti diversi · ↑ volumi unitari (→ commodity) · ↓ personalizzazione · ↑ standardizzazione · industrializzazioni meno frequenti.
- **Processo**: ↑ rigidità · macchinari specifici · economie di scala · capital intensive · bilanciamento più facile · colli di bottiglia stabili.
- **Materiali**: distinte più stabili · ↓ WIP · ↑ scorte PF · ↑ integrazione verticale.
- **Manodopera**: ↓ contenuto di lavoro/output · ↓ varietà mansione · incentivi da individuali → di squadra/aziendali.
- **Organizzazione**: funzioni in staff (materiali, qualità, metodi, scheduling) · ↑ (impiegati+indiretti)/(diretti).

## §6 Collegamenti
### Sintetizza
- [[Job shop]] · [[Group technology]] · [[Flow shop]] — le soluzioni sulla diagonale
- [[Classificazione per processi tecnologici]] — per processo vs per parti
- [[CODP - Customer Order Decoupling Point]] — la risposta alla domanda lungo la diagonale
- [[Classificazione dei prodotti]] — mix e volumi sull'asse mercato

### Trade-off correlato
- [[Analisi CVP]] — il confronto economico processo vs prodotto (volume critico $q^*$)
- flessibilità ↔ efficienza è il trade-off che la matrice rende geometrico

### Vedi anche
- §2.2 e Figura 6 di `Impianti_2026 - 02` · [[02 Cap2 - Classificazione dei sistemi di produzione]] · [[_Knowledge Graph v2]] §2.2
