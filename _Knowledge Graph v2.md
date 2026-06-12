# IMPIANTI INDUSTRIALI — Knowledge Graph v2

> Sintesi maestra compressa del corso. Formato: outline denso + notazione logica.
> Simboli: `→` causa/conseguenza · `⊂` sottoinsieme · `⇔` equivalenza · `∧` and · `∨` or ·
> `∈` appartiene · `{…}` set · `⚠️` trappola d'esame.
> La numerazione delle sezioni segue **esattamente** quella dei PDF `Impianti_2026__01…06`.
> Questo file NON sostituisce i PDF per esempi numerici dettagliati e figure. Mappa d'ingresso → [[index]] · navigazione → [[00 Impianti - MOC]].

---

## §0 META — Struttura documento
```
Cap1 Introduzione ai sistemi di produzione        [18 pp]
Cap2 La classificazione dei sistemi di produzione [17 pp]  (adatt. Sianesi 2011)
Cap3 Le prestazioni dei sistemi di produzione     [22 pp]
Cap4 La progettazione dei sistemi di produzione   [23 pp]
Cap5 La configurazione dei sistemi di produzione  [31 pp]
Cap6 Il layout dei sistemi di produzione          [37 pp]  (adatt. De Carlo; Pareschi et al.)
Cap7 — RIMOSSO dai PDF 2026 (impianti di servizio non più nel materiale)
```
Mappa argomenti → capitolo·sezione:
- definizioni base, gerarchia, pianificazione → §1.1
- contesto, economie scala/scopo, VRP, cicli di vita, ubicazione, metodo del punteggio → §1.2–1.3
- classificazione prodotti, CODP/MTS…ETO, job/GT/flow, lavoro, volumi, matrice P-P → §2
- efficacia/efficienza, flessibilità, servizio, P, TA, IF, Pmix, OEE/TEEP, CP → §3
- occasioni/dimensioni/articolazione progetto, archivi tecnici, diagrammi, bilancio di massa, ABC, make-or-buy → §4
- K1–K4, M′ij/uj/U, bilanciamento (Salveson, Elmaghraby), Vladzyevsky, WIP, Little, curve logistiche → §5
- tipologie layout, CVP, flussi (O-D, multiprodotto), Buff/AEIOU, combinabilità, handling, magazzini, allocazione scorte → §6

---

## §1 INTRODUZIONE AI SISTEMI DI PRODUZIONE (Cap 1)

### 1.1 Sistema di produzione e processo produttivo
```
SistemaProduzione ≔ {persone + macchine + attrezzature + sottosistemi aziendali}
   input[materiali, componenti] ↦ output[beni, servizi] a maggior valore
   vendibili ⇔ quantità✓ ∧ scadenze✓ ∧ livelli-qualitativi✓
ProcessoProduttivo ≔ trasformazione materiali→prodotti via scambi-energia (variazioni
   fisico-chimiche) ∨ manodopera (montaggi → variazioni morfologiche)
Valore ≔ costi + marginalità_desiderata [azienda] ≔ riconoscimento-utilità [cliente]
```
Gerarchia: `Enterprise ⊃ Site ⊃ Area ⊃ WorkCenter ⊃ WorkUnit` (+ StorageZone = WC speciale).
Sottosistemi: informativo · ammin/controllo · organizzativo · logistico esterno · logistico interno.
→ dimensionamento (progettazione) e gestione (programmazione+controllo) NON scindibili.

Ciclo di pianificazione (3 orizzonti in parallelo, rolling):
```
Pianificazione  [lungo, ≥1 anno]  : previsioni domanda + scelte strategiche
Programmazione  [medio, mesi]     : ordini reali → programmi → ordini di produzione + acquisti MP
Scheduling      [breve, settimane]: sequenze operative per operatori e macchine
```

### 1.2 Il contesto di riferimento
Leve competitive = {prezzo, qualità, immagine, capacità-adattiva, forza-vendita, organizzazione}.
Cause compressione ciclo di vita / time-to-market: concorrenza elevata (globalizzazione) ·
evoluzione consumatore (compra il SERVIZIO non il bene) · innovazione tecnologica.
```
Economie_scala ≔ ↓costo_unitario via ↑volumi [saturazione + specializzazione]
Economie_scopo ≔ risparmio da produzione-congiunta con stessi fattori ⇔ diversificazione
```

