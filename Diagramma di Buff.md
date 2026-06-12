# Diagramma di Buff

> [!summary] In 10 secondi
> Il **diagramma di Buff** (*relationship chart*, §6.3.1) è il diagramma triangolare delle relazioni usato nel **layout** quando il flusso di materiali **non è l'unico criterio** (disturbi reciproci, sicurezza, servizi condivisi). Per ogni **coppia** di attività registra **importanza** del rapporto (scala **A-E-I-O-U-X**) e **motivo** (codice numerico).

## §1 Quando si usa
Il solo [[Analisi CVP|flusso]] non basta a decidere le adiacenze: alcune attività vanno vicine per comodità, altre **lontane** per disturbi (polvere, vibrazioni, rumore). Serve uno strumento che pesi relazioni **qualitative**.

## §2 La scala A-E-I-O-U-X
| Codice | Significato |
|---|---|
| **A** | Assolutamente necessario (vicinanza) |
| **E** | Eccezionalmente importante |
| **I** | Importante |
| **O** | Ordinaria importanza |
| **U** | non importante (*Unimportant*) |
| **X** | indesiderato → vicinanza da **evitare** |

**Motivo** del legame (codice numerico), es.: 1 flusso di materiali · 2 comodità di supervisione · 3 personale in comune · 4 contatti personali · 5 comodità.

## §3 Dal diagramma al layout
→ **Diagramma dei rapporti**: le attività si collegano con linee tanto più **numerose** quanto più importante è la relazione → si posizionano vicine le attività con più linee. Variante solo-flussi: **diagramma del flusso principale**.

## §4 Combinabilità dei processi
Per associare/integrare processi:
1. individuare i **fattori di disturbo** ricorrenti: polverosità, vibrazioni, azione termica, infiammabilità, esplosività, rumore;
2. caratterizzare ogni operazione con una **stringa alfanumerica** (una cifra per fattore):
   - **estesa**: 0 non interessa · da 1 a 5 **genera** il disturbo · da −1 a −5 lo **subisce**;
   - **sintetica**: 0 non interessa · 1 generatore · 2 sensibile;
3. **confronto a coppie** delle stringhe → diagramma triangolare delle relazioni.

## §5 Collegamenti
- [[06 Cap6 - Layout e flussi di materiali]] — pagina indice del capitolo
- [[Layout a celle]] · [[Analisi CVP]] — altri strumenti di scelta del layout
- [[Job shop]] / [[Group technology]] — le adiacenze dipendono dalla soluzione impiantistica
- §6.3.1 di `Impianti_2026 - 06` · [[_Knowledge Graph v2]] §6.3.1
