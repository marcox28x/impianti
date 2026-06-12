---
aliases:
  - "Potenzialità produttiva (P)"
  - "ritmo standard di produzione"
  - "Ritmo standard"
  - "Tempi standard di produzione"
---
# Potenzialità produttiva

> [!summary] In 10 secondi
> La **potenzialità produttiva** ($P$) — detta anche *produttività*, *ritmo produttivo standard* o *tasso di attraversamento* (throughput rate) — è il **ritmo atteso di generazione di prodotti**, misurato in volume prodotto fratto tempo. È il mattone di base da cui derivano [[Potenzialità di mix]], [[Capacità produttiva (CP)]] e i conti dell'[[OEE]].

## §1 Domanda fondamentale
A che ritmo "sforna" pezzi una macchina, una linea o un impianto? E quel ritmo è quello **dichiarato dal costruttore** o quello **effettivamente tenuto** in produzione?

## §2 Definizione (§3.2.1 del PDF)
$$P = \frac{\text{volume prodotto}}{\text{tempo}} \qquad (1)$$

È una **prestazione interna**: il cliente non la percepisce direttamente, ma è fondamentale per il management perché misura l'efficienza con cui vengono impiegati gli input. Si tratta di una **misura aggregata**, utile soprattutto al **dimensionamento della capacità produttiva** → si osserva su intervalli **medio-lunghi**, trascurando le variazioni di breve periodo.

### Teorica vs effettiva
| | Riferimento | Significato |
|---|---|---|
| $P$ **teorica** (o massima) | dati di **targa** dell'impianto | velocità teoricamente raggiungibile |
| $P$ **effettiva** | ritmo reale di un periodo | ritmo produttivo mantenuto nel tempo |

## §3 Misure disaggregate (⚠️ punto d'esame)
I fattori produttivi sono **disomogenei** (ore-uomo, ore-macchina, kg di materiale): un indice "assoluto" unico è poco significativo. Per scopi diagnostici si preferisce la **vista disaggregata**:

- **Produttività del lavoro** = volume prodotto / ore-uomo (dirette ∨ totali)
- **Produttività dei macchinari** = volume prodotto / ore-macchina
- **Produttività dei materiali** = volume prodotto / quantità materiali ⇔ **"resa"**

La **produttività complessiva** (da bilancio: valore aggiunto / costi dei fattori) ha **valore diagnostico limitato** → serve scomporre per diagnosticare e poi intervenire.

## §4 Trappole d'esame
> [!warning] ⚠️ TA: doppio significato
> $P$ è un **tasso di attraversamento** [pz/tempo], da non confondere con il **tempo di attraversamento** TA [tempo/pz] di [[Tempo di attraversamento]]. Sono grandezze inverse di natura diversa.

> [!warning] ⚠️ $P \neq 1/TA$ in generale
> Il reciproco della potenzialità coincide col tempo di attraversamento **solo** per una macchina isolata senza *starving* e senza *blocking*. In linea con buffer vale la legge di Little: $WIP = P \cdot TA$.

> [!warning] ⚠️ $TS = 1/P$
> Nel calcolo dell'[[Efficienza prestazioni (Ep)]], il **tempo standard** $TS$ è la distanza temporale fra due uscite = $1/P$. Nel caso multiprodotto si usa $TS = 1/P_{mix}$.

## §5 Collegamenti
### Conseguenze
- [[Potenzialità di mix]] — generalizzazione di $P$ al caso multiprodotto (media armonica pesata)
- [[Capacità produttiva (CP)]] — $CP = P \cdot T_{OVA} = P \cdot TA \cdot TEEP = P \cdot TC \cdot OEE$
- [[Efficienza prestazioni (Ep)]] — usa $TS = 1/P$ come riferimento di velocità di progetto
- [[Tempo di attraversamento]] — la grandezza inversa/duale di $P$

### Vedi anche
- §3.2.1 di `Impianti_2026 - 03` — definizione e misure disaggregate
- [[03 Cap3 - Prestazioni dei sistemi di produzione]] — pagina indice del capitolo
- [[_Knowledge Graph v2]] §3.2.1
