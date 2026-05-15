**In 10 secondi:** Il Delivery Lead Time è il tempo che il cliente concede all'azienda per consegnargli il prodotto dopo aver emesso l'ordine. Non lo decidi tu, lo decide il mercato. Confrontato con i tempi interni della tua fabbrica, ti dice quali fasi puoi fare su ordine e quali devi anticipare su previsione — cioè dove piazzare il [[CODP - Customer Order Decoupling Point]].

---

## §1 Domanda fondamentale

Quanto tempo ho davvero per produrre, prima che il cliente vada da un altro? E come questa risposta determina l'intera architettura gestionale della mia fabbrica (cosa tengo a stock, cosa lancio solo all'ordine)?

---

## §2 Il problema concreto

**Maison Lavanderia**, casa cosmetica milanese di fascia alta, vende due prodotti molto diversi:

- **Rossetto matte "Velour 12"** — catalogo standard, 14 colori. Il cliente lo ordina su Sephora online e si aspetta la consegna a casa entro **2 giorni**.
- **Profumo bespoke "Lavanderia su misura"** — il cliente prenota una consulenza olfattiva, sceglie 5–7 essenze tra 80 disponibili, e l'azienda formula la fragranza personalizzata. Il cliente accetta serenamente un'attesa di **8 settimane**.

In fabbrica i tempi interni reali sono:

|Fase|Rossetto|Profumo bespoke|
|---|---|---|
|Progettazione/formulazione|(già fatta)|2 settimane|
|Approvvigionamento MP (cere, oli, essenze)|3 settimane|1 settimana (spesso a stock)|
|Produzione/miscelazione|2 giorni|3 giorni|
|Confezionamento + etichettatura|1 giorno|2 giorni|
|**Cammino interno totale**|**~3 settimane + 3 giorni**|**~4 settimane**|

Il dilemma:

- Per il **rossetto**, il DLT (2 giorni) è **molto più corto** del cammino interno (≈25 giorni). Impossibile partire dall'ordine.
- Per il **profumo**, il DLT (8 settimane) è **molto più lungo** di tutti i lead time sommati (≈4 settimane). Posso permettermi di partire perfino dalla formulazione.

→ Il DLT, da solo, non dice cosa fare. La risposta nasce dal **confronto** con i tempi interni.

---

## §3 La definizione

**Definizione formale:**

> Il **Delivery Lead Time (DLT)** è l'intervallo di tempo che intercorre tra il momento dell'emissione dell'ordine da parte del cliente e il momento della consegna richiesta.

È una grandezza **esogena**: data dal mercato/cliente, non sotto controllo immediato dell'azienda.

**Scomposizione concettuale:**

- **Cosa misura** → una promessa temporale che il cliente accetta come ragionevole per quel tipo di prodotto.
- **Da dove viene** → settore, tipo di prodotto, posizionamento competitivo, abitudini di consumo, pressione concorrenziale.
- **Termine di paragone** → la somma dei lead time interni (engineering + acquisti + fabbricazione + assemblaggio); è da questo confronto che nasce la modalità gestionale.

**Distinzioni che molti confondono:**

- **DLT ≠ Lead time interno**: il DLT è una richiesta del mercato; i lead time interni sono caratteristiche della fabbrica.
- **DLT ≠ Time-to-market**: il TTM è "idea → mercato" per un prodotto _nuovo_; il DLT è "ordine → consegna" per un prodotto già definito.
- **DLT ≠ Tempo tecnico di lavorazione**: il tempo tecnico è solo il "tempo macchina"; il lead time include code, attese, controlli, movimentazioni — spesso è 1-2 ordini di grandezza maggiore del tempo tecnico (minuti vs giorni).

---

## §4 Come funziona

**Cuore del meccanismo:** il DLT comprime o dilata lo spazio di scelta gestionale dell'azienda. Più il DLT è breve rispetto al cammino interno, più devo anticipare attività su previsione (spostando i magazzini "a valle"); più il DLT è lungo, più posso aspettare l'ordine prima di iniziare (spostando i magazzini "a monte" o eliminandoli del tutto).

**Connessione con il [[CODP - Customer Order Decoupling Point|CODP]]:** il DLT determina dove cade il CODP. Il CODP è esattamente il punto del processo in cui "ci sto ancora dentro" rispetto al DLT — a valle lavoro su ordine, a monte su previsione.

**I 5 scenari, ordinati per DLT crescente:**

| Caso | DLT vs LT interni                                | Cosa è già fatto su previsione      |
| ---- | ------------------------------------------------ | ----------------------------------- |
| MTS  | DLT ≪ tutti i LT interni                         | Tutto, fino al PF a magazzino       |
| ATO  | DLT ≈ LT assemblaggio                            | Semilavorati e sottogruppi standard |
| MTO  | DLT ≥ LT fabbricazione + assemblaggio            | Solo le materie prime               |
| PTO  | DLT ≥ LT acquisto + fabbricazione + assemblaggio | Solo i progetti                     |
| ETO  | DLT ≥ tutti i LT (incluso engineering)           | Niente; si parte dalle specifiche   |

