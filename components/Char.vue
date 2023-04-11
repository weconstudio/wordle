<template>
  <v-card outlined :color="color" class="char">
    <v-card-text class="text-center">
      <b class="text-xl">{{char}}</b>
    </v-card-text>
  </v-card>
</template>

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