#### 1.2.1 Standardizzazione e personalizzazione
```
Mass_customization ≔ prodotto configurato per il cliente SU linea di massa
VRP (Variety Reduction Program) ≔ sviluppo CONTEMPORANEO della gamma per ↓varietà componenti
4 AZIONI VRP:
1. Scomposizione fisse/semivariabili/variabili → core standard + differenziazione in assemblaggio
2. Combinazione : moduli base standard + interfacce → molte combinazioni (LEGO)
3. Multifunzionalità e integrazione : min parti per funzione
4. Range : ↑ampiezza intervallo d'uso di un componente → ↓componenti equivalenti
```

#### 1.2.2 Ciclo di vita del prodotto e del processo
PLC mercato (5 fasi): Sviluppo → Introduzione → Crescita → Maturità → Declino.
Ciclo di vita fisico (5 fasi): acquisizione-risorse → produzione → distribuzione → utilizzo → fine-vita.
Evoluzione TECNOLOGICA: curva a S, tecnologie sostitutive A→B→C da studiare con anticipo.
Ciclo di vita del PROCESSO (4 macro-fasi): Concepimento+progettazione · Avviamento · Regime · Chiusura∨riconfigurazione.

### 1.3 L'ubicazione di un impianto industriale
Occasioni: prima installazione · espansione geografica · integrazione/disintegrazione · trasferimento · ampliamento in loco.
#### 1.3.1 Principi
```
MERCATO: concentrato → prossimità; distribuito → baricentro (geografico/ponderale/volumetrico)
  range distanze = f(costo-trasporto/valore, shelf-life, unicità)
FORNITORI (costo/km·q uniforme): 1 MP senza perdita peso → indifferente; con perdita peso → PRESSO LA FONTE
RISORSE: manodopera · trasporti · energia · connettività · servizi di supporto
ALTRO: distretti · incentivi (fondo perduto, finanziamenti agevolati, fiscali) · fattori geografici
```
#### 1.3.2 Metodo del punteggio
```
1. n fattori · 2. pesi pᵢ con Σpᵢ=1 [strategia] · 3. voti Vᵢⱼ∈[1;10] [tecnica]
4. Pᵢⱼ=pᵢ·Vᵢⱼ · 5. Pⱼ=ΣᵢPᵢⱼ · 6. scegli max Pⱼ
LIMITI: soggettività pesi+voti · ignora interdipendenze · differenze piccole → analisi economica
Esempio sughi pronti (3 siti): P(A)=6,25 P(B)=6,75✓ P(C)=6,40
```

---

## §2 LA CLASSIFICAZIONE DEI SISTEMI DI PRODUZIONE (Cap 2)

### 2.1.1 Classificazione dei prodotti — 3 chiavi
```
PER AGGREGAZIONE: codice/SKU (max dettaglio, controllo) · famiglia (affinità produttiva = setup brevi) · tipo (previsioni lungo periodo)
PER COMPLESSITÀ (gestionale, dalla DISTINTA BASE):
  semplice  : DB ≃1 livello ("ricetta") — spesso produzioni per processo
  complesso : DB profondità (fasi in sequenza) ∧ ampiezza (codici convergenti)
  ⚠️ carta: gestionalmente SEMPLICE ma tecnologicamente COMPLESSA (le due complessità anticorrelate)
PER MODULARITÀ: modulare (moduli + interfacce standard; Dell) vs integrale
```

### 2.1.2 Modalità di soddisfazione della domanda (CODP)
```
delivery_lead_time (ordine→consegna) vs internal_lead_time (attraversamento fasi)
⚠️ TA fase ≫ tempo tecnico · indice di programmazione ≔ rapporto tra le due
PUSH = su previsione · PULL = su ordine · CODP ≔ spartiacque previsione/ordine
MTS : vendo da magazzino, cliente anonimo, previsioni
ATO (MTS-ATO): sottogruppi standard su previsione + assemblaggio su ordine [automotive]
MTO : produzione su ordine, MP a scorta
PTO : anche approvvigionamento a valle dell'ordine [sartoriale]
ETO : anche progettazione+industrializzazione su ordine [impianti, aerospazio]; critico: PREVENTIVAZIONE
MTS ed ETO = uniche modalità "pure"; le altre = ibride con CODP
LEVE a ↓delivery LT: gestionale (magazzini a valle) · progettuale (↓tempi attraversamento) · postponement (modularità)
```

