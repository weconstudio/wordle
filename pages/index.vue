<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card>
        <v-card-title class="headline">
          Step 2
        </v-card-title>
        <v-card-subtitle>
          Lavoriamo con i componenti
        </v-card-subtitle>
        <v-card-text>
          <!-- TODO: sostituire con un componente dedicato denominato Guess -->
          <div class="guess">
            <Char v-for="(char,i) in characters" :key="i" :char="char" />
          </div>
          <!-- END TODO -->
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
    // TODO: sostituire la variabile di stato characters con una nuova variabile che sarà passata come prop per il componente Guess
    characters: ['', '', '', '', ''],
  }),

  computed: {

  },
  methods: {
    handleGuess(input) {
      // TODO: impostare il valore della nuova variabile con il valore di input
    },
  }
}
</script>
