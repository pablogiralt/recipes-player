<template>
  <div class="player">
    <!-- eslint-disable-next-line vue/no-v-html -->
    <div class="player__player" v-html="test" />
    <v-list>
      <v-list-item
        v-for="(step, i) in steps"
        :key="i"
      >
        <v-list-item-content>
          <v-list-item-title v-text="step.title" />
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </div>
</template>

<style>
</style>

<script>
export default {
  props: {
    // eslint-disable-next-line vue/require-default-prop
    steps: Array
  },
  computed: {
    test () {
      return 'esto es html'
    }
  },
  head: {
    // script: [
    //   { src: 'https://cdnjs.cloudflare.com/ajax/libs/jquery/3.1.1/jquery.min.js' }
    // ]
  }
}
// _1_R0P09zJBHTBttHZx55WInT0RrMlRVaEdkVXRpTXpKWWFGQjJZbkpGYTFObVprdHAn
</script>
