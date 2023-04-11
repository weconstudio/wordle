<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card>
        <v-card-title class="headline">
          Woordle
        </v-card-title>
        <v-card-text>

          <div class="guess">
            <Char v-for="(char,i) in characters" :key="i" :char="char" />
          </div>
          <Input @guess="handleGuess"/>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>
<style lang="scss">
.guess {
  display: flex;
  gap: 10px;
}
</style>

<script>

export default {
  data: () => ({
    // TODO: adattare lo stato per il nuovo componente Guess.vue 
    characters: ['', '', '', '', ''],
  }),
  
  computed: {
    
  },
  methods: {
    handleGuess(guess) {
      // TODO: passare "guess" come prop al nuovo componente Guess.vue 
    },
  }
}
</script>
