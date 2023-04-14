# WORDLE

## Introduzione

Il workshop prevede la realizzazione guidata di un piccolo gioco di nome Wordle in forma semplificata.

Lo scopo del gioco è quello di indovinare una parola casuale di 5 caratteri.

## Modalità

Per seguire gli step del workshop basterà cambiare il branch quando chiesto.

In ogni step ci sarà la soluzione dello step precedente.

Questo l'elenco dei branch:
- main
- step-1
- step-2
- step-3
- step-4
- step-5

## Avvio ambiente

```bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev

# build for production and launch server
$ yarn build
$ yarn start

# generate static project
$ yarn generate
```

## Step

### main (TODO)

Questo step serve per dare una piccola dimostrazione della reattività del framework Nuxt (Vue)

### step-1

In questo step iniziamo lo sviluppo del progettino Wordle.

In **pages/index.vue** troviamo il codice della pagina principale dove possiamo vedere l'utilizzo di due componenti: Input e Char.

Input è il componente che si occupa di recuperare l'input dell'utente, in questo caso la parola di 5 lettere.

Char è il componente che si occupa di visualizzare una singola lettera della parola inserita dall'utente.

Lo sviluppo necessario è implentare il codice della funzione **validateGuess** all'interno del file **components/Input.vue** che si occupa verificare che la parola inserita dall'utente abbia una lunghezza di 5 caratteri e che questa parola sia presente all'interno di un dizionario già importato.

### step-2

In questo step dobbiamo sviluppare il componente Guess (**components/Guess.vue**) che si occupa di prendere come prop la parola inserita dall'utente, e si occupa di visualizzarla mediante l'utilizzo del componente Char:
- in **components/Guess.vue**
  - nella sezione *template* c'è da spostare il codice da **pages/index.vue** riguardo al componente Char
  - nella sezione *script* ci sarà da implementare la computed **characters** in modo da tornare un array di caratteri derivanti dalla parola inserita dall'utente e passata al componente Guess 
- in **pages/index.vue** ci sarà da sostituire l'utilizzo del componente Char con il componente Guess

### step-3

In questo step andiamo arecuperare una parola randomica dal dizionario e andiamo ad implementare la logica degli indizi sulla parola inserita mediante colorazione dei singoli caratteri:
- in **pages/index.vue** ci sarà da utilizzare la funzione **getRandomWord** per recuperare la parola segreta
- in **components/Guess.vue** c'è da implementare la computed **states** che deve tornare un arrai di costanti in base alle lettere prensenti nella parola inserita dall'utente
- in **components/Char.vue** sarà necessario registrare la nuova prop **state** e quindi gestire la computed **color** in modo che colori il carattere in linea con la prop state passata

### step-4

In questo step andremo a gestire i 6 tentativi che l'utente ha a disposizione. Il lavoro si svolgerà all'interno del file **pages/index.vue**, in particolare:
- c'è da implementare il metodo **handleGuess** andando ad aggiungere l'ultima parola inserita dall'utente all'interno dell'array dei tentativi (guesses)
- c'è da implementare il codice della computed **gameOver** in modo che torni *true* quando il gioco è terminato (il gioco può terminare perchè l'utente ha indovinato la parola o perchè l'utente ha raggionto il massimo numero di tentavi, in questo caso 6)
- c'è da implementare il codice del metodo **reset** in modo che resetti i tentativi ed estragga una nuova parola, permettendo l'utente di giocare nuovamente
- [opzionale] fare in modo che a schermo vengano visualizzati sempre i 6 tentativi
- nella sezione *template*:
  - ci sarà da mostrare la parola corretta in caso di sconfitta
  - ci sarà da aggiungere un pulsante "Gioca di nuovo" che utilizzerà il metodo **reset**

  ### step-5

  In questo step si può vedere la proposta di soluzione finale
