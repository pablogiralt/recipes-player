<template>
  <v-layout>
    <v-flex class="text-center">
      <v-subheader>{{ title }}</v-subheader>
      <Player :steps="steps" :video-id="videoId" />
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
    title: 'Steak Tartar',
    videoId: '424368670',
    steps: [
      {
        title: 'Los Ingredientes',
        offset: 0
      },
      {
        title: 'Picar los ingredientes',
        offset: 43
      },
      {
        title: 'Mezclar los ingredientes',
        offset: 104
      },
      {
        title: 'Emplatar',
        offset: 200
      }
    ]
  })
}
</script>