### 2.1.3 Processi tecnologici e soluzioni impiantistiche
```
Produzione_per_processo ≔ IRREVERSIBILE, ciclo OBBLIGATO, flusso continuo [acciaio, carta, chimica]
Produzione_per_parti ≔ REVERSIBILE (montaggio/smontaggio), ciclo non obbligato [auto, elettronica]
JOB_SHOP ≔ macchine general-purpose per reparti ad affinità tecnologica; routing alternativi
  + flessibilità (prodotto/mix/volumi) − programmazione difficile, ↑WIP/TA, ↓saturazione
GROUP_TECHNOLOGY ≔ celle dedicate a FAMIGLIE (affinità cicli → setup↓); flusso a direzione unica
  + programmabilità, collo stabile, ↓WIP/TA, ↑saturazione − operazioni fuori cella, rigidità
FLOW_SHOP ≔ macchine sequenziate sul routing, trasporto automatizzato
  − rigidità massima, capacità per quantità DISCRETE, guasto blocca tutto
```

### 2.1.4 Organizzazione del lavoro
```
MODALITÀ AVANZAMENTO: ritmo NON imposto (polmoni) · ritmo IMPOSTO (cadenza fissa) ·
  trasferimento CONTINUO (convogliatore, auto) · trasferimento NON vincolato (operatore decide)
MANODOPERA: parcellizzata · ricomposta (job enrichment) · a isola (responsabilità collettiva)
⚠️ celle (scala) vs isole (mansioni complete, +flessibilità/qualità)
```

### 2.1.5 Modalità di realizzazione dei volumi
```
⚠️ UNICO profilo DISCREZIONALE (MTS/MTO si subiscono; processo fissato dal prodotto)
discreta {unitaria, a lotti} — intermittente · continua — flusso omogeneo
Congruenze: continua∧processo∧MTS [cemento] · discreta∧parti∧ETO [navale] · discreta∧parti∧ATO [auto]
```

### 2.2 Matrice Prodotto–Processo
```
Assi: MERCATO (specialty→commodity) × FLUSSO (frammentario→continuo)
DIAGONALE = fisiologica: job shop → group technology → flow shop → processo continuo
FUORI DIAGONALE = PATOLOGIE (oneri ingiustificati ∨ opportunità perse)
TREND lungo diagonale: ↓prodotti ↑volumi, ↑rigidità/standardizzazione, ↓WIP, ↑scorte PF
```

---

## §3 LE PRESTAZIONI DEI SISTEMI DI PRODUZIONE (Cap 3)

### 3.1 La misura
```
Efficienza ≔ output/input · Efficacia ≔ successi/eventi-totali
4 prestazioni: produttività (eff. STATICA) · qualità · servizio · flessibilità (eff. DINAMICA)
```
#### 3.1.1 Flessibilità (4 dim.) e versatilità
```
mix · prodotto · volume (⇔ ELASTICITÀ) · piano
Versatilità ≔ solo macchinari; NECESSARIA ma NON SUFFICIENTE; riconfigurabilità + convertibilità
```
#### 3.1.2 Livello di servizio
```
per COMMESSA: prontezza, puntualità · a MAGAZZINO: disponibilità, persistenza stock-out
COMUNI: accuratezza, completezza
```

### 3.2.1 Potenzialità produttiva
```
P ≔ produttività = ritmo standard = throughput rate [volume/tempo]
P_teorica (targa) vs P_effettiva · misure disaggregate: lavoro, macchinari, materiali (=resa)
```

### 3.2.2 Tempo di attraversamento ⚠️
```
TA ≔ tempo di attraversamento = flow/cycle/throughput time [tempo/unità]
TVA ≔ tempo a valore aggiunto (netto attese, code, trasporti)
TCL ≔ tempo di ciclo della linea = TA della macchina PIÙ LENTA
IF ≔ TA/TVA  (tipici 10–100 · buoni 3–5 · ottimi 1–2 · sempre ≥1)
```
Esempio 5 stazioni (10-20-30-10-20): TVA=90, 1°pezzo TA=90, a regime TA=120, IF=1,33, P=2 pz/h.
⚠️ Doppio uso simboli: TA attraversamento ≠ TA apertura (OEE); TS standard 1/P ≠ TS solare.

