# Funzioni asincrone JavaScript

Il programma JavaScript viene eseguito tutto in un’unica successione di esecuzioni: in termini tecnici, questa cosa viene definita a filo unico, ovvero single-threaded. 

Tutte le operazioni, dall’elaborazione dell’input dell’utente alla visualizzazione del risultato sulla pagina web, sono affidate a questo singolo thread, che scandisce i tempi. L’esecuzione è, quindi, detta **sincrona**.
Per molti impieghi, la sincronia non è un buon modo di eseguire il software. Infatti, le operazioni del software vengono eseguite una dopo l’altra, per cui se alcune richiedono elaborazioni lunghe o bloccate, come richieste di rete, lettura di file o altre operazioni I/O, il resto del programma aspetta il suo turno e resta bloccato.

Per questo motivo, nel linguaggio JavaScript si utilizza la programmazione asincrona: alcune funzioni vengono gestite al di fuori del single thread, eseguito in modo asincrono, migliorando così la reattività e la performance dell'applicazione ed evitando blocchi o altri problemi. 

## Esempi

Sono esempi di funzioni asincrone setTimeout() o fetch().

Eseguendo questo codice: 

```
console.log("primo")
console.log("secondo")
console.log("terzo")
```

La stampa sarà:

primo 

secondo

terzo

Con questo codice invece:

```
console.log("primo")
setTimeout(()=>{ console.log("secondo"), 1000})
console.log("terzo")
```

Ritardare la stampa del secondo nome usando la funzione asincrona *setTimeout()* non ritarda l’esecuzione di ciò che viene dopo: si stampa “primo”, si ritarda di 1s la stampa di “secondo” e quindi si stampa “terzo”. La stampa di “terzo” richiede meno di 1s, per cui la stampa complessiva di questo programma sarà:

primo

terzo

secondo