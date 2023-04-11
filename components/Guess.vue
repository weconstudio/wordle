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
    word: {
      type: String,
      required: true,
    },
  },
  computed: {
    characters() {
      if(this.guess.length !== 5)
        return ['', '', '', '', '']
        
      return this.guess.split('')
    },
    states() {
      if(this.guess.length !== 5)
        return [STATE_MISSING, STATE_MISSING, STATE_MISSING, STATE_MISSING, STATE_MISSING]
        
      return this.characters.map((char, i) => {
        if(this.word[i] === char) return STATE_CORRECT
        if(this.word.includes(char)) return STATE_PRESENT
        return STATE_MISSING
      })
    }
  }
}
</script>