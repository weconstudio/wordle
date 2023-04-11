<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card>
        <v-card-title class="headline">
          Wordle
        </v-card-title>
        <v-card-text>
          <div>
            <Guess class="mb-2" v-for="(guess, i) in board" :key="i" :guess="guess" :word="word"/>
          </div>
          <Input @guess="handleGuess"  />
          
          <!-- TODO: mostrare la parola corretta in caso di sconfitta -->

          <!-- TODO: aggiungere pulsante gioca di nuovo che usa il metodo reset visibile quando si è in gameOver  -->
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
import { getRandomWord } from '~/utils/words';

export default {
  data: () => ({
    guesses: [],
    word: '',
  }),
  fetch() {
    this.word = getRandomWord()
  },
  computed: {
    board() {
      // TODO (opzionale) mostrare sempre la board completa con 6 righe
      return this.guesses
    },
    gameOver() {
      // TODO tornare true quando il gioco è finito: il gioco finisce se indovini la parola o raggiungi 6 tentativi
      return false
    },
  },
  methods: {
    handleGuess(guess) {
      // TODO: aggiungere all'array di guesses il nuovo tentativo
    },
    reset() {
      // TODO: implementare il reset del gioco
    },
  }
}
</script>
