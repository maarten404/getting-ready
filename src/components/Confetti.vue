<template><div></div></template>
<script>
import Confetti from "vue-confetti/src/confetti.js";

export default {
  data: () => ({
    confetti: new Confetti(),
  }),
  methods: {
    start() {
      this.$confetti.start({
        colors: ["#FF6F61", "#004C83", "#55C6A9", "#FFC82B"],
      });
    }
  }
};
</script>