### 3.2.3 Potenzialità di mix
```
Pmix = Q_TOT/T_TOT = 1/Σᵢ(αᵢ/Pᵢ) = Σᵢβᵢ·Pᵢ   αᵢ=Qᵢ/Q_TOT (volume) · βᵢ=Tᵢ/T_TOT (tempo)
⚠️ media ARMONICA pesata sui volumi (non aritmetica!)
```
Esempio: P_A=600, P_B=400, α_A=2/3 → Pmix=514,2 kg/h (≠ 533).

### 3.2.4 Overall Equipment Effectiveness
Six big losses: fermate misurabili (guasti, set-up) · velocità (piccole fermate, rallentamenti) · difetti (scarti, rilavorazioni).
```
Gerarchia tempi: TS (solare 8760h) → TA (apertura) → TC (carico) → TO (operativo) → TON (op. netto) → TOVA (a VA)
L  = TC/TA   Efficienza di carico
Ap = TO/TC   Disponibilità (tipico >90%; MTBF, MTTR → limite)
Ep = TON/TO  Efficienza prestazioni (TS=1/P; linea 0,80–0,95 · reparti 0,65–0,80)
Q  = TOVA/TON Tasso di qualità (95–100%)
OEE  = Ap·Ep·Q = TOVA/TC
TEEP = L·Ap·Ep·Q = TOVA/TA
```
⚠️ Rilavorazioni ignote: Ep* sottostima, Q* sovrastima, ma Ep*·Q*=Ep·Q → OEE INVARIATO.
Esempio nylon: TA=7680, L=96,7%, Ap=95,2%, Ep*=86,7%, Q*=97,4%, OEE=80,4%, TEEP=77,7%.

### 3.2.5 Capacità produttiva
```
CP ≔ quantità MASSIMA in arco prefissato · teorica (ideale) vs reale (effettiva)
CP = P·TOVA = P·TA·TEEP = P·TC·OEE
```
Esempio Gragnano: Pmix=17,2 pz/h, OEE=82,9%, CP_mix≈4705 pz/mese. ⚠️ β≠α (Secchiello 49% vol / 56% tempo).
⚠️ AFFIDABILITÀ (R, λ, MTTF/MTBF/MRL, Weibull, vasca, RBD, FTA/MOCUS): in domande_impianti ma ASSENTE dal PDF 2026.

---

## §4 LA PROGETTAZIONE DEI SISTEMI DI PRODUZIONE (Cap 4)

### 4.1 Elementi di progettazione
Progettare = COMPORRE mezzi di esercizio rispondendo a obiettivi+vincoli → visione olistica.
#### 4.1.1 Occasioni
```
EX-NOVO ≔ nuovo impianto [raro] + max ottimizzazione
RIPROGETTAZIONE (complessità decrescente): conversione · riconversione · ammodernamento ·
  ampliamento ORIZZ (↑mezzi, analisi mercato) · ampliamento VERT (integrazione monte/valle) · sicurezza
⚠️ CP impianto = saturazione del fattore a PIÙ BASSA capacità → ampliamento sfrutta prima i NON saturi
```
#### 4.1.2 Dimensioni — 5 sotto-progetti
finanziario · prodotto · processo · architettonico · commerciale (ciclo iterativo).
#### 4.1.3 Articolazione
```
STUDIO DI FATTIBILITÀ (11 fasi, → piano finanziario + redditività)
PROGETTAZIONE: massima → definitivo → esecutivo (livelli che vincolano)
TRADE-OFF: costi INVESTIMENTO ↔ costi PRODUZIONE; capacità di influire DECRESCE col progetto
```

### 4.2 I processi produttivi
5 attività: operazioni, trasporti, controlli, attese, immagazzinamenti.
Macchine SPECIALIZZATE (−inv, ↓flessibilità) vs GENERAL PURPOSE (+inv, ↑flessibilità).

