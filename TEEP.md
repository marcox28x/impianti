
**In 10 secondi:** TEEP misura quanta parte del tempo _totale_ in cui ho l'impianto aperto si traduce davvero in produzione conforme — è l'OEE allargato a tutto il tempo di apertura, fermate pianificate incluse.

---

## §1 Domanda fondamentale

> Del tempo durante cui il mio impianto è teoricamente disponibile (cancelli aperti, turni programmati), quanto ne sto effettivamente trasformando in pezzi buoni che il cliente paga?

Mentre l'OEE si chiede _"quando la macchina è caricata, sto sfruttandola bene?"_, il TEEP allarga il campo e include anche le ore in cui ho deciso di **non** caricarla (manutenzione preventiva, mancanza ordini, cambio turno mancato). È la fotografia più severa: rispetto ad essa, ogni altro indice è una "scusa".

---

## §2 Il problema concreto

**Cosmetic Lab S.p.A.** produce rossetti su una linea di riempimento e confezionamento a Crema. L'impianto è in **doppio turno per 5 giorni a settimana, 50 settimane/anno**:

$$ T_A = 2 \cdot 8 \cdot 5 \cdot 50 = 4{.}000 \text{ h/anno} $$

A consuntivo, il direttore di stabilimento ha questi numeri annuali:

- pezzi conformi venduti: **18 milioni** di rossetti
- ritmo standard della linea (di targa): **6.000 pz/h**
- ore in cui la linea era effettivamente accesa e calibrata: **3.400 h** (le restanti 600 h sono manutenzione preventiva, riunioni di reparto e settimane senza ordini)
- ore di guasti + riattrezzaggi: **350 h**
- pezzi totali processati (conformi + scarti + rilavorazioni): **18.900.000**
- scarti: 600.000; rilavorazioni: 300.000

Il direttore commerciale chiede: _"Quanti rossetti in più potremmo davvero produrre senza comprare un'altra linea?"_ Il responsabile produzione mostra l'OEE: **82%**. _"Ottimo,"_ dice il commerciale, _"siamo già al limite."_ Ma il CEO sospetta che 600 ore l'anno di linea spenta siano un margine enorme nascosto.

**Il dilemma:** l'OEE da solo nasconde le perdite di carico — quelle decisioni gestionali (turni, manutenzione, ordini) che riducono $T_C$ rispetto a $T_A$. Per quantificare il vero potenziale serve un indice che parta da $T_A$. Quell'indice è il TEEP.

---

## §3 La definizione

**Definizione formale**

$$ \boxed{;TEEP = \frac{T_{OVA}}{T_A};} $$

dove:

- $T_{OVA}$ = tempo operativo a valore aggiunto (solo produzione conforme)
- $T_A$ = tempo di apertura dell'impianto (l'intero arco temporale in cui l'impianto è accessibile, escluso solo il tempo di chiusura)

**Scomposizione in fattori** — passando attraverso $T_C$, $T_O$, $T_{ON}$ si dimostra che:

$$ TEEP = \frac{T_C}{T_A} \cdot \frac{T_O}{T_C} \cdot \frac{T_{ON}}{T_O} \cdot \frac{T_{OVA}}{T_{ON}} = L \cdot A_p \cdot E_p \cdot Q $$

con:

|Fattore|Nome|Cosa cattura|Tipico|
|---|---|---|---|
|$L$|Efficienza di carico|quanto del $T_A$ viene effettivamente programmato come $T_C$|dipende dall'azienda|
|$A_p$|Disponibilità|quota di $T_C$ in cui la macchina è produttiva (no guasti/setup)|>90%|
|$E_p$|Efficienza prestazioni|velocità reale / velocità di progetto|0.80–0.95 (linea)|
|$Q$|Tasso di qualità|conformi / totale prodotto|95–100%|

---

## §4 Come funziona

