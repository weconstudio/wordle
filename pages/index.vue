<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card>
        <v-card-title class="headline">
          Wordle
        </v-card-title>
        <v-card-text>

          <div class="word">
            <Char v-for="(char,i) in characters" :key="i" :char="char" />
          </div>
          <Input @guess="handleGuess"/>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>
<style lang="scss">
.word {
  display: flex;
  gap: 10px;
}
</style>

<script>

export default {
  data: () => ({
    
    characters: ['', '', '', '', ''],
  }),
  
  computed: {
    
  },
  methods: {
    handleGuess(guess) {
      this.characters = guess.split('')
    },
  }
}
</script>
