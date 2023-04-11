<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card>
        <v-card-title class="headline">
          Scrivi il tuo nome
        </v-card-title>
        <v-card-text>
          <v-text-field filled label="Nome" v-model="name"></v-text-field>
          <v-divider class="mb-4"></v-divider>
          <template v-if="name">
            <h1>CIAO {{ nameUppercase }}!</h1>
            <v-btn class="mt-4" color="primary" @click="reset">Resetta</v-btn>
          </template>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  data: () => ({
    name: ''
  }),
  computed: {
    nameUppercase() {
      return this.name.toUpperCase()
    }
  },
  methods: {
    reset() {
      this.name = ''
    },
  }
}
</script>
