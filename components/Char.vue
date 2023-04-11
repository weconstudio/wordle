<template>
  <v-card outlined class="char">
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
export default {
  props: {
    char: {
      type: String,
      required: true,
    },
  },
}
</script>