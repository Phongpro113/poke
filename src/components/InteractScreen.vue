<template>
  <div class="cre">
    <h1>interface component here ...</h1>
    <cardflip
      v-for="(card, index) in cardsContext"
      :key="index"
      :imgBackFaceUrl="`images/${card}.png`"
    />
  </div>
</template>
<script>
import cardflip from "./Card.vue";
export default {
  props: {
    cardsContext: {
      type: Array,
      default: function () {
        return [];
      },
    },
  },
  components: {
    cardflip,
  },
};
</script>
