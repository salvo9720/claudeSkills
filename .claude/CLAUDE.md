# Regole di scrittura codice
## chiarezza e leggibilita
Quando lavori su questa codebase, la leggibilita e chairezza di quello che si fa hanno la priorita massima.
L'approccio preferenziale quando si approccia un nuovo task è quello del minimal changes, se devi apportare dei cambiamenti, devi sempre provare a ridurre al minimo possibile il codice che scrivi, senza compromettere la sua leggibilita.
Se dei passaggi sono troppi complessi aggiungere 1-2 righe per fare tutto in step piu semplici va bene, perche ne aumenta la leggibilita.

### scrittura su dom HMTL
- come regola principale vale il fai il piu possibbile nel file html ed evita di lavorare nel ts per rendirizzare dei dati dell'html.
Questo quando il codice ts non va ad impattare.
Potrebbero capitare siutazioni tipo angualr 13 ha un check di tipo e quindi il codice html viene rilevato per infererenza sbaglaito, in questo caso sei autorizzato a mettere la funzione nel ts e farlo li, quando si verifica questo punto la prima riga della funzione deve essere: 
``` typescript
// angualr inference type case error in html file for this declaration
```


# Regole espressamente vietate:
1) wrapper function.
2) manipolare i dati provenienti da un api: il tuo compito di solito sara quello di fare da passacarte e mostrarli nel dom html, se credi che vado modificati chiedi all'untente.