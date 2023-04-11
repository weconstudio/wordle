<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card>
        <v-card-title class="headline">
          Woordle ({{word}})
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
    this.word = getRandomWord()
  },
  methods: {
    handleGuess(guess) {
      this.guess = guess
    },
  }
}
</script>
