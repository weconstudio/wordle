<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card>
        <v-card-title class="headline">
          Woordle
        </v-card-title>
        <v-card-text>

          <Guess :guess="guess" />
          <Input @guess="handleGuess"/>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>

export default {
  data: () => ({
    guess: '',
  }),
  
  computed: {
    
  },
  methods: {
    handleGuess(guess) {
      this.guess = guess
    },
  }
}
</script>
