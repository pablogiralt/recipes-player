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
        title: 'Los Ingredientes',
        offset: 0
      },
      {
        title: 'Calentar el caldo',
        offset: 25
      },
      {
        title: 'Pelar los langostinos',
        offset: 42
      },
      {
        title: 'Carpaccio de Langostinos',
        offset: 55
      },
      {
        title: 'Jugo de marisco: Sofreir',
        offset: 129
      },
      {
        title: 'Jugo de marisco: Exprimir',
        offset: 172
      },
      {
        title: 'Sofrito: Preparar ingredientes',
        offset: 235
      },
      {
        title: 'Sofrito: Cebolla',
        offset: 289
      },
      {
        title: 'Sofrito: Chipirón',
        offset: 343
      },
      {
        title: 'Sofrito: Arroz',
        offset: 414
      },
      {
        title: 'Cocer el arroz',
        offset: 510
      },
      {
        title: 'Añadir el Pilpil',
        offset: 682
      },
      {
        title: 'Emplatar',
        offset: 740
      }
    ]
  })
}
</script>
