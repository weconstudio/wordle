<template>
  <v-row justify="center" align="center">
    <v-dialog
      v-model="dialog"
        transition="dialog-bottom-transition"
        max-width="750"
      >
      <v-card>
        <v-toolbar
          color="primary"
          dark
        >Wordle</v-toolbar>
        <v-card-text>
          <div class="text-h4 pa-12">Indovina la parola segreta in 6 tentativi!</div>
        </v-card-text>
        <v-card-actions class="justify-end">
          <v-btn
            text
            x-large
            color="primary"
            @click="dialog = false"
          >Inizia!</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    <v-col cols="12" sm="8" md="6">
      <v-card>
        <v-card-text>
          <div>
            <Guess class="mb-2" v-for="(guess, i) in board" :key="i" :guess="guess" :word="word"/>
          </div>
          <Input v-if="!gameOver" @guess="handleGuess"  />
          <v-alert v-else-if="!win" type="error" class="headline mt-4">
            Hai perso! La parola segreta era <b>{{word}}</b>.
          </v-alert>
          <v-alert v-else-if="win" type="success" class="headline mt-4">
            Hai vinto, che occhio!
          </v-alert>
          <v-btn
            v-if="gameOver"
            block
            class="mt-2"
            x-large
            @click="reset"
            color="primary"
          >Gioca di nuovo</v-btn>
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
    dialog: true,
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
