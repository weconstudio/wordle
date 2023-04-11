<template>
  <div class="mt-4">
    <v-text-field filled hint="Inserisci una parola di 5 lettere" :error-messages="error ? [error] : []" @keyup.enter="sendGuess" persistent-hint autofocus counter  v-model="guess"></v-text-field>
    <v-btn class="mt-2" color="primary" large block @click="sendGuess">Invia</v-btn>
  </div>
</template>
<script>

import { words } from '~/utils/words'

export default {
  data: () => ({
    guess: '',
    error: null,
  }),
  methods: {
    validateGuess() {
      if(this.guess.length !== 5) {
        this.error = 'La parola deve essere lunga 5 lettere'
        return false
      }

      if(!words.includes(this.guess)) {
        this.error = 'La parola non è valida'
        return false
      }

      return true
    },
    sendGuess() {
      this.error = null

      if(!this.validateGuess()) { return }
      this.$emit('guess', this.guess)
      this.guess = ''
    }
  }
}
</script>