---
aliases:
  - "Break Even Point"
  - "Volume critico Q*"
  - "Layout per processo vs per prodotto"
---

No, non è (in primo luogo) una questione di margine: è una questione di **costo per pezzo**. Il margine c'entra, ma in modo diverso da come lo stai immaginando — ci arrivo alla fine.

Il punto è che robot e operatore hanno strutture di costo opposte. Il robot ha un grosso investimento iniziale (costo _fisso_, indipendente da quanti pezzi fai) ma un costo variabile per pezzo bassissimo (energia, supervisione minima). L'operatore è il rovescio: investimento ≈ 0, ma alto costo variabile per pezzo, perché la manodopera la paghi su _ogni_ singolo pezzo.

Il costo unitario del robot è quindi CF/Q + c_var. Il pezzo che "ti costa caro" non è il robot in sé, è il termine CF/Q — e quel termine crolla all'aumentare di Q. "Assorbire" il costo del macchinario vuol dire esattamente questo: spalmare l'investimento fisso su tante unità finché il costo per pezzo scende sotto quello manuale.

Con numeri tondi, su un assemblaggio di schede elettroniche:

- Robot: investimento ammortizzato CF = 500.000 €/anno, c_robot = 0,50 €/pz
- Manuale: CF ≈ 0, c_manuale = 5 €/pz

Il robot risparmia 4,50 € su ogni pezzo, e pareggia quando il risparmio totale copre l'investimento: Q* = 500.000 / (5 − 0,50) ≈ **111.000 pz/anno**.

- A 10.000 pz/anno → robot = 500.000 + 0,50·10.000 = 505.000 € → 50,5 €/pz. Manuale = 50.000 € → 5 €/pz. Vince il manuale, e di parecchio.
- A 1.000.000 pz/anno → robot = 1.000.000 € → 1 €/pz. Manuale = 5.000.000 € → 5 €/pz. Vince il robot, e di parecchio.

Nota la cosa decisiva: il prezzo di vendita non è mai entrato nel conto. Sto confrontando due modi di fare lo _stesso_ pezzo, vendibile allo _stesso_ prezzo: il ricavo è identico nei due scenari, quindi si elide e resta solo da minimizzare il costo. Per questo è una decisione di costo, non di margine.

È esattamente il compromesso del **Cap 4** tra _costi di investimento_ (risorse usate a prescindere dal volume — macchinari, attrezzature) e _costi di produzione_ (risorse variabili col volume — materie prime, energia): investire di più ti garantisce, a parità di produzione, un costo per unità più basso. Lo ritrovi come **economie di scala** nel Cap 2 (↑volumi → ↓costo unitario, produzioni _capital intensive_) e in forma grafica nell'**analisi CVP** del Cap 6 — il robot è la retta ad alto costo fisso e bassa pendenza (come il layout in linea), l'operatore quella a basso costo fisso e alta pendenza (come il layout per reparti). Il tuo Q* è il _volume critico_ oltre cui conviene passare all'automazione.

E il margine, allora? La tua intuizione non è campata in aria, ma entra in due punti diversi: per decidere _se_ produrre serve p > c (ma questo vale identico col robot e a mano, quindi non discrimina tra i due); e un margine alto ti dà "slack", cioè puoi permetterti di restare con un metodo meno efficiente senza andare in perdita — ma questo è _tollerare_ l'inefficienza, non _giustificare_ l'investimento.

La sintesi precisa è questa: ciò che ripaga il robot è il risparmio per pezzo (c_manuale − c_robot) **moltiplicato per il volume**. Il volume non è un'alternativa al margine, è il moltiplicatore che trasforma un vantaggio di pochi centesimi a pezzo in un risparmio totale abbastanza grande da coprire l'investimento. Su un solo pezzo, 4,50 € contro 500.000 € non basta mai; su un milione di pezzi, sì.