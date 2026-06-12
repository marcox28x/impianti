---
aliases:
  - "Ciclo tecnologico"
  - "Routing"
  - "Routing / Ciclo tecnologico"
  - "Foglio di lavoro"
  - "Foglio di lavorazione"
---
# Ciclo di lavorazione

> [!summary] In 10 secondi
> Il **ciclo di lavorazione** (§4.2.1) è la **sequenza ordinata delle operazioni** necessarie a realizzare un assieme, con per ciascuna: reparto, macchina, attrezzature, tempo di lavorazione + set-up, risorse umane. È, insieme alla [[Distinta base (BOM)]], l'archivio tecnico che alimenta la configurazione ([[Numero di risorse]], [[Bilanciamento delle linee]]).

## §1 Struttura
Per ogni **operazione**: codice op · reparto · macchina · attrezzature · tempo di lavorazione + set-up · risorse umane. Il *routing* può essere **obbligato** (produzione per processo) o ammettere **alternativi** (job shop).

> [!example] Esempio — libreria metallica 3 ripiani
> op 10 taglio montanti (rep.1, A36, 0,2′) · op 20 taglio pianali (rep.1, A40, 0,3′) · op 30 piegatura montanti (rep.2, C17, 1,0′) · op 40 piegatura pianali (rep.2, C19, 1,0′) · op 50 assemblaggio (rep.3, banco, 4,0′).

## §2 Foglio di lavoro
Una scheda **per operazione**: scompone l'operazione in fasi/elementi con i parametri tecnologici (velocità di taglio, avanzamento, profondità di passata, tempi per fase, set-up).

## §3 Collegamenti
- [[Distinta base (BOM)]] — il "cosa" (struttura prodotto); il ciclo è il "come" (sequenza operativa)
- [[Bilanciamento delle linee]] — i tempi $TP_i$ degli elementi minimi vengono dal ciclo
- [[Numero di risorse]] · [[ingegnerizzazione]] — usano i tempi di ciclo
- §4.2.1 di `Impianti_2026 - 04` · [[04 Cap4 - Progettazione dei sistemi di produzione]] · [[_Knowledge Graph v2]] §4.2.1
