---
name: i18n-angular
description: Gestisce i file JSON di traduzione (i18n) del progetto Angular basato su ngx-translate, in src/assets/i18n/. Usa questa skill quando l'utente chiede di aggiungere, modificare, rinominare testi visibili nell'interfaccia, anche senza dire "i18n" o "traduzione" (es. "cambia questa label", "questo testo è hardcoded"). Usa anche per sincronizzare chiavi tra lingue o pulire chiavi non usate.
---

# i18n-angular

- Quando viene richeisto di creare i lang o i18n:
1. usare la cartella src del progetto
2. sostituire tutte le strighe hardcoded prima in tutti gli html e successivamente nei file ts.

## Struttura

`src/assets/i18n/<lingua>.json` (es. `it.json`, `en.json`). Stessa struttura di chiavi in tutte le lingue, cambia solo il valore.

```json
{
  "components": {
    "userProfile": {
      "saveButton": "Salva modifiche"
    }
  }
}
```

- Chiavi in lowerCamelCase.
- Nome componente = nome del file kebab-case convertito in lowerCamelCase (`user-profile.component.ts` → `userProfile`).
- Chiave parlante sul contenuto, non generica (`saveButton`, non `text1`).
- Sezione già esistente per quel componente → aggiungi lì, non duplicare.

## Uso nel codice

Template: `{{ 'components.userProfile.saveButton' | translate }}`
TS: `this.translate.instant('components.userProfile.saveButton')`

Variabili: `"welcomeUser": "Benvenuto, {{name}}!"` → `{{ 'components.loginPage.welcomeUser' | translate: { name: user.name } }}`

## Flusso nuova installazione e creazione file di lang

1. Leggi tutti i file lingua in `src/assets/i18n/`.
2. Trova o crea la sezione del componente.
3. Aggiungi/modifica la chiave in **tutte** le lingue (se manca il testo per una lingua, traduci tu e segnalalo come da rivedere).
4. Aggiorna in `src` ogni punto (template + TS) che usava il testo hardcoded o la vecchia chiave.
5. Controlla che tutte le lingue abbiano le stesse chiavi. Chiavi orfane trovate → segnala, non rimuovere senza conferma.

## Flusso migrazioni chiavi 
1. verifica che tutti i file di lang abbiamo le stess chiavi. 
2. scegline uno e salva in un json una mappa con vecchie chiavi e nuove.
3. applica le modifiche e aggirona le chiavi basandoti sui file. 

## Flusso aggiunta chiavi in i18n gia configurato o presente
1. Quando si verifica l'aggiunta di una chaive verifica se il compoente ha gia la sua chaive creata.
2. tra questi verifica i valori di traduzione se ne trovi uno ugaule a 100% della striga da aiigunere usa quella, altrimenti crea la chaive sotto la chaive del nome del componente.

## Direttive di escusione
Quanto trovi nel codice cose come:
- isDevmode(): significa codice solo per la modalita sviluppo, non lavorare su questa linea.