**Casi limite:**

- **DLT che si riduce improvvisamente** (pressione concorrenziale): l'azienda deve reagire spostando il CODP a valle (es. da MTO a ATO), oppure investendo per ridurre i LT interni, oppure facendo postponement.
- **DLT che si allunga** (mercato meno esigente): l'azienda può ritirare i magazzini, ridurre WIP e scorte, spostare il CODP a monte.
- **DLT "infinito"** (ETO con grande complessità, es. cantieristica navale): non è più un problema di tempo, ma di **preventivazione** dei costi e di rispetto della data promessa.

---

## §5 Applicazione pratica

**Metodologia operativa step-by-step** per posizionare il CODP a partire dal DLT:

1. **Misura il DLT richiesto dal mercato** per ciascuna famiglia di prodotti. Non inventarlo: chiedi al commerciale, leggi i contratti, osserva la concorrenza.
2. **Mappa la sequenza interna** delle fasi: progettazione → approvvigionamento → fabbricazione → assemblaggio → consegna.
3. **Stima i lead time interni reali** di ciascuna fase (non i tempi tecnici!): includi code, setup, attese, controlli qualità, movimentazione.
4. **Somma i LT interni dalla coda** (consegna) andando a ritroso, finché il totale raggiunge o supera il DLT.
5. **Il CODP cade in quel punto**: tutto a monte deve essere già pronto al momento dell'ordine; tutto a valle è lanciato dall'ordine.
6. **Identifica la modalità gestionale risultante** (MTS / ATO / MTO / PTO / ETO) e verifica che sia coerente con il tipo di prodotto e con la varietà del mix.
7. **Se il risultato non è gestibile** (es. DLT troppo corto + mix troppo ampio per tenere tutto a stock), valuta le **3 leve di risposta**:
    - **gestionale** → spostare i magazzini a valle (richiede previsioni più affidabili);
    - **progettuale** → ridurre i LT interni (just-in-time, ↓setup, [[Group Technology]], rivedere [[Capacità produttiva (CP)]]);
    - **postponement** → ridisegnare il prodotto con base "neutra" + personalizzazione confinata in coda (es. verniciatura).

**Checklist anti-errore:**

