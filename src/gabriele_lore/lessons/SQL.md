SQL, acronimo di Structured Query Language è un linguaggio standardizzato per database basati sul modello relazionale (RDBMS), progettato per le seguenti operazioni:

- creare e modificare schemi di database
- inserire, modificare e gestire dati memorizzati
- interrogare i dati memorizzati 
- creare e gestire strumenti di controllo e accesso ai dati

A dispetto del nome, non si tratta perciò di un semplice linguaggio di interrogazione: alcuni suoi sottoinsiemi, infatti, permettono di creare, gestire e amministrare database.

# Comandi

Per manipolare i dati abbiamo dei comandi.

## Insert

Il comando ha la funzione di inserire i dati nelle tabelle.

Le colonne (o campi) di destinazione dei valori possono essere o meno dichiarate nel comando. Se non vengono dichiarate, è necessario passare al comando un valore per ogni colonna della tabella, rispettando rigorosamente l'ordine delle colonne stesse. Se, invece, le colonne di destinazione vengono dichiarate, è possibile indicare le sole colonne per le quali vengono passati dei valori, purché vengano inseriti comunque i valori per tutte le colonne not null (che non possono essere nulle) della tabella.

Di per sé il comando insert opera inserendo in tabella una sola riga per volta. È possibile, però, inserire più di una riga "in modo automatico" passando all'insert una serie di righe (o tuple) risultanti da un comando di select, purché tali righe siano compatibili con le colonne della tabella su cui si inseriscono i dati.

Sintassi:
`INSERT INTO nome_tabella VALUES (elenco valori, tutti, rispettando l’ordine dei campi della tabella, ad es "donato");

## Update

Il comando update ha la triplice funzione di modificare i dati delle tabelle.

Il nome di ogni campo che deve essere modificato va dichiarato dopo la parola chiave SET e deve essere seguito dal simbolo = (uguale) e dal nuovo valore che deve assumere.

È possibile modificare più campi della stessa riga in un unico comando update, separandoli l'uno dall'altro con il simbolo , (virgola).

Il comando generico aggiorna tutte le righe della tabella. È possibile restringerne il numero applicando la parola chiave aggiuntiva WHERE, che permette di effettuare una selezione qualitativa delle righe imponendo delle condizioni sui dati presenti nelle righe prima dell'aggiornamento.

Sintassi:
`
UPDATE nome_tabella
SET nome_campo1 = 'valore1_nuovo',
    nome_campo2 = 'valore2_nuovo',
     ...
;
`

## Delete

Il comando delete ha la funzione di cancellare i dati dalle tabelle.

Come il comando update anche delete può operare in modo generico cancellando tutte le righe della tabella oppure può identificare le righe da cancellare mediante la parola chiave aggiuntiva WHERE e la condizione (o le condizioni) ad essa associata.

Sintassi:
`
DELETE FROM nome_tabella;
`

Delete con condizione:
`
DELETE FROM nome_tabella
WHERE nome_campo = 'valore';
`

# Tabelle

Per manipolare tabelle abbiamo dei comandi.

## Creazione tabelle

`
CREATE TABLE users (
    id SERIAL PRIMARY_KEY
    title VARCHAR(50) NOT NULL
    content VARCHAR(255) NOT NULL
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP 
) 
`

# Interrogazione dei dati

Si usa il select per prendere dati dal database.

`
SELECT nome_colonne FROM nome_tabella
`
Si possono usare anche qui le condizioni. Con `*` si selezionano tutte le colonne.

# Operatori

Gli operatori, messi a disposizione dal SQL standard si dividono in sette categorie:

- Operatori di assegnazione
- Operatori di confronto
- Operatori stringa
- Operatori aritmetici
- Operatori condizionali
- Operatori logici
- Operatori tra bit

## Operatori di assegnazione
  
Gli operatori di assegnazione assegnano un valore a una variabile o a un campo.

- `=` Esprime un'assegnazione e non restituisce alcun valore.
- `:=` Esprime un'assegnazione di un valore ad una variabile non ancora istanziata e non restituisce alcun valore.

## Operatori di confronto

Gli operatori di confronto servono a determinare uguaglianze e disuguaglianze tra valori e ad effettuare ricerche all'interno dei dati. Di seguito uno schema tabellare:

- `=` Esprime uguaglianza tra due valori numerici o stringhe di caratteri (dove non è usato come operatore di assegnazione)
- `IS` Si usa per verificare se un valore è NULL, oppure se corrisponde a un valore booleano (TRUE, FALSE, UNKNOWN).
- `LIKE` Esprime somiglianza tra due valori letterali: con l'operatore LIKE è possibile usare, per i confronti, i caratteri speciali `%` (sostituisce un arbitrario numero di lettere) e `_` (sostituisce una lettera arbitraria)
- `<` Stabilisce se un valore è minore di un altro
- `>` Stabilisce se un valore è maggiore di un altro
- `<=` Stabilisce se un valore è minore o uguale di un altro
- `>=` Stabilisce se un valore è maggiore o uguale di un altro
- `<>` o `!=` stabilisce se due valori sono diversi tra loro
- `BETWEEN ... AND` Recupera un valore compreso tra due valori
- `IN` Stabilisce se un valore è contenuto in una lista di valori possibili

Ad alcuni di questi operatori corrisponde un operatore contrario che fa uso del termine NOT:

- `IS NOT`
- `NOT LIKE`
- `NOT BETWEEN`
- `NOT IN`
- `NOT EXISTS`

## Operatori aritmetici

Gli operatori aritmetici accettano operatori di un tipo numerico (interi o decimali) e restituiscono il risultato dell'operazione aritmetica corrispondente.

- `+`: Effettua un'addizione, o lascia immutato il segno di un numero
- `-` Effettua una sottrazione, o inverte il segno di un numero
- `*` Effettua una moltiplicazione
- `/` Effettua una divisione
- `MOD` Restituisce il resto di una divisione
- `DIV` Restituisce la parte intera di una divisione
  
## Operatori condizionali

L'unico operatore condizionale di SQL è WHERE (dove) e serve a definire criteri di ricerca mirati.

## Operatori logici

Gli operatori logici di SQL appartengono agli operatori logici booleani e sono:

- L'operatore logico AND, che lega due condizioni, restituisce il valore TRUE se e solo se entrambi gli operandi sono veri.
- L'operatore logico OR, che lega due condizioni, restituisce TRUE se e solo se almeno uno degli operandi è vero.
- L'operatore NOT accetta un solo operando e restituisce il valore inverso: falso se questo è vero, vero se questo è falso.
- L'operatore XOR, che accetta due condizioni, restituisce TRUE se e solo se uno solo degli operandi è vero.

L'uso delle parentesi tonde ( ) all'interno delle espressioni di ricerca consente di modificare o esplicitare la precedenza degli operatori, ossia l'ordine in cui essi vengono elaborati. Ove un'espressione composta sia scritta senza parentesi, vengono applicate le precedenze tra gli operatori previste dal linguaggio.
