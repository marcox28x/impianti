SKU è semplicemente il codice univoco con cui un'azienda identifica **una specifica variante di prodotto vendibile e gestita a magazzino**.

Attenzione a non confonderlo col codice componente:

- il **codice componente** vive nella distinta base (Cap 4): è la vite, il tappo, l'etichetta, il semilavorato
- lo **SKU** vive nella logistica commerciale: è quello che il cliente compra come prodotto finito

---

## la razionalizzazione SKU di Coca-Cola durante la pandemia (2020)
Coca-Cola gestiva circa 1.200 SKU e ne ritirava in media 200 all'anno. Su scala globale il portafoglio dichiarato superava i 3.500 prodotti in oltre 200 paesi.

Quando è scoppiata la pandemia, il CEO James Quincey ha parlato esplicitamente di "prioritizzare in modo spietato i brand e gli SKU core per rafforzare la resilienza della supply chain". Il risultato: il portafoglio è stato ridotto da oltre 400 brand a circa 200 (più della metà eliminata).

Quincey ha detto una frase che è quasi una citazione perfetta dal manuale di Impianti: "i brand di un singolo paese, con poca o nessuna scala, rappresentano solo il 2% del fatturato ma ognuno richiede comunque risorse".
In sintesi, la **coda lunga di SKU a basso volume** consuma capacità di previsione, spazio a magazzino, slot di produzione, risorse di pianificazione, ma senza generare ricavi proporzionali.

C'è un dettaglio illuminante in uno degli articoli: "anche se il liquido dentro sei diverse SKU di Diet Coke è lo stesso, le diverse dimensioni e campagne promozionali confondono la supply chain". 
Questo è il caso da manuale. _Stessa_ bevanda fisica → SKU multipli per:

- formato (lattina 33cl, lattina 25cl, bottiglia PET 50cl, vetro 33cl, fontane bar...)
- multipack (singola, 6-pack, 12-pack, 24-pack)
- mercato/lingua etichetta
- promo (edizione speciale, co-branding, etichette regionali)

Risultato: una sola "ricetta" può diventare facilmente 20–30 SKU. La distinta base del liquido è identica, ma a livello logistico-commerciale sono prodotti distinti, ognuno con la sua scorta, la sua previsione, il suo codice a barre.

La decisione concreta fu quella di sacrificare quelli che Quincey ha chiamato "zombie brand", non solo "zombie SKU": brand ancora vivi sul mercato ma senza prospettiva di crescita.

---

## Perché avere tanti SKU è un problema (e non sembra)

Intuitivamente più varianti = più scelta = più vendite. Ma ogni SKU porta con sé dei costi nascosti:

1. **Previsione di domanda**: Coca-Cola lavora MTS (Make-To-Stock), quindi produce su previsione. Ogni SKU richiede la sua previsione, e prevedere uno SKU che vende 100 pezzi al mese è molto più impreciso che prevederne uno che ne vende un milione (legge dei grandi numeri).
2. **Scorta a magazzino**: capitale immobilizzato.
3. **Set-up sulla linea**: ogni cambio formato/etichetta richiede un riattrezzaggio.
4. **Anagrafica tecnica**: distinta base, foglio di lavoro, fornitori, codifiche da mantenere.
5. **Spazio fisico**: nello StorageZone (gerarchia ISA-95 del Cap 1).

Il punto critico è che la distribuzione delle vendite è quasi sempre fortemente sbilanciata: tipicamente **metà degli SKU genera ~98% del fatturato**, l'altra metà solo il 2%. Quella seconda metà sono i cosiddetti _zombie SKU_ — vendono pochissimo ma ti costano lo stesso tutti i punti sopra.

## Il legame con l'OEE (la parte importante per il Cap 3)

Qui c'è il pezzo che il tuo materiale dà per scontato. Ragiona passo per passo:

Sulla stessa linea fisica, quando passi da lattine 33cl a lattine 25cl devi fare un **set-up**: regolare la macchina, cambiare etichette, eventualmente sciacquare i tubi. Il set-up consuma tempo dal Tempo di Carico TC senza produrre niente di vendibile.

Catena causale:

Più SKU → più set-up → meno Tempo Operativo TO → cala la Disponibilità Ap = TO/TC → cala l'OEE = Ap·Ep·Q.

In più, ogni SKU ha la sua potenzialità standard P_i (pezzi/ora). Se hai SKU "lenti" sulla linea, anche con peso modesto, ti tirano giù la Pmix:

$$P_{mix} = \frac{1}{\sum_i \alpha_i / P_i^{std}}$$

dove α_i è la quota di volume dello SKU i. Uno SKU con α_i piccolo ma P_i^std molto basso pesa comunque sulla media armonica. Tradotto: gli SKU di nicchia non solo vendono poco, ma rallentano anche il resto della produzione quando ci sono.

## Cosa ha fatto Coca-Cola nel 2020

In piena pandemia, il CEO James Quincey ha annunciato il taglio del portafoglio brand da circa 400 a 200, chiudendo marchi come Odwalla, TaB, Zico. Questa è un'**applicazione manualistica del VRP** (Variety Reduction Program, Cap 1.2.1), solo che applicata al portafoglio commerciale invece che ai componenti tecnici:

- **Parti fisse** ⇔ brand core (Coca-Cola, Sprite, Fanta, Powerade) → intoccabili
- **Parti semivariabili** ⇔ varianti consolidate (Coca Zero, Cherry, Vanilla) → alcune si tengono
- **Parti variabili** ⇔ brand di nicchia → candidati al taglio

Effetto atteso: meno set-up → più Ap → più OEE → più capacità produttiva reale CP = P·TC·OEE → previsioni di domanda più affidabili.

## Le alternative al taglio brutale (per essere completi a esame)

Tagliare SKU è la soluzione "ascia". Il corso suggerisce alternative più eleganti per gestire varietà senza esplosione di codici:

**Postponement (spostare il CODP a monte)**: invece di tenere a magazzino 1.200 prodotti finiti come MTS, tieni a magazzino sottoassiemi _neutri_ e fai la personalizzazione finale solo all'ordine, passando di fatto a una logica ATO. Esempio: bottiglie senza etichetta a magazzino, etichettatura per mercato solo a valle. La varietà offerta al cliente resta alta, gli SKU "veri" da gestire scendono.

**VRP a livello componente**: 1.200 SKU di prodotto finito possono benissimo essere fatti con 50 componenti standardizzati invece di 500. Riduci la varietà _interna_ senza toccare quella esterna.

**Group technology a livello di linea**: raggruppi gli SKU "simili" (tutte le lattine 33cl) su celle dedicate, così i set-up intra-famiglia sono brevissimi e i set-up "pesanti" sono solo tra famiglie diverse.

## Sintesi da ricordare per l'esame

Lo SKU è il punto di intersezione tra mondi diversi del corso: sottosistema logistico (Cap 1), classificazione MTS/MTO (Cap 2), OEE (Cap 3), distinta base (Cap 4), saturazione e bilanciamento (Cap 5).

Il trade-off attivato è sempre lo stesso, già presente nella tua mappa §RELAZIONI: **varietà offerta al mercato ↔ efficienza interna di produzione**, ovvero standardizzazione ↔ personalizzazione, ovvero flessibilità ↔ efficienza.

Coca-Cola 2020 è il caso da manuale di azienda che, accortasi che il trade-off pendeva troppo dal lato "varietà" (1.200 SKU, coda lunga, OEE compresso), interviene con un VRP di portafoglio per riequilibrare verso "efficienza".

---

Se vuoi posso fare un esempio numerico concreto: prendiamo una linea con 5 SKU, calcoliamo Pmix e OEE prima e dopo aver tagliato i 2 SKU di coda lunga, e vediamo di quanto sale la capacità produttiva. È il tipo di esercizio che potrebbe capitarti.