**Il cuore in una frase:** il TEEP è una **catena di setacci moltiplicativi** che parte dal tempo totale aperto e filtra via, uno strato alla volta, le ragioni per cui quel tempo non si trasforma in valore.

**Come si connettono i pezzi.** Ogni fattore stacca una fetta di tempo dal precedente:

```
T_A   ──[ ×L  ]──► T_C    perdo qui le fermate pianificate (gestionali)
T_C   ──[ ×Ap ]──► T_O    perdo qui guasti e set-up
T_O   ──[ ×Ep ]──► T_ON   perdo qui rallentamenti e microfermate
T_ON  ──[ ×Q  ]──► T_OVA  perdo qui scarti e rilavorazioni
```

Trattandosi di prodotti, **basta che uno sia basso e il TEEP crolla**: se $L=0{,}50$ il tetto massimo del TEEP è 50%, anche se tutto il resto è perfetto.

**Casi limite e varianti**

- **$L = 1$** → impianto sempre programmato per produrre, mai chiuso ⇒ $TEEP = OEE$. Significa: ho saturato la leva gestionale, ogni miglioramento ulteriore deve venire dal piano operativo.
- **$L < 1$ ma $OEE$ alto** → la linea è efficientissima quando lavora, ma lavora troppo poco. La leva di miglioramento è **commerciale/organizzativa** (più ordini, terzo turno), non tecnica.
- **$OEE$ basso ma $L$ alto** → la linea è sempre programmata, ma quando lavora soffre di guasti, scarti, rallentamenti. La leva è **manutentiva/tecnologica**.

> **Utilità chiave:** noto il $T_A$ e stimato il TEEP, si ricava direttamente $$T_{OVA} = TEEP \cdot T_A$$ che è l'input per calcolare la [[Capacità produttiva (CP)]] reale.

---

## §5 Applicazione pratica

### Formula operativa

$$ TEEP = L \cdot A_p \cdot E_p \cdot Q = \frac{T_{OVA}}{T_A} $$

### Procedura passo-passo

1. **Definisci $T_A$** sulla base del calendario aziendale: ore/turno × turni/giorno × giorni/settimana × settimane/anno. Non confonderlo con $T_S$ (8.760 h) né con $T_C$.
2. **Calcola $L = T_C / T_A$**: dai dati di pianificazione, somma le ore in cui l'impianto era programmato per produrre (escludi manutenzione preventiva, mancanza ordini, scioperi, riunioni).
3. **Calcola $A_p = T_O / T_C$**: usa la formula $A_p = (T_C - t_{guasti} - t_{set\text{-}up})/T_C$. In assenza di dati storici, stima via MTBF/MTTR.
4. **Calcola $E_p$** indirettamente con i tempi standard: $$E_p = \frac{T_S \cdot (Q_{cnf} + Q_{scarti} + Q_{rilav})}{T_O}$$ dove $T_S = 1/P_{std}$ (inverso del ritmo standard).
5. **Calcola $Q$**: $$Q = \frac{Q_{cnf}}{Q_{cnf} + Q_{scarti} + Q_{rilav}}$$
6. **Moltiplica:** $TEEP = L \cdot A_p \cdot E_p \cdot Q$.
7. **Verifica di coerenza:** ricalcola $T_{OVA} = Q_{cnf}/P_{std}$ direttamente e controlla che $T_{OVA}/T_A$ coincida col TEEP appena calcolato. Se non coincide, c'è un errore di dati.

### Checklist anti-errore

- [ ] $T_A$ è in **ore**, non in giorni o turni
- [ ] $T_S$ è in **ore/pezzo**, $P_{std}$ in **pezzi/ora** (uno è l'inverso dell'altro)
- [ ] Le quantità $Q_{cnf}, Q_{scarti}, Q_{rilav}$ sono **annue** se $T_A$ è annuo (coerenza temporale)
- [ ] Tutti i coefficienti sono in $[0, 1]$ (non in percentuale, o convertili)
- [ ] Non sto includendo $T_S$ (tempo solare = 8.760 h) al posto di $T_A$ in $L$
- [ ] Le rilavorazioni, se ignote, sono assunte = 0 ⇒ $\tilde{E_p}$ è **sottostima** e $\tilde{Q}$ è **sovrastima**

