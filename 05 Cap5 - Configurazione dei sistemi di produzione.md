

## Domanda del capitolo
**Quante risorse servono per i volumi richiesti, e come le organizzo (stazioni, magazzini, WIP) perché la linea scorra al ritmo giusto senza tempi morti né scorte inutili?**

## Mini-riassunto
Due aspetti (§5.1): **① numero di risorse** (§5.2) e **② organizzazione delle risorse** (§5.3). Per il numero: rendimento $\eta = K_1 K_2 K_3 K_4$, cascata degli scarti (moltiplicativi!), numero teorico $M'_{ij}$, arrotondamento $M_j = \lceil \Sigma M'_{ij} \rceil$, utilizzo $u_j$ e $U$ di linea, con $u(Q)$ a **dente di sega**. Per l'organizzazione: **bilanciamento** della linea monoprodotto (aggregare gli elementi minimi in $M = \max\{M', M''\}$ stazioni con $TOP_j \le TCL$, minimizzando il balance delay) coi criteri di **Salveson** (senza precedenze) ed **Elmaghraby** (euristica con $KP$); poi i **magazzini interoperazionali** (numero ottimo con **Vladzyevsky**) e l'**entità del WIP**: legge di **Little** ($WIP = P \cdot TA$), $WIP_c = P_b \cdot TVA$, diagramma di throughput, kanban/CONWIP e le tre **curve logistiche operative** (caso migliore, peggiore, massima casualità).

## Concetti trattati

### 5.2 La determinazione del numero di risorse
- [[Numero di risorse]] — η = K1·K2·K3·K4, cascata degli scarti, M′ij / Mj / uj / U
- [[Numero di risorse|Andamento dente di sega della saturazione]] — salti da M/M a M/(M+1), dipendono solo da M
- [[Capacità produttiva (CP)]] — il target di volume a monte del dimensionamento

### 5.3 Il bilanciamento delle linee (5.3.1 linea monoprodotto)
- [[Bilanciamento delle linee]] — elementi minimi, TCL, TOPj ≤ TCL, TIj, balance delay, M′/M″
- [[Bilanciamento delle linee|Criterio di Salveson]] (§5.3.1.1) — per tentativi, ignora le precedenze
- [[Bilanciamento delle linee|Criterio di Elmaghraby]] (§5.3.1.2) — euristica con KP = (P+Iₙ)·TP
- [[Collo di bottiglia]] — la stazione a potenzialità minima fissa Pb e TCL

### 5.3.2–5.3.3 Giacenze interoperazionali e numero di magazzini
- [[Criterio di Vladzyevsky]] — scorta operativa vs di sicurezza; $\text{MG*} = \sqrt{(Ī/I_M)(1+δ)}$

### 5.3.4 Entità delle scorte operative (WIP)
- [[Legge di Little e WIP]] — WIP = P·TA, WIPc = Pb·TVA, diagramma di throughput, kanban/CONWIP, esempio Gagghi Anchia
- [[Curve logistiche operative]] — caso migliore / peggiore / massima casualità; aree positiva/negativa; impianto non bilanciato (§5.3.4.5); incremento prestazioni (§5.3.4.6)

## Formule da ricordare a memoria
- $\eta = K_1 \cdot K_2 \cdot K_3 \cdot K_4$ · cascata scarti: $Q_{monte} = Q_{valle} / \prod_k(1-p_k)$
- $M'_{ij} = \dfrac{Q_{ij}}{(1/T_{ij}) \cdot N_{ij}}$ ; $M_j = \lceil \Sigma_i M'_{ij} \rceil$ ; $u_j = M'_j / M_j$ ; $U = \dfrac{\Sigma_j u_j M_j}{\Sigma_j M_j}$
- $TCL = TP/Q^* = DT/v$ · $TOP_j \le TCL$ · $BD = \Sigma_j (TCL - TOP_j)$
- $i = M - \dfrac{\Sigma TP_i}{TCL}$ (8) ⚠️ forma del PDF, può superare 1
- $M' = \lfloor \Sigma TP_i / TCL \rfloor + 1$ ; $M'' = \#\{TP_i > TCL/2\}$ ; $M = \max\{M', M''\}$
- Elmaghraby: $(P + I_n) \cdot TP = KP$ (12)
- Vladzyevsky: $MG^* = \sqrt{(\bar I / I_M)(1+\delta)}$ (28)
- Little: $WIP = P \cdot TA$ (29) · $WIP_c = P_b \cdot TVA$ (30)
- Massima casualità: $TA = TVA + \dfrac{w-1}{P_b}$ (40) · $P = \dfrac{w \cdot P_b}{WIP_c + w - 1}$ (41)

## Punti chiave per l'esame
- Scarti in serie **moltiplicativi** (mai sommare le %); risorse tra due controlli → stessa potenzialità.
- Il salto del dente di sega dipende **solo da M**, non dalla potenzialità della macchina.
- ⚠️ Formula (8): $i = M - \Sigma TP_i/TCL$, **non** $1 - \Sigma TP_i/(M \cdot TCL)$; min $i$ ⇔ min $M$.
- Salveson **non gestisce le precedenze**: con sequenza obbligata la soluzione ottima può diventare infeasible (es. 4→5 stazioni).
- Elmaghraby: la matrice P include i legami **transitivi**; condizione doppia (tempo residuo **e** predecessori in $g \le j$).
- $P \ne 1/TA$ in generale (solo senza starving/blocking): il legame vero è **Little** → check di coerenza dei dati.
- $WIP_c$ = numero di macchine **solo** se linea bilanciata con 1 macch/stazione; non bilanciata → $WIP_c <$ n. macchine.
- Il collo **non** è né la stazione con meno macchine né quella col tempo maggiore (es. §5.3.4.5).
- Il caso **peggiore è deterministico** (lotti); la massima casualità è il "caso pratico peggiore".
- Potenziare il collo ↑Pb (costoso, WIP invariato); potenziare i non-colli ↓TVA → ↓WIPc (meglio per piccoli WIP).

> [!warning] Fuori programma 2026
> Kilbridge-Wester, Hoffmann e COMSOAL **non sono più nel testo** (restano solo Salveson ed Elmaghraby). Il "bilanciamento multiprodotto" come sezione a sé **non esiste nel PDF 2026**: il §5.3.1 tratta la sola linea monoprodotto; il caso multiprodotto compare solo di passaggio (cause reali dei lotti nel caso peggiore, §5.3.4.3).

## Collegamenti
- ← [[04 Cap4 - Progettazione dei sistemi di produzione]]: ciclo di lavorazione e tempi (gli elementi minimi TPi) arrivano da qui
- ← [[03 Cap3 - Prestazioni dei sistemi di produzione]]: K1–K4 gemelli di OEE/L; TA/TVA/TCL stesso linguaggio
- → [[06 Cap6 - Layout e flussi di materiali]]: Mj, stazioni e magazzini interoperazionali si dispongono nello spazio
