<script>
import ShowPicture from "./components/ShowPicture.vue";
import Confetti from "./components/Confetti.vue";

export default {
  name: "App",
  components: {
    ShowPicture,
    Confetti,
  },
  methods: {
    start() {
      this.$confetti.start();
    },

    stop() {
      this.$confetti.stop();
    },
  },
};

</script>

<template>
  <ShowPicture />
  <Confetti />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body {
  text-align: center;
}

img {
  width: 400px;
}

[v-cloak] {
  display:none; 
}

div{
  height:100vh;
}
</style>

