# Promises

Le Promises sono uno dei pilastri della programmazione asincrona in JavaScript. Una Promise è un oggetto che rappresenta il completamento (o il fallimento) di un'operazione asincrona e il suo risultato. E' un oggetto javascript.

Una Promise in JavaScript è simile a una promessa nella vita reale. Quando facciamo una promessa nella vita reale, è garantito che faremo qualcosa in futuro. Infatti le promesse possono essere fatte solo per il futuro.

Una promessa ha due possibili risultati: quando arriva il momento, può essere mantenuta oppure no.

Questo vale anche per le Promise in JavaScript. Definiamo una Promise e quando arriva il momento, sarà risolta oppure rifiutata.


Un oggetto Promise in JavaScript può essere:

- In sospeso (Pending)
- Completato (Fulfilled)
- Rifiutato (Rejected)

L'oggetto Promise supporta due proprietà: stato (state) e risultato (result).

- Mentre un oggetto Promise è "in sospeso" (sta lavorando), il risultato è indefinito.
- Quando un oggetto Promise è "completato", il risultato è un valore.
- Quando un oggetto Promise è "rifiutato", il risultato è un oggetto errore.

Non è possibile accedere a queste due proprietà. Si deve usare un metodo Promise per gestirle.

Sintassi:

```
let myPromise = new Promise(function(myResolve, myReject) {
// "Producing Code" (May take some time)

  myResolve(); // when successful
  myReject();  // when error
});

// "Consuming Code" (Must wait for a fulfilled Promise)
myPromise.then(
  function(value) { /* code if successful */ },
  function(error) { /* code if some error */ }
);
```

Esempio completo di una Promise:

```
function myDisplayer(some) {
  document.getElementById("demo").innerHTML = some;
}

let myPromise = new Promise(function(myResolve, myReject) {
  let x = 0;

// The producing code (this may take some time)

  if (x == 0) {
    myResolve("OK");
  } else {
    myReject("Error");
  }
});

// "Consuming Code" (Must wait for a fulfilled Promise)
myPromise.then(
  function(value) { /* code if successful */ },
  function(error) { /* code if some error */ }
);

```

# Async e wait

async/await: Introdotti in ECMAScript 2017, sono sintatticamente più puliti e rendono il codice asincrono simile a quello sincrono. La parola chiave async viene utilizzata per dichiarare una funzione asincrona, mentre await viene utilizzata per aspettare una Promise.

```
async function esempioAsync() {
    try {
        let risultato = await promise;
        console.log(risultato);
    } catch (error) {
        console.error(error);
    }
}

esempioAsync();
```

# callback

In programmazione, una callback o richiamo è generalmente una funzione o un "blocco di codice" che viene passato come parametro a un'altra funzione. In particolare, quando ci si riferisce alla callback richiamata da una funzione, la callback viene passata come argomento ad un parametro della funzione chiamante. In questo modo la chiamante può realizzare un compito specifico (quello svolto dalla callback) che non è, molto spesso, noto al momento della scrittura del codice.