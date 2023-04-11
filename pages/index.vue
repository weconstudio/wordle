<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card>
        <v-card-title class="headline">
          Woordle
        </v-card-title>
        <v-card-text>
          <div>
            <Guess class="mb-2" v-for="(guess, i) in board" :key="i" :guess="guess" :word="word"/>
          </div>
          <Input v-if="!gameOver" @guess="handleGuess"  />
          <div v-else-if="!win" class="headline mt-4">
          La parola era  <b>{{word}}</b>. Hai perso!
            
          </div>
          <v-btn v-if="gameOver" block class="mt-2" @click="reset">Gioca di nuovo</v-btn>
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
      const empty = Array(6- this.guesses.length).fill('')
      return [...this.guesses, ...empty]
    },
    reachedMaxGuesses() {
      return this.guesses.length >= 6
    },
    win() {
      return this.guesses.includes(this.word)
    },
    gameOver() {
      return this.guesses.includes(this.word) || this.guesses.length >= 6
    },
  },
  methods: {
    handleGuess(guess) {
      this.guesses.push(guess)
    },
    reset() {
      this.guesses = []
      this.word = getRandomWord()
    },
  }
}
</script>