---

## §6 Esercizio tipo esame

> **Traccia.** La linea di assemblaggio della Lumière S.r.l. (occhiali da sole, settore moda) ha potenzialità standard $P_{std} = 250$ pz/h. L'azienda lavora su **3 turni × 8 h × 5 gg × 48 settimane = 5.760 h/anno** di tempo di apertura. Da consuntivo annuale risultano:
> 
> - ore di linea programmata e accesa ($T_C$): 4.800 h
> - ore di fermate per guasti e cambi-modello: 460 h
> - occhiali conformi prodotti: 920.000 pz/anno
> - scarti: 35.000 pz; rilavorazioni: 18.000 pz
> 
> **Domande.** (a) Calcola TEEP e OEE. (b) Calcola $T_{OVA}$ per via diretta e per via di TEEP, verificando la coerenza. (c) Se l'azienda eliminasse le settimane di chiusura forzata aumentando $T_C$ a 5.300 h (lasciando invariato tutto il resto in termini di tassi), come cambierebbero TEEP e OEE?

### Soluzione passo-passo

**Step 1 — Efficienza di carico** $$L = \frac{T_C}{T_A} = \frac{4.800}{5.760} = 0{,}833$$

**Step 2 — Disponibilità** $$A_p = \frac{T_C - t_{guasti+setup}}{T_C} = \frac{4.800 - 460}{4.800} = \frac{4.340}{4.800} = 0{,}904$$ quindi $T_O = 4.340$ h.

**Step 3 — Efficienza prestazioni** (con $T_S = 1/250 = 0{,}004$ h/pz) $$E_p = \frac{T_S \cdot (Q_{cnf}+Q_{scarti}+Q_{rilav})}{T_O} = \frac{0{,}004 \cdot (920.000+35.000+18.000)}{4.340} = \frac{3.892}{4.340} = 0{,}897$$ quindi $T_{ON} = 3.892$ h.

**Step 4 — Tasso di qualità** $$Q = \frac{920.000}{920.000+35.000+18.000} = \frac{920.000}{973.000} = 0{,}946$$

**Step 5 — TEEP e OEE** $$TEEP = 0{,}833 \cdot 0{,}904 \cdot 0{,}897 \cdot 0{,}946 = 0{,}639 \approx \mathbf{63{,}9%}$$ $$OEE = A_p \cdot E_p \cdot Q = 0{,}904 \cdot 0{,}897 \cdot 0{,}946 = 0{,}767 \approx \mathbf{76{,}7%}$$

**Step 6 — Verifica di coerenza per $T_{OVA}$**

- Via diretta: $T_{OVA} = Q_{cnf}/P_{std} = 920.000/250 = 3.680$ h
- Via TEEP: $T_{OVA} = TEEP \cdot T_A = 0{,}639 \cdot 5.760 = 3.680$ h ✓

**Step 7 — Interpretazione.** L'OEE del 76,7% è onesto (livello "buono" per una linea di assemblaggio), ma il TEEP del 63,9% mostra che **il 36% del tempo aperto** sta evaporando. Di questo, ben **17 punti percentuali sono perdita di carico** ($1 - L = 16{,}7%$): il vero margine è gestionale prima che tecnico.

### Variante: "e se eliminassi le chiusure forzate?"

Se $T_C$ sale a 5.300 h con $T_A$ invariato e gli stessi tassi $A_p, E_p, Q$:

$$L' = \frac{5.300}{5.760} = 0{,}920 \quad\Rightarrow\quad TEEP' = 0{,}920 \cdot 0{,}904 \cdot 0{,}897 \cdot 0{,}946 = 0{,}706 \approx \mathbf{70{,}6%}$$

