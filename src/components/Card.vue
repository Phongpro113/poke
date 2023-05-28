<template>
  <div class="card">
    <div
      class="card_inner"
      :class="{ 'is-flipped': isFlipped }"
      @click="onTogleFlipCard"
    >
      <div class="card_face card_face--font">
        <div class="card_content"></div>
      </div>
      <div class="card_face card_face--back">
        <div
          class="card_content"
          :style="{
            backgroundImage: `url('${require('@/assets/' + imgBackFaceUrl)}')`,
          }"
        ></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    imgBackFaceUrl: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      isFlipped: false,
    };
  },
  methods: {
    onTogleFlipCard() {
      this.isFlipped = !this.isFlipped;
    },
  },
};
</script>

<style lang="css" scoped>
.card {
  display: inline-block;
  margin-right: 1rem;
  margin-bottom: 1rem;
  width: 90px;
  height: 120px;
}

.card_inner {
  width: 100%;
  height: 100%;
  transition: transform 1s;
  transform-style: preserve-3d;
  cursor: pointer;
  position: relative;
  background-color: #fefefe;
}

.card_inner.is-flipped {
  transform: rotateY(-180deg);
}

.card_face {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  overflow: hidden;
  border-radius: 1rem;
  padding: 1rem;
  box-shadow: 0 3px 10px rgba(0, 0, 0, 0.2);
}

.card_face--back {
  background-color: var(--dark);
  transform: rotateY(-180deg);
}

.card_face--font {
  background-color: blueviolet;
}

.card_face--font .card_content {
  background: url("../assets/images/icon_back.png") no-repeat center center;
  background-size: 40px 40px;
  height: 100%;
  width: 100%;
}
</style>
