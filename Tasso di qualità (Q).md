# Tasso di qualità (Q)

> In 10 secondi: Q è la frazione di pezzi conformi sul totale di tutti i pezzi che la macchina ha lavorato (conformi + scarti + rilavorati). È il terzo fattore di OEE e dice "di tutto quello che ho prodotto, quanto era davvero vendibile?".

---

## §1 Domanda fondamentale

**Dei pezzi che la mia macchina ha fisicamente lavorato, quanti erano "buoni al primo colpo"?**

Cioè: quanti sono usciti conformi senza dover essere scartati e senza dover essere ripresi in mano per essere sistemati. È un indicatore puro di qualità, indipendente da quanto la macchina sia veloce ([[Efficienza prestazioni (Ep)]]) o da quanto tempo sia stata disponibile ([[Disponibilità (Ap)]]).

---

## §2 Il problema concreto

**Luxottica-style: stabilimento di lenti per occhiali da sole ad Agordo.**

Una linea di stampaggio a iniezione di lenti in policarbonato lavora 22 giorni al mese, 16 h/giorno. Lo standard è 200 lenti/ora.

A fine mese il responsabile di linea raccoglie i dati:
- Lenti **conformi** spedite al reparto trattamento antiriflesso: **52.800**
- Lenti **scartate** (bolle d'aria nello stampaggio, graffi, deformazioni): **2.400**
- Lenti **rilavorate** (lieve sbavatura sul bordo → ripassate al rifilo manuale e poi rientrate in linea): **1.800**

Il direttore di stabilimento gli chiede: *"Qual è il nostro tasso di qualità?"*

Il dilemma: il caporeparto è tentato di dire "facile, 52.800 conformi su 55.200 (conformi + scarti) → 95,7%". Ma questa risposta **dimentica le 1.800 lenti rilavorate**, che pure hanno occupato la macchina per essere prodotte la prima volta sbagliate. Se le includiamo, il Q reale scende a 52.800 / 57.000 = **92,6%**.

Tre punti percentuali di differenza che, su scala annua, valgono migliaia di euro di costo nascosto.

---

## §3 La definizione

**Definizione formale:**

$$Q = \frac{TOVA}{TON} = \frac{\text{tempo operativo a valore aggiunto}}{\text{tempo operativo netto}}$$

Operativamente, traducendola in pezzi (assumendo tempo standard $T_{std}$ uguale per tutti):

$$Q = \frac{T_{std} \cdot Q_{cnf}}{T_{std} \cdot Q_{cnf} + T_{std} \cdot Q_{scarti} + T_{std} \cdot Q_{rilav}} = \frac{Q_{cnf}}{Q_{cnf} + Q_{scarti} + Q_{rilav}}$$

**Scomposizione in parti:**

| Componente | Cosa rappresenta | Dove va a finire |
|---|---|---|
| $Q_{cnf}$ (numeratore) | Pezzi conformi al primo passaggio | Vendita / fasi a valle |
| $Q_{scarti}$ (al denom.) | Pezzi prodotti **e poi buttati** | Rottame / rifiuto |
| $Q_{rilav}$ (al denom.) | Pezzi prodotti male **e poi sistemati** | Rientrano in linea, ma hanno "pesato" due volte sulla macchina |

Il numero è puro (adimensionale), tipicamente **95–100%**. Valori più bassi sono spia di problemi su: condizione macchina (manutenzione, parametri ambientali), conduzione (operatore, parametri operativi), o materiali in ingresso (qualità approvvigionamenti).

---

## §4 Come funziona

**Il cuore:** Q misura quanta della capacità produttiva "vera e propria" della macchina è andata a finire in prodotto vendibile. Tutto il resto — scarti che butti, rilavorazioni che devi rifare — è capacità sprecata anche se la macchina, di per sé, stava girando.

**Connessione con le parti:** il denominatore $(Q_{cnf} + Q_{scarti} + Q_{rilav})$ rappresenta **tutto ciò che la macchina ha materialmente prodotto** durante il [[Quadro sinottico tempi|Tempo operativo netto (TON)]]. Il numeratore è solo la fetta "buona". Le rilavorazioni sono al denominatore perché **la prima volta che le hai prodotte male, la macchina era occupata** — quel tempo lo paghi.

**Casi limite e varianti — il problema delle rilavorazioni ignote:**

In azienda spesso i dati di scarto sono ben tracciati (vanno in un cassone, si pesano) ma le **rilavorazioni no**: il pezzo torna indietro informalmente, viene risistemato e nessuno lo registra. In questo caso si è costretti a stimare:

$$\tilde{Q} = \frac{Q_{cnf}}{Q_{cnf} + Q_{scarti}}$$

> ⚠️ Questa è una **stima per eccesso**: il denominatore è più piccolo del reale, quindi $\tilde{Q} > Q_{reale}$.

**Compensazione magica con OEE:** se non conosci le rilavorazioni, anche $\widetilde{E_p}$ risulta sbagliata, ma **per difetto** (denominatore della formula di $E_p$ implicito nel calcolo). I due errori si compensano esattamente, quindi:

$$\widetilde{E_p} \cdot \tilde{Q} = E_p \cdot Q$$

→ **l'[[OEE]] rimane corretto anche se non sai nulla sulle rilavorazioni.** Comodo, ma pericoloso: se guardi solo Q ed Ep separatamente, ti illudi.

---

## §5 Applicazione pratica

### Formula da ricordare

$$\boxed{Q = \frac{Q_{cnf}}{Q_{cnf} + Q_{scarti} + Q_{rilav}}}$$

### Passo-passo per calcolarla

1. **Definisci il periodo** (mese, anno, turno). Tutti i dati devono riferirsi allo stesso intervallo.
2. **Recupera $Q_{cnf}$**: quantità di prodotto conforme uscito dalla linea (ufficio spedizioni / passaggio al reparto successivo).
3. **Recupera $Q_{scarti}$**: quantità scartata definitivamente (registri di rottamazione / cassone scarti).
4. **Recupera $Q_{rilav}$**: quantità rilavorata. ⚠️ Questo è il dato più rognoso: verifica se l'azienda lo traccia davvero.
5. **Verifica omogeneità unità di misura** (kg con kg, pezzi con pezzi).
6. **Applica la formula** e leggi il risultato come percentuale.
7. **Confronta** con il range atteso (95–100%): se sei sotto, indaga le cause (macchina/operatore/materiali).

### Checklist anti-errore

- [ ] Le quantità sono **tutte** nella stessa unità di misura?
- [ ] Le quantità si riferiscono **allo stesso periodo**?
- [ ] Ho davvero il dato sulle rilavorazioni? Se no, sto chiamando $\tilde{Q}$ come $Q$? Lo segnalo?
- [ ] I "pezzi rilavorati e poi conformi" li sto contando **sia** in $Q_{cnf}$ (versione finale buona) **sia** in $Q_{rilav}$ (passaggio iniziale fallito)?
- [ ] Sto presentando Q come % e non come numero puro 0,xxx ambiguo?

---

## §6 Esercizio tipo esame

**Traccia** — *Lentech S.p.A., produzione monture in acetato.*

Lentech produce montature per occhiali da vista in acetato di cellulosa. La linea di fresatura CNC lavora 250 giorni all'anno su due turni da 8 ore. La produttività standard è 60 montature/ora.

Nel corso dell'anno si è registrato:
- Produzione conforme: **420.000** montature
- Scarti (montature con crepe o difetti di colorazione non recuperabili): **18.000**
- Rilavorazioni (montature con sbavature minori, ripassate alla levigatura): **24.000**

Il tempo operativo netto effettivo è stato di **7.700 ore**.

**Domande:**
1. Calcolare il tasso di qualità Q.
2. Calcolare la stima $\tilde{Q}$ che si otterrebbe ignorando le rilavorazioni e commentare la direzione dell'errore.
3. Calcolare l'efficienza delle prestazioni $E_p$ e verificare la compensazione $\widetilde{E_p} \cdot \tilde{Q} = E_p \cdot Q$.

### Soluzione passo-passo

**(1) Q reale:**

$$Q = \frac{420.000}{420.000 + 18.000 + 24.000} = \frac{420.000}{462.000} = 90{,}91\%$$

Sotto la soglia tipica 95–100% → segnale che qualcosa non va (forse materia prima di qualità incostante o operatori in apprendimento).

**(2) Stima $\tilde{Q}$ ignorando le rilavorazioni:**

$$\tilde{Q} = \frac{420.000}{420.000 + 18.000} = \frac{420.000}{438.000} = 95{,}89\%$$

→ La stima è **per eccesso** di circa 5 punti percentuali. Il manager che vede 95,9% si illude di essere "nella norma", mentre il valore vero (90,9%) avrebbe acceso una luce rossa.

**(3) Efficienza delle prestazioni:**

Tempo standard per montatura: $1/60 = 0{,}01\overline{6}$ h/pz.

Tempo standard per produrre **tutto** (conformi + scarti + rilavorazioni):

$$TON_{std} = \frac{1}{60} \cdot (420.000 + 18.000 + 24.000) = \frac{462.000}{60} = 7.700 \text{ h}$$

$$E_p = \frac{TON_{std}}{TON_{reale}} = \frac{7.700}{7.700} = 100\%$$

Stima ignorando rilavorazioni:

$$\widetilde{E_p} = \frac{1/60 \cdot (420.000 + 18.000)}{7.700} = \frac{7.300}{7.700} = 94{,}81\%$$

**Verifica compensazione:**
- Prodotto reale: $E_p \cdot Q = 1{,}0000 \cdot 0{,}9091 = 0{,}9091$
- Prodotto stimato: $\widetilde{E_p} \cdot \tilde{Q} = 0{,}9481 \cdot 0{,}9589 = 0{,}9091$ ✓

I due errori si compensano esattamente: l'OEE è invariante rispetto alla nostra ignoranza sulle rilavorazioni.

### Variante: *"E se cambiasse X?"*

**E se Lentech investisse in un sistema di visione artificiale che dimezza gli scarti** (da 18.000 a 9.000), senza toccare le rilavorazioni?

$$Q_{nuovo} = \frac{420.000}{420.000 + 9.000 + 24.000} = \frac{420.000}{453.000} = 92{,}71\%$$

Guadagno: +1,8 punti percentuali. Modesto, perché il vero problema sono le rilavorazioni (24k), non gli scarti (9k). Lezione: prima di investire, **guarda dove pesa di più la perdita** nel denominatore.

---

## §7 Errori comuni

> [!warning] ❌ Errore 1 — Confondere $Q$ con "% di pezzi venduti"
> Q non c'entra con quanto vendi sul mercato. È un indicatore **interno** di linea: quanti pezzi sono usciti conformi alla prima rispetto a tutti i pezzi prodotti dalla macchina. Un pezzo conforme che resta a magazzino invenduto è comunque "buono" per Q.
> **Come evitarlo:** ricorda la definizione tempo-based: $Q = TOVA/TON$. È un rapporto tra tempi, non tra fatturati.

> [!warning] ❌ Errore 2 — Mettere le rilavorazioni al numeratore (perché "alla fine sono conformi")
> Le rilavorazioni vengono **risistemate** e diventano conformi, ma il tempo macchina della **prima** produzione fallita resta perso. La macchina è stata occupata a fare un pezzo difettoso → quel tempo va al denominatore, non al numeratore.
> **Come evitarlo:** pensa al denominatore come "tutto ciò che ha occupato la macchina la prima volta", non come "tutto ciò che è uscito dal magazzino conforme".

> [!warning] ❌ Errore 3 — Concludere che $\tilde{Q}$ alto = qualità ottima
> Se non hai dati sulle rilavorazioni, $\tilde{Q}$ è una **stima per eccesso**. Un 97% calcolato senza rilavorazioni può corrispondere a un Q reale del 90%. Idem al contrario: $\widetilde{E_p}$ è per difetto.
> **Come evitarlo:** prima di dichiarare un Q, verifica se le rilavorazioni sono tracciate. Se no, dichiaralo esplicitamente come stima e accompagnalo con OEE (che è invariante).

---

## §8 Collegamenti

**Cosa devo sapere prima (prerequisiti):**
- [[03 Cap3 - Prestazioni]] (MOC)
- [[Quadro sinottico tempi]] — Q opera tra TON e TOVA
- [[Sei grandi perdite (six big losses)]] — Q copre le ultime due (scarti, rilavorazioni)
- [[Scarti, rilavorazioni e sfridi]] — distinzione tipologica

**Cosa ne consegue (dipendenze):**
- [[OEE]] — Q è uno dei tre fattori: $OEE = A_p \cdot E_p \cdot Q$
- [[TEEP]] — Q è uno dei quattro fattori: $TEEP = L \cdot A_p \cdot E_p \cdot Q$
- [[Capacità produttiva (CP)]] — Q entra nel calcolo della CP reale via OEE/TEEP
- [[Efficienza prestazioni (Ep)]] — gemello di Q nella compensazione errori
- [[Potenzialità di mix]] — quando si hanno più prodotti con qualità diverse

**Concetti correlati per contrasto:**
- [[Disponibilità (Ap)]] — Ap misura *quando* la macchina è disponibile; Q misura *cosa* esce di buono mentre lavora
- [[Efficienza di carico (L)]] — L è scelta gestionale; Q è dato tecnico-operativo

---

## §9 Auto-verifica

1. **(Base)** Una linea produce 800 pezzi conformi, 40 scartati, 60 rilavorati in un mese. Quanto vale Q?
   *(Risposta attesa: 800 / 900 = 88,9%)*

2. **(Intermedia)** Perché, se non conosco le rilavorazioni, la stima $\tilde{Q}$ è per eccesso mentre $\widetilde{E_p}$ è per difetto? Spiega l'asimmetria guardando dove compaiono le rilavorazioni nelle due formule.

3. **(Profonda)** Un'azienda mi mostra OEE = 78% e dice "non sappiamo separare scarti da rilavorazioni, ma il dato OEE è solido". Posso fidarmi del 78%? E se mi dicesse "abbiamo Q = 97%" senza distinguere scarti da rilavorazioni? Quale dei due dati richiede più cautela e perché?