#### 4.2.1 Archivi tecnici
```
Distinta base: albero rovesciato · scalare · riepilogata
ESPLOSIONE (fabbisogni, ricambi) · IMPLOSIONE (modifiche, esaurimento scorte)
Dati di legame: coeff. impiego (netto) · coeff. scarto (extra-consumo) · validità · lead time
Evoluzione: DB progetto → DB produzione → DB ordinazione → concurrent engineering
Ciclo di lavorazione: {op, reparto, macchina, attrezzature, tempo+setup, risorse}
```

#### 4.2.2 Rappresentazioni e bilancio di massa
Diagrammi: qualitativo · sequenziale (ASME: ○ operazione, □ controllo, ⇒ trasporto, D attesa, ▽ magazzino) · quantitativo (bilancio di massa) · Sankey.
```
INPUT: MP principali (definite/indefinite) · parti componenti · MP ausiliarie (dirette/indirette)
OUTPUT A VALORE: prodotti · sottoprodotti · cascami
OUTPUT DA VALORIZZARE: scarti · sfridi/ritagli · boccami · rottami · perdite/cali/rifiuti  [8 voci totali]
```

### 4.3 L'ingegnerizzazione
```
COSTO DELLA COMPLESSITÀ (varia con diversità, non volumi): unit/batch/product/facility level
INGEGNERIZZAZIONE ≔ raccordo prodotto↔processo → min costo complessità
ITER: 1) programma · 2) famiglie per similitudine tecnologica · 3) ANALISI ABC (A~80%, B→95%, C→eliminare) ·
  4) make-or-buy (unificate UNI/EN/ISO · da catalogo · normazione aziendale) · 5) dai disegni
```

---

## §5 LA CONFIGURAZIONE DEI SISTEMI DI PRODUZIONE (Cap 5) ⚠️ capitolo-chiave

### 5.1 I 2 aspetti
1) NUMERO di risorse (§5.2) · 2) ORGANIZZARE le risorse (bilanciamento, §5.3).

### 5.2 Numero di risorse
```
η = Qu/Q = K1·K2·K3·K4 < 1
  K1 scarto · K2 disponibilità · K3 rendimento operatore · K4 utilizzo (programmazione)
Cascata scarti (a ritroso): Q_monte = Qu/Πₖ(1−pₖ)  ⚠️ MOLTIPLICATIVI, non somma
M′ij = Qij/[(1/Tij)·Nij]  · Mj = ⌈ΣᵢM′ij⌉ · uj = M′j/Mj · U = Σⱼ(uj·Mj)/ΣⱼMj
Dente di sega u(Q): salti da M/M a M/(M+1) — dipende SOLO da M, non dalla potenzialità
```
Esempi: 6 prodotti → M′₁=2,643, M₁=3, u₁=88,1%. Linea 7 macchine → U=77% (18 macchine).

### 5.3 Bilanciamento delle linee
```
Bilanciamento ≔ ↓inattività e differenze di velocità → flusso organico
Fattori: output, vincoli PRECEDENZA, disponibilità risorse, vincoli DISPOSIZIONE
3 sotto-problemi: aggregazione (§5.3.1) · n. magazzini (§5.3.3) · entità scorte (§5.3.4)
```
#### 5.3.1 Linea monoprodotto — formule
```
TCL = TP/Q* = DT/v · TOPj = Σ TPi ≤ TCL · TIj = TCL−TOPj · BD = Σ TIj
i = M − ΣTPi/TCL  (8) ⚠️ FORMA DEL PDF (può superare 1); min i ⇔ min M
M′ = ⌊ΣTPi/TCL⌋+1 · M″ = #{TPi>TCL/2} · M = max{M′,M″}
```
##### 5.3.1.1 Salveson
Per TENTATIVI senza vincoli di precedenza. Limiti: enumerazione · soluzioni incongruenti con sequenze.
Esempio: TPi {0,50;1,00;0,20;0,85;0,80;0,10}, M=4, sol. libera BD=0,55; con sequenza obbligata BD=1,55 (M=5).
##### 5.3.1.2 Elmaghraby (euristico, con precedenze)
```
Matrice P (con transitivi) · KP = (P+In)·TP = TPi + Σ successori
Ordina KP decrescente; assegna se TPk≤TRj ∧ tutti i predecessori in g≤j
```
Esempio 9 operazioni, TCL=12: KP1=38…KP9=3 → 4 stazioni, BD=10, i=4−38/12=0,83 ✓.

