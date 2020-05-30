<template>
  <v-layout>
    <v-flex class="text-center">
      <v-subheader>{{ title }}</v-subheader>
      <Player :steps="steps" />
    </v-flex>
  </v-layout>
</template>

<script>
import Player from '~/components/Player.vue'

export default {
  components: {
    Player
  },
  data: () => ({
    title: 'Arroz con Chipirones',
    steps: [
      {
        title: 'Paso 1'
      },
      {
        title: 'Paso 2'
      },
      {
        title: 'Paso 3'
      },
      {
        title: 'Paso 3'
      }
    ]
  })
}
</script>
