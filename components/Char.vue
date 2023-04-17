<template>
  <v-card outlined :color="color" class="char">
    <v-card-text class="text-center">
      <span class="text-xl text-uppercase font-weight-black">{{char}}</span>
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
    state: {
      type: String,
      required: true,
    },
  },
  computed: {
    color() {
      if(this.state === STATE_CORRECT) return 'green'
      if(this.state === STATE_PRESENT) return 'yellow darken-2'
      return undefined
    },
  },
}
</script>

<style lang="scss">
.char{
  flex-grow: 1;
  font-size: 20px !important;
  height: 60px;
  width: 60px;
}
.text-xl{
  font-size: 20px !important;
}
</style>