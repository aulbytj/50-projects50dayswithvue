<template>
  <div class="container">
    <div
      class="panel"
      @click="toggleActive(idx)"
      :class="{ active: idx === isActive}"
      :style="{ backgroundImage: 'url(' + card.img + ')' }"
      v-for="(card, idx) in cards"
      :key="idx"
    >
      <h3>{{ card.title }}</h3>
    </div>
  </div>
</template>

<script>
import store from "@/store.js";
export default {
  data() {
    return {
      cards: store.cards,
      isActive: 0,
    };
  },

  computed: {},
  methods: {
    toggleActive(idx) {
      this.isActive = idx;
    }
   }
};
</script>

<style scoped>
.container {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  width: 90vw;
}

.panel {
  background-size: auto 100%;
  background-position: center;
  background-repeat: no-repeat;
  height: 80vh;
  border-radius: 50px;
  color: #fff;
  cursor: pointer;
  -webkit-box-flex: 0.5;
  -ms-flex: 0.5;
  flex: 0.5;
  /* margin: 10px; */
  margin: 0.5em;
  position: relative;
  -webkit-transition: -webkit-box-flex 0.7s ease-in;
  transition: -webkit-box-flex 0.7s ease-in;
  -o-transition: flex 0.7s ease-in;
  transition: flex 0.7s ease-in;
  transition: flex 0.7s ease-in, -webkit-box-flex 0.7s ease-in,
    -ms-flex 0.7s ease-in;
}

.panel h3 {
  font-size: 1.5rem;
  /* font-size: 24px; */
  position: absolute;
  bottom: 0.9em;
  left: 0.9em;
  margin: 0;
  opacity: 0;
}

.panel.active {
  -webkit-box-flex: 5;
  -ms-flex: 5;
  flex: 5;
}

.panel.active h3 {
  opacity: 1;
  -webkit-transition: opacity 0.3s ease-in 0.4s;
  -o-transition: opacity 0.3s ease-in 0.4s;
  transition: opacity 0.3s ease-in 0.4s;
}

@media (max-width: 580px) {
  .container {
    width: 100vw;
  }

  .panel:nth-of-type(4),
  .panel:nth-of-type(5) {
    display: none;
  }
}
</style>
