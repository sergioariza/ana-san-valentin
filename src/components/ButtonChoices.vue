<template>
  <div class="button-choices-container">
    <button class="yes-button" @click="$emit('yes-action')">Sim</button>
    <button class="no-button" :style="styleNoButton" @mouseover="moveRandom" @click="moveRandom">Não</button>
  </div>
</template>

<script>
export default {
  name: 'ButtonChoices',
  props: {},
  data() {
    return {
      styleNoButton: {},
      pleaseCounter: 0,
    };
  },
  methods: {
    moveRandom() {
      const randomX = Math.floor(Math.random() * 200) - 100; // Move between -100px and +100px
      const randomY = Math.floor(Math.random() * 200) - 100; // Move between -100px and +100px
      this.styleNoButton = {
        transform: `translate(${randomX}px, ${randomY}px)`,
      };
      this.pleaseCounter++;
      if (this.pleaseCounter === 5) {
        this.$emit('show-please');
        this.styleNoButton = { transform: 'translate(0, 0)' };
      }
    },
  },
}
</script>

<style scoped>
.button-choices-container {
  display: flex;
  justify-content: center;
  gap: 20px;
  margin-top: 20px;

  button {
    padding: 10px 20px;
    font-size: 16px;
    cursor: pointer;
    border: none;
    border-radius: 5px;
    color: white;
    transition: background-color 0.3s ease;

    &.yes-button {
      background-color: #27ae60;
      &:hover {
        background-color: #2ecc71;
      }
    }
    &.no-button {
      background-color: #c0392b;
      &:hover {
        background-color: #e74c3c;
      } 
    }
  }
}
</style>
