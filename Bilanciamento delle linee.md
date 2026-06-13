---
aliases:
  - "Bilanciamento di linea"
  - "Bilanciamento di linea monoprodotto"
  - "Bilanciamento linea monoprodotto"
  - "Bilanciamento multiprodotto"
  - "Bilanciamento linea multiprodotto"
  - "Metodo di Salveson"
  - "Criterio di Salveson"
  - "Criterio di Elmaghraby"
  - "Coefficiente di posizione"
  - "Vincoli di precedenza"
  - "Balance Delay (BD)"
  - "Elemento minimo di lavoro"
  - "Stazioni e fasi"
---
# Bilanciamento delle linee

> [!summary] In 10 secondi
> **Bilanciare** (§5.3) = aggregare le operazioni in **stazioni** in modo che ognuna lavori vicino allo stesso ritmo $TCL$, così che nessuna resti scarica o faccia da collo. Obiettivo: flusso organico, **massima saturazione**, minime scorte. Si misura con il **balance delay** $BD$ (tempo morto totale), da minimizzare → equivale a usare il **minor numero di stazioni**. Due criteri: **Salveson** (per tentativi, *ignora* le precedenze) ed **Elmaghraby** (euristico, *rispetta* le precedenze).

## §0 L'idea di fondo
Immagina una linea come una fila di stazioni, ognuna con a disposizione una "finestra" di durata $TCL$ — il tick con cui i pezzi avanzano. Devi distribuire le operazioni elementari nelle stazioni in modo che:

- nessuna stazione sfori la finestra ($TOP_j \le TCL$, altrimenti diventa collo e cala la produttività);
- il tempo morto complessivo ($BD$) sia minimo, cioè le stazioni siano il più piene possibile.

È un problema di **impacchettamento**: riempire il minor numero di "contenitori" da $TCL$ con i blocchi di lavoro. La differenza fra i due criteri è una sola: **se tieni conto dell'ordine obbligato delle operazioni o no.**

## §1 Parametri e formule (§5.3.1)
| Simbolo | Formula | Significato |
|---|---|---|
| $TCL$ | $TP/Q^*$ = $DT/v$ | tempo di ciclo della linea (il "tick", ritmo richiesto) |
| $TP_i$ | — | tempo dell'**elemento minimo** di lavoro $i$ |
| $TVA$ | $\sum_i TP_i$ | contenuto di lavoro totale |
| $TOP_j$ | $\sum_{i \in j} TP_i \le TCL$ | tempo della stazione $j$ (vincolo di **congruenza**) |
| $TI_j$ | $TCL - TOP_j$ | inattività (tempo morto) della stazione $j$ |
| $BD$ | $\sum_j TI_j = M\cdot TCL - \sum TP_i$ | *balance delay* — quello che voglio **minimizzare** |
| $i$ | $M - \dfrac{\sum TP_i}{TCL}$ (8) | coefficiente di inattività |

**Perché minimizzare $BD$ ⇔ minimizzare $M$.** In $BD = M\cdot TCL - \sum TP_i$ il termine $\sum TP_i$ (contenuto di lavoro) e $TCL$ sono **fissati dal problema**: l'unica leva è $M$. Quindi meno stazioni uso, meno tempo morto ho.

**Numero minimo di stazioni:**
$$M' = \left\lfloor \tfrac{\sum TP_i}{TCL} \right\rfloor + 1 \quad;\quad M'' = \#\{i : TP_i > TCL/2\} \quad;\quad M = \max\{M', M''\}$$

- $M'$ — limite "di volume": non posso comprimere tutto il lavoro in meno contenitori di così.
- $M''$ — limite "di ingombro": due elementi che durano **più di metà** $TCL$ non possono stare nella stessa stazione (sforerebbero); se ce ne sono tanti, è il loro numero a fissare il minimo.

> [!warning] ⚠️ Formula (8) del PDF
> $i = M - \sum TP_i/TCL$ (può anche **superare 1**), **non** $1 - \sum TP_i/(M \cdot TCL)$. Resta vero: poiché $\sum TP_i/TCL$ è costante → **min $i$ ⇔ min $M$**.

## §2 Criterio di Salveson (§5.3.1.2)

### L'intuizione
Salveson tratta il problema in modo "ingenuo ma esaustivo": **prova tutte le partizioni** possibili degli $n$ elementi in stazioni e tiene quella con il $M$ più piccolo che rispetta $TOP_j \le TCL$. Niente furbizie: enumera e confronta.

