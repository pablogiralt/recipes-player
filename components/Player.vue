/* eslint-disable no-console */
<template>
  <div class="player">
    <v-container fluid>
      <v-row>
        <v-col cols="12" md="6">
          <div class="player__wrapper">
            <no-ssr>
              <vimeo-player
                ref="player"
                :video-id="videoID"
                :options="options"
                @ready="onReady"
                @timeupdate="onTimeupdateHandler"
              />
            </no-ssr>
            <div v-if="overlayVisible" class="player__overlay">
              <div class="player__overlay-actions">
                <v-btn
                  text
                  x-large
                  color="error"
                  @click="play()"
                >
                  <v-icon center x-large>
                    mdi-play
                  </v-icon>
                </v-btn>

                <v-btn
                  text
                  x-large
                  color="error"
                  @click="goToStep(-1, 'relative')"
                >
                  <v-icon center x-large>
                    mdi-replay
                  </v-icon>
                </v-btn>
              </div>
            </div>
          </div>

          <v-btn
            v-if="currentStep > 0"
            depressed
            color="error"
            @click="goToStep(-1, 'relative')"
          >
            <v-icon left>
              mdi-step-backward
            </v-icon>
            Anterior
          </v-btn>
          <v-btn
            depressed
            color="error"
            @click="play()"
          >
            <v-icon center>
              mdi-play
            </v-icon>
          </v-btn>
          <v-btn
            depressed
            color="error"
            @click="pause()"
          >
            <v-icon center>
              mdi-pause
            </v-icon>
          </v-btn>

          <v-btn
            depressed
            color="error"
            @click="goToStep(0, 'relative')"
          >
            <v-icon center>
              mdi-replay
            </v-icon>
          </v-btn>

          <v-btn
            v-if="currentStep <= steps.length"
            depressed
            color="error"
            @click="goToStep(1, 'relative')"
          >
            Siguiente
            <v-icon right>
              mdi-step-forward
            </v-icon>
          </v-btn>
        </v-col>

        <v-col cols="12" md="6">
          <v-list>
            <v-list-item
              v-for="(step, i) in steps"
              :key="i"
              @click="goToStep(i, 'absolute')"
            >
              <v-list-item-content>
                <v-list-item-title v-text="i+1 + '. ' + step.title" />
              </v-list-item-content>
            </v-list-item>
          </v-list>
        </v-col>
      </v-row>
    </v-container>
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
  data () {
    return {
      videoID: '424289228',
      playerReady: false,
      options: {
        title: false,
        byline: false,
        playsinline: true
      },
      currentStep: 0,
      stepIndex: [],
      stepMode: true,
      overlayVisible: false
    }
  },
  computed: {},
  methods: {
    onReady () {
      this.playerReady = true
      const _this = this
      this.steps.forEach((step, index) => _this.stepIndex.push(step.offset))
    },
    goToStep (step, type) {
      if (type === 'relative') {
        this.currentStep = this.currentStep + step
      } else {
        this.currentStep = step
      }

      this.goTo(this.steps[this.currentStep].offset)
    },
    goTo (seconds) {
      const player = this.$refs.player
      player.player.setCurrentTime(seconds).then(function () {
        return this.play()
        // return player.play()
      })
    },
    play () {
      this.overlayVisible = false
      this.$refs.player.play()
    },
    pause () {
      this.$refs.player.pause()
    },
    onTimeupdateHandler (event, data, player) {
      const currentSec = Math.round(event.seconds)
      // console.log(currentSec, this.steps[this.currentStep].offset)
      if (this.stepIndex.includes(currentSec) && this.steps[this.currentStep].offset < currentSec) {
        this.currentStep++
        if (this.stepMode) {
          this.pause()
          this.overlayVisible = true
        }
      }
    }
  }
}
</script>

<style scoped>
  .player__wrapper {
    position: relative;
  }
  .player__overlay {
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: rgba(0,0,0,0.8);
  }
  .player__overlay-actions {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%,-50%);
  }
</style>
