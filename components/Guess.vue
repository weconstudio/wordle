<template>
  <div class="guess">
    <Char v-for="(char,i) in characters" :key="i" :char="char" :state="states[i]"  />
  </div>
</template>
<style lang="scss">
.guess {
  display: flex;
  gap: 10px;
}
</style>
<script>

import {STATE_MISSING, STATE_CORRECT, STATE_PRESENT} from '~/utils/words'

export default {
  props: {
    guess: {
      type: String,
      required: true,
    },
    // TODO aggiungere la prop word
  },
  computed: {
    characters() {
      if(this.guess.length !== 5)
        return ['', '', '', '', '']

      return this.guess.split('')
    },
    states() {
      // TODO restituire uno stato che descriva ciascun carattere
      // - STATE_MISSING se il carattere non è presente in this.word
      // - STATE_PRESENT se il carattere è presente in this.word ma non è in posizione corretta
      // - STATE_CORRECT se il carattere è presente in this.word ed è in posizione corretta

      return [STATE_MISSING, STATE_MISSING, STATE_MISSING, STATE_MISSING, STATE_MISSING]
    }
  }
}
</script>