Ha un difetto strutturale: **non guarda le precedenze**. Lavora come se gli elementi fossero blocchi indipendenti da impacchettare. Funziona se l'ordine delle operazioni è davvero libero; ma appena c'è una sequenza tecnologica obbligata, alcune partizioni "ottime sulla carta" diventano **non eseguibili**, e ti tocca ripiegare su una soluzione peggiore — l'unica fattibile.

### Il procedimento
1. Calcola i due limiti $M'$ e $M''$ → il minimo $M = \max\{M',M''\}$.
2. Cerca **per tentativi** una partizione degli $n$ elementi in $M$ stazioni con $TOP_j \le TCL$ per ognuna.
3. Se la trovi, è ottima ($BD$ minimo). Se le precedenze la rendono impossibile, sali a $M+1$ e ripeti.

> [!warning] Due limiti pratici
> ① L'enumerazione di tutte le partizioni **esplode** al crescere di $n$ (problema combinatorio). ② Le soluzioni "ottime" possono essere **incongruenti** quando esistono vincoli di sequenza.

### Esempio svolto
6 elementi, $TCL = 1{,}00$:

| $i$ | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|
| $TP_i$ | 0,50 | 1,00 | 0,20 | 0,85 | 0,80 | 0,10 |

$\sum TP_i = 3{,}45$.
$M' = \lfloor 3{,}45/1 \rfloor + 1 = 4$ ; $M'' = \#\{TP_i > 0{,}5\} = \#\{2,4,5\} = 3$ → $M = \max\{4,3\} = 4$.

**Caso senza precedenze (ordine libero):** $\{1\}\ \{2\}\ \{3,5\}\ \{4,6\}$
$TOP = 0{,}50 \mid 1{,}00 \mid 1{,}00 \mid 0{,}95$ → $BD = 0{,}50 + 0 + 0 + 0{,}05 = \mathbf{0{,}55}$. **Ottima**, $M=4$.

**Caso con sequenza obbligata $1\to2\to3\to4\to5\to6$:** non posso accorpare 3 con 5 (in mezzo ci sono 4). L'unica partizione fattibile è $\{1\}\ \{2\}\ \{3\}\ \{4\}\ \{5,6\}$
$BD = 0{,}50 + 0 + 0{,}80 + 0{,}15 + 0{,}10 = \mathbf{1{,}55}$, $M=5$.

> [!example] Morale
> La soluzione **sub-ottima** (5 stazioni) diventa **l'unica eseguibile**: ecco perché serve un metodo che parta dalle precedenze → **Elmaghraby**.

## §3 Criterio di Elmaghraby (§5.3.1.2)

### L'intuizione
Elmaghraby risolve il punto debole di Salveson con un'idea semplice: **assegna prima le operazioni che si trascinano dietro più lavoro a valle.**

Pensa al montaggio di una montatura da vista: fissare la **cerniera** è breve, ma da lì dipendono allineamento, inserimento lenti, controllo qualità — tantissimo lavoro le sta "appeso a valle". Se la rimandi, accumuli il lavoro pesante in fondo alla linea e lasci le prime stazioni semivuote. Quindi misuri *"quanto lavoro pende da un'operazione, inclusa l'operazione stessa"*: è il **coefficiente di posizione $KP_i$**.

### Il procedimento
**Passo 0 — Matrice delle precedenze $P$.** $p(h,k)=1$ se $h$ precede $k$ (diretta **o** indiretta, cioè $k$ è raggiungibile da $h$ nel reticolo), altrimenti $0$. ⚠️ I legami **transitivi vanno inclusi**.

**Passo 1 — Coefficiente di posizione.** Per ogni operazione: $KP_i = TP_i + \sum_{k\ \text{successore di }i} TP_k$. In forma compatta (l'identità $I_n$ aggiunge il tempo dell'operazione stessa sulla diagonale):
$$(P + I_n)\cdot TP = KP \qquad (12)$$

**Passo 2 — Ordina $KP$ in senso decrescente** → lista di priorità (13). A parità di $KP$, l'ordine è indifferente.

**Passo 3 — Assegnazione.** Apri la stazione $j=1$ e prendi l'operazione in cima alla lista. Tieni il tempo residuo $TR_j = TCL - \sum TP(\text{assegnati})$ (14). Scendendo nella lista, assegni $k$ a $j$ **se e solo se valgono entrambe:**
- **(i)** $TP_k \le TR_j$ → ci sta nel residuo;
- **(ii)** **tutte** le precedenti di $k$ sono già in stazioni $g \le j$.

Se una non passa, **la salti e provi la successiva**. Quando nessuna operazione rimasta soddisfa (i) e (ii), apri la stazione $j+1$. Fine quando tutte le $n$ sono collocate.