- [ ] Sto usando il DLT _richiesto dal mercato_, non il DLT _attuale dell'azienda_?
- [ ] Sto sommando i LT interni _completi_ (con code e attese), non i tempi tecnici?
- [ ] Ho considerato la varietà di mix? (mix ampio + magazzini a valle = previsioni rischiose)
- [ ] Ho distinto le famiglie con DLT diversi? (un'azienda può avere CODP diversi per famiglie diverse)
- [ ] Se sto pensando ATO, il prodotto è effettivamente modulare? (servono sottogruppi standard veri)

---

## §6 Domanda tipo esame

**Domanda (stile orale):**

> Un'azienda di mobili ufficio produce scrivanie regolabili in altezza. Storicamente lavorava in MTO con DLT concesso dal mercato di **4 settimane**. Per pressione della concorrenza, i clienti corporate ora pretendono consegne in **5 giorni lavorativi**. I tempi interni sono: approvvigionamento componenti (motori, piani, gambe) = 3 settimane; assemblaggio + collaudo + verniciatura = 4 giorni. Discuti come il sistema deve evolvere e quali leve può attivare l'azienda.

**Traccia di risposta strutturata:**

1. **Riconoscere il problema.** Il nuovo DLT (5 giorni) è inferiore al solo lead time di approvvigionamento (3 settimane = 15 giorni lavorativi). In MTO l'azienda non riuscirebbe mai a rispettare la consegna, perché solo l'acquisto dura più del tempo concesso.
    
2. **Posizionare il nuovo CODP.** I 5 giorni di DLT coincidono quasi esattamente con il tempo di assemblaggio+collaudo+verniciatura (4 giorni). Quindi il CODP si sposta tra "approvvigionamento" e "assemblaggio". L'azienda passa da MTO ad **ATO**: i componenti standard (motori, piani, gambe nei formati base) vanno tenuti a stock e ordinati su previsione; l'assemblaggio finale parte solo all'arrivo dell'ordine.
    
3. **Discutere le tre leve attivabili:**
    
    - **Leva gestionale (effetto immediato)**: spostare i magazzini a valle. Costo: maggior capitale immobilizzato in scorte di componenti e rischio di obsolescenza se il mix evolve. Richiede previsioni di vendita più affidabili.
    - **Leva progettuale (medio termine)**: ridurre i lead time interni. Esempi: contratti di fornitura kanban-pull con i fornitori (passare da 3 settimane a 1 settimana di approvvigionamento), ridurre i setup tra commesse, introdurre celle di [[Group Technology]] per le sotto-componenti più variabili. Costo: investimento e riprogettazione organizzativa.
    - **[[Postponement]]**: standardizzare il telaio della scrivania (parte "neutra" tenuta a stock) e confinare la personalizzazione (colore del piano, finitura, dimensioni precise) all'ultima fase. Permette di tenere a stock semi-finiti universali, riducendo le referenze a magazzino senza perdere varietà nel PF.
4. **Conclusione critica.** La scelta dipende da ampiezza e stabilità del mix. Mix ampio e instabile → postponement preferibile. Mix stretto e prevedibile → ATO con magazzino di sottogruppi più semplice. Probabilmente un'azienda reale combina più leve insieme.
    

**Variante** ("e se cambiasse X?"):

> _E se invece il DLT si riducesse a 1 giorno?_

In 1 giorno non riesco neanche ad assemblare. Devo passare a **MTS**: tenere a stock le scrivanie già assemblate nelle configurazioni standard più richieste. Il mix di PF a magazzino diventa il problema critico: o si applica un [[VRP - Variety Reduction Program]] per ridurre la varietà di referenze, o si rinuncia a parte del catalogo in nome della velocità. È il caso tipico di chi vende su Amazon Prime: la promessa di velocità impone disciplina sul mix.

---

## §7 Errori comuni

> [!warning] ❌ Errore 1 — Confondere DLT con lead time interni Il DLT è imposto dal mercato; i lead time interni sono caratteristiche della fabbrica. Se uso i miei lead time interni come "DLT" sto facendo l'errore opposto a quello giusto: sto promettendo al cliente quanto ci metto io, invece di partire da quanto MI CONCEDE lui. **Come evitarlo**: chiedi sempre prima "quanto tempo aspetta il cliente?", e _solo dopo_ guarda alla fabbrica.

> [!warning] ❌ Errore 2 — Trattare il DLT come un singolo numero per tutta l'azienda Nella stessa azienda possono coesistere prodotti con DLT radicalmente diversi (uno standard e uno custom). Trattarli con lo stesso CODP porta a inefficienze: o sovra-investo in scorte per il custom (che non servono) o ne sotto-investo per lo standard (e perdo ordini). **Come evitarlo**: segmenta il portafoglio per DLT _prima_ di scegliere la modalità gestionale. Possono benissimo coesistere CODP multipli.

> [!warning] ❌ Errore 3 — Confondere riduzione DLT con riduzione del time-to-market Il DLT è "ordine → consegna" per un prodotto esistente; il TTM è "idea → mercato" per un prodotto nuovo. Ridurre il TTM richiede [[Concurrent Engineering]] e progettazione integrata; ridurre il DLT richiede leve gestionali/progettuali/postponement. Sono problemi diversi che si risolvono con strumenti diversi. **Come evitarlo**: prima di scegliere uno strumento, chiarisci "stiamo accelerando la consegna di qualcosa che già esiste, o lo sviluppo di qualcosa di nuovo?"

---

## §8 Collegamenti

**Cosa devo sapere PRIMA (prerequisiti):**

- [[CODP - Customer Order Decoupling Point]] — il DLT, confrontato con i LT interni, determina dove cade il CODP. Senza il concetto di CODP, il DLT è solo un numero.
- [[Lead Time]] / [[Internal Lead Time]] — la controparte interna del DLT; necessari per fare il confronto.
- [[Sistemi di produzione]] — il quadro generale di classificazione.

**Cosa ne consegue (dipendenze):**

- [[CODP - Customer Order Decoupling Point|CODP]] — le 5 modalità gestionali sono conseguenza diretta del rapporto DLT/LT interni.
- [[Postponement]] — una delle tre leve attivabili quando il DLT si riduce.
- [[Just-in-time]] — leva progettuale per ridurre i LT interni e accomodare DLT più stretti.
- [[Group Technology]] — strumento di riduzione setup e flessibilità, utile quando la leva progettuale è la risposta.
- [[VRP - Variety Reduction Program]] — utile per gestire i mix in MTS quando il DLT è molto ridotto.
- [[Mass Customization]] — strategia che concilia DLT corto + alta varietà.

---

## §9 Auto-verifica

1. **(facile)** Cosa misura il delivery lead time? Chi lo determina?
2. **(media)** In che modo il rapporto tra DLT e lead time interni determina la posizione del CODP? Fai un esempio concreto in cui un DLT corto forza un CODP più "a valle".
3. **(profonda)** Se il DLT si riduce drasticamente per pressione concorrenziale, l'azienda ha tre leve di risposta: descrivile, indicando per ciascuna il tipo di intervento (gestionale / tecnico / di prodotto), il principale costo associato e in quale scenario di mix prodotti ciascuna è più adatta.