---
aliases:
  - "02 Cap2 - Classificazione"
  - "Classificazione dei sistemi di produzione"
---
## Domanda del capitolo
**Come si classificano i prodotti e i sistemi di produzione, e perché le classificazioni non sono indipendenti tra loro?**

## Mini-riassunto
Prima si classifica il **prodotto** (3 chiavi: aggregazione, complessità gestionale, modularità — §2.1.1), poi il **sistema** lungo 4 prospettive: rapporto col mercato (CODP → MTS/ATO/MTO/PTO/ETO), processi tecnologici e soluzioni impiantistiche (processo vs parti; job shop / group technology / flow shop), organizzazione del lavoro (avanzamento + manodopera), modalità di realizzazione dei volumi (discreta vs continua — **unico profilo davvero discrezionale**). La sintesi è la **Matrice Prodotto-Processo** (§2.2): le combinazioni coerenti stanno sulla diagonale, fuori diagonale ci sono patologie. Il CODP resta il concetto cardine: spartiacque tra previsione (push) e ordine (pull).

## Concetti trattati

### 2.1.1 Classificazione dei prodotti
- [[Classificazione dei prodotti]] — 3 chiavi: **aggregazione** (SKU/famiglia/tipo), **complessità gestionale** (dalla distinta base: profondità + ampiezza), **modularità** (modulare vs integrale)
- [[SKU - Stock Keeping Unit]]
- ⚠️ carta: gestionalmente semplice ma tecnologicamente complessa — le due complessità sono assi indipendenti

### 2.1.2 Modalità di soddisfazione della domanda (CODP)
- [[CODP - Customer Order Decoupling Point]] — include MTS/ATO/MTO/PTO/ETO, l'**indice di programmazione** (delivery LT vs internal LT) e le **3 leve** di riduzione del delivery lead time (gestionale, progettuale, postponement)
- [[Delivery Lead Time]]
- [[Postponement e Commonality]] — la 3ª leva, abilitata dalla modularità del prodotto

### 2.1.3 Processi tecnologici e soluzioni impiantistiche
- [[Classificazione per processi tecnologici]] — produzione **di processo** (irreversibile, ciclo obbligato) vs **di parti** (reversibile: fabbricazione + montaggio)
- Soluzioni impiantistiche:
	- [[Job shop]] — reparti per affinità tecnologica, massima flessibilità, programmazione difficilissima
	- [[Group technology]] — celle dedicate a famiglie, collo di bottiglia stabile, rigidità su volumi e guasti
	- [[Flow shop]] — macchine sequenziate sul routing, rigidità massima, guasto blocca tutto

### 2.1.4 Organizzazione del lavoro
- [[Ritmi di avanzamento]] — 4 modalità (non imposto, imposto, trasferimento continuo, non vincolato) + manodopera **parcellizzata / ricomposta / a isola** (job enrichment, job rotation)
- ⚠️ celle vs isole: operativamente simili, motivazioni diverse (vantaggi di scala vs mansioni più complete)

### 2.1.5 Modalità di realizzazione dei volumi
- [[Modalità di realizzazione dei volumi]] — discreta (unitaria, a lotti) vs continua; ⚠️ unico profilo **discrezionale** per l'impresa (CODP si subisce, il processo lo fissa il prodotto)
- Congruenze tipiche: continua∧processo∧MTS (cemento) · discreta∧parti∧ETO (cantieri) · discreta∧parti∧ATO (automotive) · discreta∧lotti∧MTS (elettronica di consumo)
- Incongruenza senza spazi: ETO ∧ per processo ∧ continua
- Caso tessile: classificazione diversa per sottosettore (fibre = processo · tessitura = lotti · nobilitazione ≈ processo a lotti · confezione = parti)

### 2.2 Sintesi: la Matrice Prodotto-Processo
- [[Matrice Prodotto-Processo]] — assi mercato (specialty→commodity) × flusso (frammentario→continuo); **diagonale fisiologica**, fuori diagonale **patologie**; lettura dinamica (archetipi di sviluppo) e trend lungo la diagonale (prodotto, processo, materiali, manodopera, organizzazione)

## Punti chiave per l'esame
- Saper collocare il **CODP** sulla catena interna e spiegare cosa cambia da MTS a ETO; **MTO vs PTO** (in PTO anche la MP si acquista dopo l'ordine); **ETO richiede preventivazione**, non previsione.
- Le 3 chiavi di classificazione del prodotto, con l'esempio-trappola della **carta** (semplice gestionalmente, complessa tecnologicamente).
- Pro/contro di **job shop / GT / flow shop** e il percorso evolutivo job → GT → flow al crescere dei volumi.
- Le 4 modalità di avanzamento (continuo = caso particolare dell'imposto) e la distinzione **celle vs isole**.
- Volumi = unico profilo discrezionale; tabella delle congruenze con esempi (cemento, cantieri, auto, tessile).
- **Matrice P-P** (chiesta ×3 in `domande_impianti`): assi, diagonale, le 2 patologie, lettura dinamica, trend.

## Collegamenti
- ← [[01 Cap1 - Introduzione ai sistemi di produzione]] — il "sistema" definito nel Cap1 è ciò che qui si classifica
- → [[03 Cap3 - Prestazioni dei sistemi di produzione]] — ogni classe ha target di prestazione diversi (OEE linea > OEE reparto)
- → [[05 Cap5 - Configurazione dei sistemi di produzione]] — CODP e soluzione impiantistica determinano WIP e tempi di attraversamento
- → [[06 Cap6 - Layout e flussi di materiali]] — job/GT/flow ⇔ layout per reparti / a celle / in linea; la matrice P-P ⇔ [[Analisi CVP]]