#### 5.3.2 Giacenze interoperazionali
Scorta OPERATIVA (WIP, bilancia ritmi, no starving/blocking) · scorta SICUREZZA (copre guasti).
#### 5.3.3 Vladzyevsky — numero magazzini
```
η = 1/(1+I) · con MG settori: I = (Ī/MG)(1+δ) + IM(MG−1)
MG* = √[(Ī/IM)·(1+δ)]
```
#### 5.3.4 Entità WIP
```
WIPc ≔ valore del WIP per cui P=Pb (collo) ∧ TA=TVA (minimo) → max efficienza scorte
Diagramma di throughput: cumulate CdL in/out → TA orizzontale, WIP verticale, P pendenza
```
##### 5.3.4.1 Little e curve logistiche
```
⚠️ P ≠ 1/TA in generale (vale solo senza starving/blocking)
LEGGE DI LITTLE: WIP = P·TA  (29) → check di coerenza
Curve logistiche (Hopp & Spearman): caso migliore · peggiore · massima casualità
KANBAN (cartellino su contenitore/macchina) · CONWIP (cartellino su pezzo, intera linea)
```
##### 5.3.4.2 Caso migliore
```
Linea bilanciata, 1 macch/staz, deterministico, CONWIP
WIPc = Pb·TVA  ⚠️ = numero macchine (M) solo se bilanciata 1 macch/staz
TA_best = TVA se w≤WIPc, = w/Pb se w>WIPc · P_best = w/TVA se w≤WIPc, = Pb se w>WIPc
```
##### 5.3.4.3 Caso peggiore
```
LOTTI = conwip; tempi sbilanciati al limite
TA_worst = w·TVA · P_worst = 1/TVA  ⚠️ DETERMINISTICO, limite teorico
```
##### 5.3.4.4 Massima casualità (caso pratico peggiore)
```
Tempi ~ esponenziale (senza memoria), stati equiprobabili
TA = TVA + (w−1)/Pb · P = w·Pb/(WIPc+w−1)
Aree: POSITIVA (tra max casualità e caso migliore) · NEGATIVA (verso caso peggiore)
```
Esempio Gagghi Anchia: P=71,8, TA=663h, WIPc=3876, WIP=47.600 (Little ✓), P/P_maxcas=68%, WIP~7,4× → area negativa.
##### 5.3.4.5 Impianto non bilanciato
⚠️ collo NON è né meno macchine né tempo maggiore: è potenzialità (macchine/tempo) MINIMA.
Esempio 4 staz/11 macchine: Pb=PB=0,40, WIPc=8 < 11 macchine.
##### 5.3.4.6 Incremento prestazioni
Potenziare collo (↑Pb, curve si alzano, costoso) · potenziare non-colli (↓TVA → ↓WIPc, meglio per WIP piccoli).

---

## §6 IL LAYOUT DEI SISTEMI DI PRODUZIONE (Cap 6)

### 6.1–6.2 Impostazione e tipologie
```
MACRO-layout (edifici/aree) vs MICRO-layout (macchine/postazioni)
6.2.1 POSTAZIONI FISSE [navale] · 6.2.2 PER PROCESSO ⇔ job shop · 6.2.3 PER PRODOTTO (linea) ·
6.2.4 A CELLE (per famiglia, ibrido; il PF può attraversare più celle)
```
#### 6.2.5 CVP — processo vs prodotto
```
PROCESSO: CF minore, cv MAGGIORE · PRODOTTO: CF maggiore, cv MINORE
4 zone: nessun utile · solo processo · entrambe (processo>linea) · q>q* (linea vince)
q* ≔ volume critico processo→prodotto
```

