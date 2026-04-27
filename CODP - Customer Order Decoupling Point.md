
> **In 10 secondi:** Il CODP è il punto della catena produttiva in cui l'ordine cliente "incontra" la produzione. A monte si lavora su **previsione** (push), a valle su **ordine** (pull). Spostarlo cambia la natura stessa del sistema produttivo (MTS ↔ ATO ↔ MTO ↔ PTO ↔ ETO).

---

## §1 Domanda fondamentale

> _Dove conviene "rompere" la catena produttiva tra ciò che l'azienda anticipa (rischiando) e ciò che l'azienda esegue solo quando il cliente ha già firmato l'ordine?_

La risposta a questa domanda determina **dove si tengono le scorte**, **quale livello di rischio previsionale** ci si assume, e **quanto velocemente** si può consegnare al cliente.

---

## §2 Il problema concreto

**Scenario.** _Helvetra Servers SA_, produttore svizzero di server enterprise per data center.

- Catalogo: 1 famiglia di chassis, 4 motherboard, 6 tagli di RAM (16→512 GB), 5 opzioni di storage (SSD/HDD/ibrido), 3 GPU opzionali → **circa 1.080 configurazioni teoriche**.
- Lead time interni: 
	- progettazione board = 6 mesi (ma board già esistono)
	- assemblaggio motherboard + alimentatore = 3 settimane
	- configurazione finale (RAM/SSD/GPU + test/burn-in) = **5 giorni**.
- Il mercato (clienti tipo banche, telco, hyperscaler) concede un **delivery lead time di 10 giorni lavorativi**.

**Il dilemma.**
1. Se Helvetra producesse i 1.080 server finiti su previsione (MTS), avrebbe:

	- decine di milioni di € immobilizzati a magazzino,
	- rischio altissimo di obsolescenza (un nuovo processore esce ogni ~12 mesi),
	- previsioni inaffidabili sul singolo SKU configurato.

2. Se Helvetra partisse dall'ordine per _tutto_ (MTO puro), il lead time interno (3 settimane + 5 giorni ≈ 26 giorni) **eccederebbe** i 10 giorni concessi → ordini persi.

→ **La domanda diventa: dove piazzo il CODP?** La risposta naturale è: tenere a magazzino motherboard + chassis + alimentatori già montati come **sottogruppi standard** (modalità MTS), e fare _solo_ la configurazione finale (RAM/SSD/GPU + test) **a valle dell'ordine** (modalità su ordine). Il CODP cade quindi tra "assemblaggio motherboard" e "configurazione finale". Risultato: il sistema lavora in **MTS-ATO**, e i 5 giorni di config finale stanno comodamente nei 10 concessi.

---

## §3 La definizione

**Definizione formale.** Il **CODP** (_Customer Order Decoupling Point_, anche detto _Customer Decoupling Point_) è il punto del flusso produttivo che funge da **spartiacque tra la fabbrica che opera su previsione e quella che opera su ordine**. Coincide tipicamente con uno **stock di disaccoppiamento** (materie prime, semilavorati, sottogruppi, o prodotti finiti).

**Scomposizione in parti.**

|Componente|Significato|
|---|---|
|**Area push (a monte del CODP)**|Tutte le fasi avviate sulla base di **previsioni** dell'azienda, _prima_ dell'ordine. Spingono materiali verso il CODP.|
|**CODP propriamente detto**|Lo **stock di disaccoppiamento** — il magazzino fisico (o virtuale) che assorbe lo sfasamento tra ritmo previsionale e ritmo degli ordini.|
|**Area pull (a valle del CODP)**|Tutte le fasi che partono **solo** dopo la ricezione dell'ordine cliente. Tirano dal CODP verso il mercato.|
|**Posizionamento**|La **profondità** con cui l'ordine cliente "penetra" nel sistema. Più il CODP è a valle → più si lavora su previsione; più è a monte → più si lavora su ordine.|

**Regola di posizionamento.** $$\text{posizione CODP} = f\left(\frac{\text{Delivery Lead Time concesso dal mercato}}{\text{Lead time interni delle fasi a valle}}\right)$$

