<template>
  <v-card outlined :color="color" class="char">
    <v-card-text class="text-center">
      <b class="text-xl">{{char}}</b>
    </v-card-text>
  </v-card>
</template>

<script>
import { STATE_CORRECT, STATE_PRESENT} from '~/utils/words'

export default {
  props: {
    char: {
      type: String,
      required: true,
    },
    // TODO aggiungere la prop state
  },
  computed: {
    color() {
      // TODO restituire il colore in base allo stato
      return undefined
    },
  },
}
</script>

<style lang="scss">
.char{
  flex-grow: 1;
  font-size: 20px !important;
  min-height: 60px;
}
.text-xl{
  font-size: 20px !important;
}
</style>