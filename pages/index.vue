<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card>
        <v-card-title class="headline">
          Step 1
        </v-card-title>
        <v-card-subtitle>
          Inserisci una parola nella casella di testo e premi il tasto INVIA. Cosa succede se la parola è troppo lunga?
        </v-card-subtitle>
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

<style lang="scss">
.word {
  display: flex;
  gap: 10px;
}
</style>