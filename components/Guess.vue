<template>
  <div class="guess">
    <Char v-for="(char,i) in characters" :key="i" :char="char" />
  </div>
</template>
<style lang="scss">
.guess {
  display: flex;
  gap: 10px;
}
</style>
<script>
export default {
  props: {
    guess: {
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
  }
}
</script>