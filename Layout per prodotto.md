---
aliases:
  - "Layout in linea"
  - "Configurazione per prodotto"
---
> **In 10 secondi:** le macchine sono disposte **in sequenza secondo il ciclo di lavorazione** del prodotto: è la traduzione fisica del [[Flow shop]]. Minimi trasporti interni e controllo semplice, al prezzo di investimento maggiore e rigidità. Varianti **in serie / in parallelo / misto**; geometrie **rettilineo / a U / zig-zag**. [§6.2.3]

## Definizione
Configurazione che organizza le macchine per **assecondare gli spostamenti dei semilavorati** da una macchina all'altra e l'occupazione degli spazi: la disposizione segue fedelmente la sequenza operativa del [[Ciclo di lavorazione]]; all'uscita di ogni macchina il prodotto trova quella della fase successiva.

## Quando si adotta
- **Obbligatoria** per cicli tecnologici **obbligati** ([[Classificazione per processi tecnologici]]): nel pane la cottura deve seguire la lievitazione che segue l'impastatura.
- Per cicli **non obbligati**: possibile solo se la sequenza di lavorazione è **standardizzata o unica** tra i prodotti (alti volumi, [[Matrice Prodotto-Processo]] in basso a destra).

## Vantaggi / Svantaggi
- ✅ **Minimi costi di trasporto interno** e spazio occupato; macchine specializzate per operazione → **tempo di produzione ridotto**; controllo semplice grazie alla standardizzazione di processi e sequenze.
- ❌ **Investimento maggiore** rispetto ai reparti, soprattutto se alcune operazioni **si ripetono** lungo il ciclo → servono più macchine della stessa tipologia.
- ❌ Rigidità del [[Flow shop]]: guasto blocca tutto il sistema, capacità modificabile solo per quantità discrete, lotti con set-up impattanti.

## Varianti della linea
- **In parallelo**: una fase lenta è svolta da **più macchine analoghe** che formano una **stazione** — si comportano come un'unica macchina di prestazioni aumentate; il pezzo in uscita sceglie una qualunque delle macchine. È il rimedio al [[Collo di bottiglia]] che detta il ritmo della linea.
- **In serie**: impianto diviso in **linee indipendenti** — il pezzo non può cambiare linea. Una fase troppo lenta per il ritmo viene divisa su due macchine in sequenza (prima parte + completamento): **parcellizzazione**.
- **Misto**: ogni combinazione non riconducibile alle due precedenti.

## Geometria della linea
| Geometria | Caratteristica |
|---|---|
| **Rettilineo** | postazioni consecutive in linea retta (caso base) |
| **a U** | un operatore **dentro la U** controlla più macchine; MP e PF in zone **adiacenti** |
| **Zig-zag** | vantaggi della U, ma magazzini MP e PF in posizioni **opposte** |

## Mini-esempio
Linea con TCL = 2 min; una fase richiede 6 min/pezzo → da sola sarebbe il collo (P = 10 pz/h vs 30 della linea). Con **3 macchine in parallelo** (M′ = 6/2 = 3) la stazione torna al ritmo della linea — è il calcolo di [[Numero di risorse]] applicato alla singola fase.

## ⚠️ Trappole d'esame
- **Parallelo ≠ serie**: parallelo = stessa fase replicata su macchine analoghe (stazione); serie = linee indipendenti + **parcellizzazione** della fase su macchine in sequenza. Non confonderle.
- **Parcellizzazione** qui (fase divisa tra macchine) condivide la radice con la *manodopera parcellizzata* di §2.1.4 ([[Ritmi di avanzamento]]) ma è un concetto impiantistico, non organizzativo.
- **U vs zig-zag**: si distinguono per la posizione dei magazzini MP/PF (adiacenti vs opposti) — dettaglio chiesto spesso.
- Nel CVP la linea ha **CF maggiori e pendenza minore**: tra BEP_linea e q* è in utile ma rende **meno** del processo — la si sceglie lì solo scommettendo sull'espansione futura ([[Analisi CVP]], 4 zone).
- "Stazione" = concetto **organizzativo** (insieme di risorse per una o più operazioni), coerente con il [[Bilanciamento delle linee]] del Cap5.

## Collegamenti
- ← [[06 Cap6 - Layout e flussi di materiali]] §6.2.3 · equivalente impiantistico del [[Flow shop]]
- → confronto economico con [[Layout per processo]] via [[Analisi CVP]] (volume critico q*)
- → il [[Bilanciamento delle linee]] (Cap5: TCL, TOPj, Salveson/Elmaghraby) decide *cosa* mettere in ogni stazione; il layout decide *dove*
- → dentro una cella di [[Layout a celle]] le macchine sono disposte proprio in linea
- → modalità di avanzamento dei pezzi: [[Ritmi di avanzamento]]
- Altre tipologie: [[Layout a posizione fissa]], [[Layout per processo]], [[Layout a celle]]
