---
tags: [impianti, cap1, qualitativo]
tipo: atomic-note
capitolo: "[[01 Cap1 - Introduzione ai sistemi di produzione]]"
aliases:
  - "Aggiornamento rolling"
  - "Pianificazione rolling"
---
# Rolling planning

> [!tldr] In 10 secondi
> I tre orizzonti di [[Pianificazione - Programmazione - Scheduling|pianificazione]] non sono in sequenza ma **in parallelo**, ricalcolati a scorrimento man mano che arrivano nuovi dati.

## Cos'è (§1.1)
Modalità di aggiornamento del ciclo di pianificazione: anziché pianificare una volta per l'intero orizzonte, si **ripianifica periodicamente** facendo scorrere in avanti la finestra temporale, integrando previsioni e consuntivi aggiornati.

```
[[Pianificazione - Programmazione - Scheduling]]  →  3 orizzonti IN PARALLELO
  + aggiornamento ROLLING (a scorrimento)
  + sistema di controllo delle prestazioni (economiche / produttive / logistiche)
```

## Perché serve
- Domanda incerta ed evolutiva → i piani invecchiano in fretta
- Lo scorrimento mantiene allineati lungo / medio / breve termine
- Si appoggia al feedback del sistema di controllo: scostamenti → correzioni

## Collegamenti
- PRIMA: [[Pianificazione - Programmazione - Scheduling]]
- CORRELATO: [[Contesto Competitivo]]
