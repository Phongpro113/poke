<script setup>
import MainScreen from "./components/MainScreen.vue"
import InteractScreen from "./components/InteractScreen.vue";
import { shuffled } from "./utils/array"
</script>

<template>
  <MainScreen v-if="statusMatch === 'default'" @onStart="onHandleBeforeStart($event)" />
  <InteractScreen v-if="statusMatch === 'match'" :cardsContext="settings.cardsContext" />
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      statusMatch: "default",
      settings: {
        totalOfBlocks: 0,
        cardsContext: [],
        startedAt: null
      }
    }
  },
  methods: {
    onHandleBeforeStart(config) {
      console.log("running hande before start, ", config);
      this.settings.totalOfBlocks = config.totalOfBlocks;

      const firstCards = Array.from(
        { length: this.settings.totalOfBlocks / 2 }, 
        (_, i) => i + 1
      )

      const secondCards = [...firstCards];
      const cards = [...firstCards, ...secondCards];

      this.settings.cardsContext = shuffled(shuffled(shuffled(shuffled(cards))))
      this.settings.startedAt - new Date().getTime()

      this.statusMatch = 'match'
    }
  }
}
</script>