Il CODP si posiziona nel punto più a valle compatibile con il vincolo: _somma dei lead time delle fasi pull ≤ delivery lead time_.

---

## §4 Come funziona

**Cuore del concetto:** _l'ordine cliente non deve necessariamente attraversare l'intera fabbrica; può "innescarsi" a un punto intermedio, a patto che il magazzino di disaccoppiamento contenga ciò che serve a partire da quel punto._

**Diagramma logico (push → CODP → pull).**

La **freccia "ordine cliente"** entra nel sistema a profondità diverse: minima in MTS (solo prelievo da magazzino PF), massima in ETO (innesca anche la progettazione).

**Casi limite e varianti.**

- **MTS puro:** CODP coincide con il **magazzino prodotto finito**. Ordine cliente attraversa zero fasi produttive. Tipico di: cosmetica di consumo, farmaci OTC, abbigliamento basic.
- **ETO puro:** non esiste un vero stock di disaccoppiamento (al massimo un "magazzino virtuale di specifiche/know-how"). Tutto è pull. Tipico di: cantieristica navale, satelliti, impianti industriali su misura.
- **Casi ibridi (ATO, MTO, PTO):** il CODP è in mezzo. La nomenclatura corretta è in realtà **MTS-ATO** o **MTS-MTO**, a sottolineare che le fasi a monte sono comunque MTS (su previsione).
- **CODP mobile nel tempo:** un'azienda può **spostare il CODP** in risposta a cambiamenti del mercato (vedi §5).
- **CODP multipli:** in produzioni complesse (es. moda lusso) possono coesistere più punti di disaccoppiamento per linee di prodotto diverse.

---

## §5 Applicazione pratica (metodologia)

**Procedura per posizionare/spostare il CODP — step-by-step.**

1. **Mappa i lead time interni.** Per ogni fase del processo (progettazione, approvvigionamento, fabbricazione, assemblaggio, finitura), misura il _lead time effettivo_ (tempo tecnico + attese + code), non il tempo di lavorazione nominale. Ricorda: il rapporto può essere **un ordine di grandezza** (lavorazione = minuti, attraversamento = giorni o settimane).
2. **Misura il delivery lead time concesso dal mercato.** Quanto tempo accetta il cliente tra ordine e consegna? Distingui per segmento di clientela se serve.
3. **Confronta.** Somma i lead time delle fasi e confrontale con il delivery LT. Identifica il punto più a valle tale che `Σ LT_fasi_pull ≤ Delivery_LT`.
4. **Posiziona il CODP** in quel punto → identifica la modalità risultante (MTS / ATO / MTO / PTO / ETO).
5. **Valuta l'affidabilità previsionale a monte del CODP.** Più il CODP è a valle, più alta è la varietà di item su cui prevedere → più critico è il _demand planning_.
6. **Scegli la leva** (se il delivery LT si riduce o serve maggiore reattività):
    - **Leva gestionale** — sposta il CODP a valle (es. da MTO a MTS-ATO). Non cambia l'assetto tecnico, ma richiede previsioni migliori e immobilizzo di scorte di semilavorati/PF.
    - **Leva progettuale** — riduci i lead time interni (just-in-time, riduzione setup, group technology, standardizzazione componenti). Non sposta il CODP, ma accorcia la coda pull.
    - **Postponement** — riprogetta il prodotto in modo che le fasi differenzianti (es. verniciatura, configurazione) siano spostate il più a valle possibile, lavorando un "prodotto neutro" finché possibile. Combina i benefici di entrambe.
7. **Ricontrolla la coerenza** con: tipologia di mercato, struttura distinta base (modulare vs. integrale), volumi, varietà di mix.

**Checklist operativa per non sbagliare il posizionamento.**

