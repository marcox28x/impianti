# Magazzini

> [!summary] In 10 secondi
> I **magazzini** (§6.5) custodiscono scorte per smorzare irregolarità di consumi e approvvigionamenti, ma immobilizzano capitale → vanno al **minimo indispensabile**. Si misurano con **6 indici di prestazione**, si progettano su **giacenze + flussi** (ABC + serie storica + dimensionamento col rischio) e si gestiscono con criteri di **allocazione delle scorte**.

## §1 Ragioni vs costi
**Ragioni**: smorzare irregolarità (valle/monte), flessibilità su mix/volumi, ovviare a inaffidabilità di impianti/manodopera, previsioni inattendibili.
**Costi**: capitali immobilizzati, interessi passivi, deprezzamento, spazio.
⚠️ Magazzini **MP e PF** comunicano con l'**esterno** → posizione vincolante per il piano regolatore.

## §2 I 6 indici di prestazione (§6.5)
| Indice | Definizione |
|---|---|
| **Selettività** | $M_u/M_t$ (movimenti utili/necessari): prelevare senza spostare altro |
| **Rotazione** | UdC prelevate / giacenza media: velocità di rinnovo (alto→costi operativi; basso→obsolescenza) |
| **Saturazione superficiale** | $A_u/A_t$ (superficie usata/totale) |
| **Saturazione volumetrica** | volume occupato / volume locale |
| **Manodopera** | tonnellate movimentate / ore addetti |
| **Potenza** | tonnellate stoccate / potenza installata [kW] (rilevante nel freddo) |

> [!note] Trade-off chiave
> **Selettività ↔ saturazione**: scaffalature a semplice profondità → selettività=1 ma poca densità; sistemi compattabili/passanti → alta saturazione ma bassa selettività.

## §3 Criteri di progettazione (§6.5.4)
Input: **giacenze** (quanto contenere) + **flussi** (movimentazioni/tempo).
- Ricezione dimensionata sui **picchi**; collaudo sulla **media** (free-pass da fornitori garanti).
- **ABC delle giacenze**: classe A ~10% articoli → 70-80% giacenza; dimensionare su A+B (~95%).
- **Serie storica** Gmin/Gm/Gmax: mai Gmin; **Gm** → terziarizzazione (affitto posti pallet, costi fissi→variabili); **Gmax** → investimenti.
- **Dimensionamento col rischio**: curva cumulata delle frequenze → rischio di sottodimensionamento per ogni capacità; G ottimo = min(costi sottodimensionamento + costi diretti).

## §4 Allocazione delle scorte (§6.5.5)
- **Posti condivisi** ("banalizzato"): primo vano libero → ↑utilizzazione vani, −tracciabilità.
- **Posti dedicati**: vani fissi per codice sul **massimo** → ↓tempi prelievo, scaffalature sottoutilizzate.
- **Allocazioni miste** (zone × classi): classe A in zona I…; dimensionare le zone sul numero **medio** di celle. ⚠️
- **Spettro grigio**: stesso codice su più corsie → resilienza ai guasti + prelievi paralleli.

## §5 Collegamenti
- [[Material handling]] — i mezzi che servono il magazzino (trasloelevatori, carrelli)
- [[Analisi ABC (Pareto 80-20)]] — lo stesso strumento applicato alle giacenze
- [[Matrice origine-destinazione]] — i flussi in/out del magazzino
- §6.5 di `Impianti_2026 - 06` · [[06 Cap6 - Layout e flussi di materiali]] · [[_Knowledge Graph v2]] §6.5
