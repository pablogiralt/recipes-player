<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" app>
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      v-model="isActive"
      app
      hide-on-scroll
      color="green darken-1"
      :class="{'header-visible' : headerVisible}"
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title>Foodie Player</v-toolbar-title>
    </v-app-bar>

    <v-content>
      <v-container class="fill-height" fluid>
        <nuxt />
      </v-container>
    </v-content>
    <v-footer absolute color="green darken-1" app>
      <span class="white--text">&copy; 2019</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  props: {
    // eslint-disable-next-line vue/require-default-prop
    source: String
  },
  data: () => ({
    drawer: false,
    headerVisible: true,
    isActive: true,
    items: [
      {
        icon: 'mdi-format-list-bulleted-type',
        title: 'Todas las recetas',
        to: '/'
      },
      {
        icon: 'mdi-rice',
        title: 'Arroz con Chipirones',
        to: '/rice'
      },
      {
        icon: 'mdi-food-steak',
        title: 'Steak Tartar',
        to: '/steak-tartar'
      }
    ]
  }),
  computed: {
  },
  created () {
    this.$nuxt.$on('fullscreenMode', (fullscreenMode) => {
      if (fullscreenMode) {
        this.isActive = 0
      }
    })
  },
  methods: {
  }
}
</script>
