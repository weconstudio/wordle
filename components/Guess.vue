<template>
  <!-- Usare il componente Char per mostrare i caratteri di guess (computed characters) -->
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
      // TODO: tornare l'array dei caratteri di this.guess

      return ['a', 'b', 'c', 'd', 'e']
    },
  }
}
</script>