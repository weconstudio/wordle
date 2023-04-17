<template>
  <!-- TODO: usare il componente Char per mostrare i singoli caratteri della prop guess utilizzando la variabile computed characters -->
  <div></div>
</template>
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
      // TODO: restituire un array contenente di caratteri di this.guess
      // es: PESCA => ['P', 'E', 'S', 'C', 'A']
      // TODO: se this.guess è vuoto, restituire un array di 5 stringhe vuote

      return ['a', 'b', 'c', 'd', 'e']
    },
  }
}
</script>