**L'OEE non cambia** (76,7%, dipende solo da $A_p, E_p, Q$): è esattamente per questo che da solo non basta. Il TEEP invece sale di quasi 7 punti — la stessa linea, senza investimenti, può produrre il **10,5% in più** di occhiali conformi semplicemente programmandola meglio.

---

## §7 Errori comuni

> [!warning]+ ❌ Confondere TEEP e OEE **Errore:** scrivere $TEEP = A_p \cdot E_p \cdot Q$ (formula dell'OEE) o viceversa. **Perché succede:** entrambi sono prodotti di coefficienti < 1, "sembrano simili". **Come evitarlo:** ricordare la regola dei _quattro vs tre fattori_. TEEP ha **4 fattori** perché include $L$ (parte da $T_A$). OEE ne ha **3** (parte da $T_C$). Mnemonica: TEEP = "Total" → tutto il tempo aperto → include il carico.

> [!warning]+ ❌ Usare $T_S = 8760$ h al posto di $T_A$ **Errore:** calcolare $L = T_C / 8760$ trattando il tempo solare come tempo di apertura. **Perché succede:** confusione nella gerarchia dei tempi. **Come evitarlo:** $T_S$ è solo un riferimento astronomico. $T_A$ è $T_S$ **meno** il tempo di chiusura dello stabilimento (ferie collettive, weekend non lavorati per scelta strutturale). Un impianto su singolo turno 5 gg/sett ha $T_A \approx 2.000$ h, non 8.760.

> [!warning]+ ❌ Dimenticarsi la coerenza temporale tra quantità e tempi **Errore:** calcolare $E_p$ con quantità _mensili_ e $T_O$ _annuo_. **Perché succede:** dati raccolti da fonti diverse (produzione mensile, manutenzione annua). **Come evitarlo:** prima di sostituire nelle formule, scrivere a margine il periodo di riferimento di ogni grandezza. Se i $Q$ sono in pz/mese, anche i tempi devono essere mensili.

---

## §8 Collegamenti

**Prerequisiti** (da padroneggiare _prima_ di TEEP)

- [[Tempo di apertura]] e [[Scomposizione gerarchica dei tempi]] — la sequenza $T_S \to T_A \to T_C \to T_O \to T_{ON} \to T_{OVA}$
- [[Sei grandi perdite (six big losses)]] (six big losses) — guasti, set-up, microfermate, rallentamenti, scarti, rilavorazioni
- [[Efficienza di carico L]], [[Disponibilità Ap]], [[Efficienza prestazioni Ep]], [[Tasso di qualità Q]] — i quattro fattori
- [[Potenzialità produttiva]] e [[Ritmo standard]]

**Conseguenze** (cosa abilita conoscere il TEEP)

- [[OEE — Overall Equipment Effectiveness]] — il "fratello stretto", $OEE = TEEP / L$
- [[Capacità produttiva (CP)]] — la formula $CP = P \cdot T_A \cdot TEEP$ deriva direttamente da qui
- [[Six Big Losses e TPM]] — TEEP è la metrica chiave del Total Productive Maintenance
- Dimensionamento sistemi produttivi — TEEP atteso come input progettuale (Cap4)

---

## §9 Auto-verifica

1. **(base)** Qual è la differenza in una frase tra TEEP e OEE, e quale dei due è "più severo"?
2. **(intermedia)** Un impianto ha $T_A = 4.000$ h, $T_C = 3.200$ h, $A_p = 0{,}9$, $E_p = 0{,}85$, $Q = 0{,}95$. Calcola TEEP a mente (approssimato) e dì quale leva conviene migliorare per prima.
3. **(profonda)** Spiega perché eliminare un turno di lavoro può _aumentare_ l'OEE pur _riducendo_ il TEEP. Cosa significa questo dal punto di vista del management?