- [ ] Ho misurato i lead time **di attraversamento** (non solo i tempi tecnici)?
- [ ] Ho considerato il delivery LT come vincolo **dal punto di vista del cliente** (dall'accettazione ordine a consegna effettiva)?
- [ ] Il CODP scelto rispetta `LT_pull ≤ Delivery_LT`?
- [ ] La varietà di item a monte del CODP è gestibile dal sistema previsionale?
- [ ] Ho verificato che la struttura della distinta base supporti il CODP scelto (modularità, sottogruppi standard)?
- [ ] Se il prodotto è integrale (non modulare), so che CODP intermedi sono di fatto preclusi?
- [ ] Ho dichiarato esplicitamente quale modalità ne risulta (MTS, ATO, MTO, PTO, ETO) per allineare la programmazione?
- [ ] Ho considerato il postponement come alternativa o complemento alle altre due leve?

---

## §6 Esercizio / domanda tipo esame

**Domanda aperta (orale o scritta breve).** _"Definisca il Customer Order Decoupling Point. Discuta come il suo posizionamento determini la classificazione del sistema produttivo e quali leve un'azienda abbia a disposizione quando il mercato riduce il delivery lead time concesso. Illustri con un esempio."_

**Traccia di risposta strutturata** (punti da toccare, in ordine):

1. **Definizione.** Il CODP è il punto di disaccoppiamento tra l'area che opera su previsione (push) e l'area che opera su ordine (pull). Coincide con uno stock fisico/virtuale.
2. **Driver del posizionamento.** Rapporto tra delivery lead time concesso dal mercato e lead time delle fasi interne. Si posiziona nel punto più a valle compatibile col vincolo.
3. **Mappatura sulle 5 modalità.**
    - MTS → CODP in magazzino PF (DLT < ultima fase).
    - ATO (correttamente MTS-ATO) → CODP a livello sottogruppi standard; assemblaggio finale su ordine.
    - MTO → CODP a livello materie prime; fabbricazione e assemblaggio su ordine.
    - PTO → CODP a livello "magazzino progetti"; anche approvvigionamento su ordine.
    - ETO → assenza di vero CODP; anche progettazione su ordine.
4. **MTS ed ETO come estremi puri**, gli altri come casi ibridi.
5. **Le tre leve** in caso di riduzione del delivery LT:
    - **Gestionale** — spostamento del CODP a valle (es. MTO → MTS-ATO). Vantaggio: nessuna modifica tecnica. Svantaggio: previsioni più critiche, scorte più voluminose.
    - **Progettuale** — riduzione dei lead time interni (just-in-time, riduzione setup, group technology). Vantaggio: assetto invariato per il cliente. Svantaggio: investimento e riprogettazione.
    - **Postponement** — terza leva basata sulla modularità del prodotto: si lavora un prodotto neutro fino a valle, posticipando la personalizzazione (es. verniciatura, packaging, configurazione finale).
6. **Esempio.** Server enterprise: CODP a livello motherboard pre-assemblata (MTS-ATO); configurazione finale (RAM/SSD/GPU) su ordine, eseguita in 5 giorni, dentro i 10 concessi dal mercato.

**Variante ("e se cambiasse X?").** _"Cosa accadrebbe se il delivery lead time si riducesse da 10 a 3 giorni?"_ → I 5 giorni della configurazione finale eccederebbero il vincolo. L'azienda dovrebbe:

- (a) **leva progettuale** — comprimere la fase di configurazione (automatizzazione test/burn-in, parallelizzazione) sotto i 3 giorni;
- (b) **leva gestionale** — spostare il CODP ulteriormente a valle, tenendo a magazzino _configurazioni-tipo_ pre-assemblate (regredendo verso MTS) — al costo di moltiplicare le scorte e il rischio di obsolescenza;
- (c) **postponement** — rivedere l'architettura per ridurre il numero di operazioni di personalizzazione finale.

---

## §7 Errori comuni

> [!warning] ❌ Confondere il CODP con un magazzino "qualunque" **L'errore.** Pensare che ogni stock nel processo sia un CODP. **Perché è sbagliato.** Il CODP è specificamente il _punto in cui cambia la logica gestionale_ (push → pull). Possono esistere stock interni (buffer interoperazionali, polmoni) che non sono CODP perché entrambe le facce restano push o entrambe pull. **Come evitarlo.** Chiediti sempre: _"a monte di questo stock si lavora su previsione e a valle su ordine?"_ Solo se la risposta è sì, è un CODP.

> [!warning] ❌ Dimenticare la nomenclatura "MTS-ATO" **L'errore.** Dire che ATO significa "tutto su ordine". **Perché è sbagliato.** In ATO, MTO, PTO solo le fasi _a valle_ del CODP sono pull. Le fasi a monte restano comunque su previsione (MTS). La dicitura corretta è MTS-ATO, MTS-MTO, MTS-PTO. Solo MTS ed ETO sono modalità "pure". **Come evitarlo.** Pensa al CODP prima di etichettare il sistema: la modalità descrive _l'ultima fase pull_, non l'intero processo.

> [!warning] ❌ Ignorare la differenza tra leva gestionale e leva progettuale **L'errore.** Rispondere che "per ridurre il delivery LT si fa just-in-time" senza distinguere il _tipo_ di intervento. **Perché è sbagliato.** Le due leve hanno costi, tempi e rischi totalmente diversi: la gestionale sposta il CODP (rapida, ma carica il previsionale); la progettuale riduce i tempi interni (richiede investimenti e ridisegno). Confonderle è un classico errore d'esame. **Come evitarlo.** Quando rispondi sulla riduzione del DLT, elenca **sempre tre leve**: gestionale, progettuale, postponement, e indica per ognuna trade-off e contesto applicabile.

---

## §8 Collegamenti

**Prerequisiti (cosa devo sapere PRIMA):**

- [[Delivery Lead Time]] — il vincolo esterno che determina dove può stare il CODP
- [[Lead Time Interno]] — distinzione tra tempo tecnico e tempo di attraversamento
- [[Indice di Programmazione]] — rapporto tra tempo di attraversamento e tempo tecnico
- [[Push vs Pull]] — logiche gestionali contrapposte
- [[Distinta Base]] — la modularità della BOM abilita o preclude certi posizionamenti del CODP
- [[02 Cap2 — Classificazione dei sistemi di produzione]]

**Dipendenze (cosa ne consegue):**

- [[MTS — Make To Stock]] — modalità con CODP a magazzino PF
- [[ATO — Assemble To Order]] — modalità con CODP a livello sottogruppi
- [[MTO — Make To Order]] — modalità con CODP a livello MP
- [[PTO — Purchase To Order]] — modalità con CODP a livello specifiche/progetti
- [[ETO — Engineer To Order]] — assenza di vero CODP
- [[Postponement]] — terza leva di gestione del CODP, basata su prodotto modulare
- [[Just-in-time]] — leva progettuale per ridurre i LT interni e abilitare CODP più a valle
- [[Group Technology]] — tecnica che abilita la riduzione setup → leva progettuale
- [[VRP — Variety Reduction Program]] — strategia di standardizzazione che agevola CODP a valle
- [[Mass Customization]] — applicazione del CODP-a-valle + postponement per personalizzazione su scala
- [[Demand Planning]] — diventa più critico man mano che il CODP si sposta a valle
- [[Matrice Prodotto-Processo]] — il CODP correla con le diagonali di congruenza job-shop/group-tech/flow-shop

---

## §9 Auto-verifica

1. **Base —** Cosa separa l'area push dall'area pull, e come si chiama il punto di separazione?
2. **Intermedio —** Un'azienda che produce mobili modulari ha un delivery LT di 4 settimane e i seguenti LT interni: progettazione (no, già fatta, catalogo), approvvigionamento legno = 6 settimane, taglio + foratura = 1 settimana, assemblaggio + finitura = 2 settimane. Dove deve stare il CODP, e in quale modalità si trova l'azienda?
3. **Profondo —** Un produttore di profumi di lusso vede ridursi il delivery LT da 30 a 10 giorni a causa di un nuovo competitor online. Discuti quale combinazione delle tre leve (gestionale, progettuale, postponement) potrebbe applicare, considerando che il prodotto è caratterizzato da fragranze diverse ma flaconi e packaging in gran parte comuni — e quale leva sfrutterebbe meglio la struttura del prodotto.

---

_Nota atomica del Cap2 — Classificazione dei sistemi di produzione · Vault Impianti Industriali · MOC: [[02 Cap2 — Classificazione dei sistemi di produzione]] · Master: [[00 Impianti — MOC]]_