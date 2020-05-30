<template>
  <v-container fluid>
    <v-row>
      <v-card
        v-for="(recipe, i) in recipes"
        :key="i"
        cols="6"
        md="6"
        style="margin: 20px"
        max-width="400"
        :to="recipe.to"
        router
        exact
      >
        <no-ssr>
          <v-img
            class="white--text align-end"
            height="200px"
            :src="recipe.image"
          >
            <v-card-title>{{ recipe.title }}</v-card-title>
          </v-img>
        </no-ssr>

        <v-card-subtitle class="pb-0">
          {{ recipe.author }}
        </v-card-subtitle>

        <v-card-text class="text--primary">
          <div>{{ recipe.description }}</div>
        </v-card-text>

        <v-card-actions>
          <v-btn
            color="green darker-1"
            text
          >
            Ver el vídeo
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    recipes: [
      {
        title: 'Arroz con Chipirones',
        author: '45 min de preparación',
        description: 'Aprenderás cómo hacer un carpaccio de langostinos',
        image: require('~/assets/images/arroz-con-chipirones.jpg'),
        to: '/rice'
      },
      {
        title: 'Steak Tartar',
        author: '15 min de preparación',
        description: 'Una receta buenísima que haras en un momento',
        image: require('~/assets/images/steak-tartar.jpeg'),
        to: '/steak-tartar'
      }
    ]
  })
}
</script>