### 6.3 Analisi dei flussi
```
min CT = Σ qij·cij·dij
Diagramma MULTIPRODOTTO → suggerisce celle · matrice ORIGINE-DESTINAZIONE (diagonale=criticità)
Primo tentativo: CENTRALITÀ (alto traffico al centro) + VICINANZA (coppie intense vicine)
POLIGONO D'INGOMBRO FUNZIONALE ≔ min poligono che racchiude ingombro+operatore+manutenzione+depositi
```
#### 6.3.1 Diagramma di Buff ⚠️
```
Relationship chart triangolare A-E-I-O-U-X:
  A Assolutamente necessario · E Eccezionalmente · I Importante · O Ordinaria · U non importante · X indesiderato
+ MOTIVO (codice): 1 flusso · 2 supervisione · 3 personale comune · 4 contatti · 5 comodità
COMBINABILITÀ: fattori disturbo (polvere, vibrazioni, termico, infiammabilità, rumore) → stringhe → confronto a coppie
```
#### 6.3.2 Postazioni: ergonomia + economia dei movimenti.

### 6.4 Material handling
Attività: trasporto · picking · sorting · merging · dispatching · feeding.
Principi: min movimentazioni/distanze · UdC standard · traiettorie lineari · bidirezionalità · gravità · meccanizzazione.
UdC: imballaggio primario (vendita) · secondario (spesso l'UdC interna) · trasporto (pallet).
Mezzi: transpallet · carrelli a forche · commissionatori · AGV (guidato) · AMR (autonomo) ·
trasportatori fissi (rulli, rotelle) · mobili (vassoi, nastro, tapparelle, aerei) · gru, carroponte, montacarichi.

### 6.5 Magazzini ⚠️
```
6 INDICI: selettività · rotazione · saturazione superficiale · saturazione volumetrica · manodopera · potenza
6.5.1 UdC: sovrapposizione diretta · scaffalature (semplice profondità sel=1, gravità FIFO, drive-in/through, compattabili, alti scaffali)
6.5.4 Progettazione: input GIACENZE + FLUSSI; arrivo sui PICCHI, collaudo sulla MEDIA (free-pass);
  ABC giacenze (A ~10% art→70-80%); serie storica Gmin/Gm/Gmax (Gm→terziarizzazione); dimensionamento col rischio
6.5.5 Allocazione: posti CONDIVISI (banalizzato) · DEDICATI (vani fissi sul max) · MISTI (zone×classi, sul medio)
  spettro grigio (stesso codice su più corsie: resilienza + prelievi paralleli)
```

### 6.6 Espansione
NON sovradimensionare. PIANO REGOLATORE D'IMPIANTO (destinazione aree). ⚠️ magazzini MP/PF comunicano con l'esterno → VINCOLANO il piano.

---

## §⚠️ TRAPPOLE D'ESAME (estratto ad alto rendimento)
```
1. TA apertura ≠ TA attraversamento · TS solare ≠ TS standard 1/P
2. Pmix = media ARMONICA pesata (514,2 ≠ 533)
3. β (tempo) ≠ α (volume): il prodotto più LENTO pesa più in tempo
4. Scarti in serie MOLTIPLICATIVI: Q_monte = Q_valle/Π(1−pk)
5. Rilavorazioni ignote: Ep*·Q* = Ep·Q → OEE INVARIATO (non "sbagliato")
6. L invisibile all'OEE (parte dal TC); si vede solo nel TEEP
7. Manutenzione PREVENTIVA → pianificata (riduce L); GUASTI → misurabili (riducono Ap)
8. Formula (8): i = M − ΣTPi/TCL (può essere >1)
9. M′=⌊Tva/TCL⌋+1 · M″=#{TPi>TCL/2} · M=max
10. Salveson non gestisce precedenze (sub-ottima può essere l'unica feasible)
11. Matrice P di Elmaghraby include i TRANSITIVI; KP=(P+In)·TP
12. P ≠ 1/TA in generale; usa Little come check
13. WIPc = n. macchine solo se bilanciata 1 macch/staz
14. Collo = potenzialità MINIMA (non meno macchine, non tempo maggiore)
15. Caso PEGGIORE è DETERMINISTICO; massima casualità = "caso pratico peggiore"
16. Potenziare collo (↑Pb) vs non-colli (↓TVA→↓WIPc)
17. Salto dente di sega da M/M a M/(M+1), dipende solo da M
18. CVP: tra BEP_linea e q* entrambe in utile ma processo rende di più
19. Allocazione mista: zone sul MEDIO (dedicati sul MASSIMO)
20. Magazzini MP/PF vincolano il piano regolatore
21. AFFIDABILITÀ: in domande_impianti ma ASSENTE dal PDF 2026 → recuperare/chiarire
```
```
