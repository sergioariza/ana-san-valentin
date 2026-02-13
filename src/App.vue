<template>
  <div id="app">
    <img width="30%" :src="pictureSrc" alt="Two cats in love">
    <h1>{{ msg }}</h1>
    <button-choices v-if="showOptions" @yes-action="yesAction" @show-please="showPlease" />
  </div>
</template>

<script>
import ButtonChoices from './components/ButtonChoices.vue'

export default {
  name: 'App',
  components: {
    ButtonChoices,
  },
  data() {
    return {
      msg: 'Ana, meu amor, você quer ser minha namorada no Dia dos Namorados?',
      pictureSrc: require('./assets/i-love-u.gif'),
      showOptions: true,
    };
  },
  methods: {
    yesAction() {
      this.msg = 'Eu te amo, Ana! Feliz Dia dos Namorados!';
      this.pictureSrc = require('./assets/ana-y-sergio.jpg');
      this.showOptions = false;
    },
    showPlease() {
      this.msg = 'Por favor, Ana, me dê uma chance! Eu prometo te fazer muito feliz!';
      this.pictureSrc = require('./assets/golfo.jpg');
    },
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
