<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card>
        <v-card-title class="headline">
          Wordle
        </v-card-title>
        <v-card-text>

          <Guess :guess="guess" :word="word"/>
          <Input @guess="handleGuess"/>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
import { getRandomWord } from '~/utils/words';

export default {
  data: () => ({
    guess: '',
    word: '',
  }),
  fetch() {
    // TODO: utilizzare il metodo getRandomWord() per recuperare la parola corretta
  },
  methods: {
    handleGuess(guess) {
      this.guess = guess
    },
  }
}
</script>