> [!tip] Il punto delicato
> La lista $KP$ dà solo **l'ordine in cui tentare**: non riempi mai alla cieca, **salti e torni indietro** rispettando sempre le precedenze.

### Esempio svolto
$n = 9$, **$TCL = 12$**.

| $i$ | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|---|---|---|---|---|---|---|---|---|---|
| $TP_i$ | 5 | 3 | 4 | 6 | 5 | 3 | 4 | 5 | 3 |
| Precedenti | – | 1 | 1 | 2 | 3 | 2 | 3 | 4,6 | 5,6,7 |

Reticolo (in forma lista):
```
1 → {2, 3}      4 → {8}        7 → {9}
2 → {4, 6}      5 → {9}        8, 9 → finali
3 → {5, 7}      6 → {8, 9}
```

**Calcolo $KP$** (tempo proprio + tutti i successori). Es.: $KP_1 = 5 + (3+4+6+5+3+4+5+3) = 38$ ; $KP_2 = 3+(6+3+5+3)=20$.
$$KP = [\,38,\ 20,\ 16,\ 11,\ 8,\ 11,\ 7,\ 5,\ 3\,] \quad (\text{op. }1\ldots9)$$

**Lista ordinata:** 1(38), 2(20), 3(16), **4(11), 6(11)**, 5(8), 7(7), 8(5), 9(3). Nota: 4 e 6 sono pari → ordine indifferente; 6 viene prima di 5 perché conta il $KP$, non l'indice.

**Traccia di assegnazione:**

| Stazione | Op | $KP$ | Prec. | $TP_i$ | Cumulato | $TR_j$ |
|---|---|---|---|---|---|---|
| **j=1** | 1 | 38 | – | 5 | 5 | 7 |
| | 2 | 20 | 1 | 3 | 8 | 4 |
| | 3 | 16 | 1 | 4 | 12 | **0** |
| **j=2** | 4 | 11 | 2 | 6 | 6 | 6 |
| | 6 | 11 | 2 | 3 | 9 | **3** |
| **j=3** | 5 | 8 | 3 | 5 | 5 | 7 |
| | 7 | 7 | 3 | 4 | 9 | 3 |
| | 9 | 3 | 5,6,7 | 3 | 12 | **0** |
| **j=4** | 8 | 5 | 4,6 | 5 | 5 | 7 |

Il momento che confonde è la **stazione 2**: dopo 4 e 6 il residuo è 3, ma op 5 ($TP=5$) e op 7 ($TP=4$) non ci stanno per (i), e op 9 è bloccata da (ii) perché 5 e 7 non sono ancora collocate. La stazione chiude con 3 di inattività. Specularmente op 9 — il $KP$ più basso — finisce in fondo: poco lavoro a valle = sicura da fare tardi.

**Risultato:** $M = 4$ stazioni → $\{1,2,3\}\mid\{4,6\}\mid\{5,7,9\}\mid\{8\}$.
Verifica: $BD = M\cdot TCL - \sum TP = 4\cdot12 - 38 = \mathbf{10}$ ; coeff. (8): $i = 4 - 38/12 = 0{,}83 = 10/12$ ✓.
Qui Elmaghraby centra anche il minimo teorico $M' = \lfloor 38/12\rfloor + 1 = 4$ — non sempre garantito (è un'**euristica**), ma in questo caso tocca il limite inferiore.

## §4 Salveson vs Elmaghraby — quando usarli
| | **Salveson** | **Elmaghraby** |
|---|---|---|
| Precedenze | ignorate | rispettate (matrice $P$) |
| Metodo | enumera tutte le partizioni | euristica greedy su $KP$ |
| Garanzia | ottimo *se* l'ordine è libero | buona soluzione, non sempre ottima |
| Limite | esplode con $n$; incongruente con sequenze | dipende dall'ordine di $KP$ |
| Quando | cicli con poche/nessuna precedenza | linee reali con vincoli di sequenza |

## §5 Collegamenti
- [[Numero di risorse]] — $M'$, $M''$ e i coefficienti $K_1\ldots K_4$ a monte del bilanciamento
- [[Collo di bottiglia]] · [[Potenzialità di mix]] — la stazione più lenta determina la potenzialità della linea
- [[Legge di Little e WIP]] · [[Curve logistiche operative]] — dopo il bilanciamento: scorte interoperazionali e WIP
- [[Criterio di Vladzyevsky]] — numero ottimo di magazzini intermedi
- [[Flow shop]] · [[Layout a celle]] — dove il bilanciamento è rilevante
- §5.3.1 di `Impianti_2026 - 05` · [[05 Cap5 - Configurazione dei sistemi di produzione]] · [[_Knowledge Graph v2]] §5.3.1
