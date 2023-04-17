# Workshop Vue.js: WORDLE

## Introduzione

Lo scopo di questo repository è quello di contenere il materiale di supporto per il workshop a tema Vue.js durante il quale è prevista la realizzazione guidata e semplificata di un clone in lingua italiana del puzzle game Wordle (https://www.nytimes.com/games/wordle/index.html).

Lo scopo del gioco è quello di indovinare in 6 tentativi una parola di 5 caratteri estratta a caso da un dizionario. Per ogni tentativo sarà possibile utilizzare solo parole di senso compiuto e il gioco fornirà alcune indicazioni riguardanti l'esattezza delle lettere introdotte.

Nell'esempio che segue è stato eseguito un tentativo con la parola "FRANO". Lo sfondo giallo indica che la parola misteriosa contiene la lettera `R` ma non in seconda posizione. Lo sfondo verde indica che la lettera `O` è presente proprio in quinta posizione.

<img width="545" alt="image" src="https://user-images.githubusercontent.com/3984889/232073784-67e651d2-acbb-4db3-97ae-529925e23011.png">

## Modalità di svolgimento del workshop

Per iniziare clona questo repository ed esegui il checkout dei branch successivi quando richiesto.

Ogni branch numerato da 1 a 5 (step-1, step-2, ...) contiene la soluzione per quello precedente.

Il branch main contiene una semplice dimostrazione della reattività di Vue.js.

## Avvio ambiente

Clona questo repository (o aggiornalo con `git pull` se lo hai clonato in precedenza) e, in base al package manager di cui disponi, segui i seguenti passi per iniziare a lavorare.
```bash
# clonazione del repository
$ git clone https://github.com/weconstudio/wordle.git

# apro la cartella del progetto con VSCode
$ code wordle
```

### yarn

```bash
# installazione delle dipendenze
$ yarn install

# avvio di un server per lo sviluppo con hot reload
$ yarn dev
```

Navigando all'indirizzo `http://localhost:3000` potrai vedere l'applicazione in azione.

### npm

```bash
# installazione delle dipendenze
$ npm install

# avvio di un server per lo sviluppo con hot reload
$ npm run dev
```

Navigando all'indirizzo `http://localhost:3000` potrai vedere l'applicazione in azione.

## Step

Per passare da uno step a un altro è sufficiente cambiare il branch corrente. Per esempio per passare al primo step è sufficiente digitare:

```bash
$ git checkout step-1
branch 'step-1' set up to track 'origin/step-1'.
Switched to a new branch 'step-1'
```

Se hai effettuato delle modifiche al codice che vuoi mantenere per uso futuro non dimenticare di eseguire un'operazione di commit prima del checkout.

```bash
$ git commit -a -m "le mie modifiche!"
[step-1 7676ec8] le mie modifiche
 2 files changed, 7686 insertions(+), 7420 deletions(-)
```

Se vuoi scartare le tue modifiche effettua la seguente operazione prima del checkout.

```bash
$ git reset --hard
HEAD is now at 2089393 feat: README
```

### step-1

Iniziamo con lo sviluppo del nostro progetto Wordle!

In `pages/index.vue` troviamo il codice della pagina principale che include due componenti: Input (`components/Input.vue`) e Char (`components/Char.vue`).

Input è il componente che si occupa di recuperare l'input dell'utente, in questo caso la parola di 5 lettere.
Char è il componente che si occupa di visualizzare la parola inserita dall'utente lettera per lettera.

#### Obiettivo
Scrivere il codice della funzione `validateGuess()` nel componente `Input` in modo che verifichi che la parola inserita dall'utente abbia una lunghezza di esattamente 5 caratteri e che questa parola sia presente all'interno del dizionario contenuto nella variabile importata `words`.

### step-2

In questo step dobbiamo sviluppare il componente `Guess` (`components/Guess.vue`) che si occupa di ricevere la parola inserita dall'utente sotto forma di `prop`, e si occupa di visualizzarla mediante l'utilizzo del componente `Char`.

#### Obiettivo

Apportare le seguenti modifiche al codice
- in `components/Guess.vue`
  - sezione `template`: inserire il codice relativo al componente `Char` ora presenti in `pages/index.vue`
  - sezione `script`: implementare la computed property `characters` in modo che restituisca un array di caratteri corrispondenti alla parola inserita dall'utente 
- in `pages/index.vue` sostituire l'utilizzo del componente `Char` con il componente Guess

### step-3

In questo step selezioniamo casualmente una parola dal dizionario e implementiamo la logica di colorazione dei caratteri.

#### Obiettivo

Apportare le seguenti modifiche al codice
- in `pages/index.vue`: utilizzare la funzione `getRandomWord()` per recuperare la parola segreta
- in `components/Guess.vue`: implementare la computed property `states` in modo che restituisca un array di costanti in base alla correttezza delle lettere della parola inserita dall'utente
- in `components/Char.vue` registrare la nuova prop `state` e quindi gestire la computed property `color` in modo che colori opportunamente il carattere

### step-4

In questo step gestiremo i 6 tentativi che l'utente ha a disposizione. Il lavoro si concentrerà sul file `pages/index.vue`.

#### Obiettivo
Apportare le seguenti modifiche al codice

- implementare il metodo `handleGuess()` aggiungendo il tentativo più recente in fondo all'array dei tentativi `guesses`
- implementare il codice della computed property `gameOver` in modo che restituisca `true` quando il gioco è terminato (il gioco termina quando l'utente indovina la parola o raggiunge 6 tentativi)
- implementare il codice del metodo `reset()` in modo che avvii una nuova sessione di gioco svuotando l'array dei tentativi ed estraendo una nuova parola,
- [opzionale] fare in modo che a schermo vengano visualizzati sempre i 6 tentativi
- nella sezione `template`:
  - mostrare la soluzione in caso di sconfitta
  - aggiungere un pulsante "Gioca di nuovo" che invoca al click il metodo `reset()`

### step-5

Passa a questo step per vedere la soluzione finale e divertiti a giocare con Wordle!
