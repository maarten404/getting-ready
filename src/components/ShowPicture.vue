<script>
import { ref } from 'vue'
import Confetti from "vue-confetti/src/confetti.js";

export default {
  name: "showpicture",
  data: function(){
    return {
      pictureVisible: true,
      readyMessageVisible: false,
      images: [
        '/onderbroek.png',
        '/hemd.png',
        '/trui.png',
        '/sokken.png',
        '/broek.png',
        '/schoenen.png'
      ],
      counter: 0,
      elapsedTime: 0,
      timer: undefined,
      confetti: new Confetti(),
    }
  },
  computed: {
   formattedElapsedTime() {
      const date = new Date(null);
      date.setSeconds(this.elapsedTime / 1000);
      const utc = date.toUTCString();
      // return utc.substr(utc.indexOf(":") - 2, 8);
      return utc.substr(utc.indexOf(":") + 1, 5); // we only want minutes and seconds
    }
  },
  methods: {
    nextImage() {
      if(this.counter == this.images.length - 1 && this.pictureVisible){
        this.finishOperation();
      } else {
        this.counter++;
      }
    },
    starttimer() {
      this.timer = setInterval(() => {
        this.elapsedTime += 1000;
      }, 1000);
    },
    stoptimer() {
      clearInterval(this.timer);
    },
    finishOperation() {
      this.pictureVisible = false;
      this.readyMessageVisible = true;
      this.stoptimer();
      this.confetti.start({
        colors: ["#FF6F61", "#004C83", "#55C6A9", "#FFC82B"],
      });
    }
  },
  mounted() {
    this.starttimer();
    console.log("we are in business");
  },
};

</script>

<template>
<div @click="nextImage">
  <img :src="images[counter]" v-if="pictureVisible"/>
  <h1 v-if="readyMessageVisible">Klaar is Hanna!</h1>
  <h1>{{ formattedElapsedTime }}</h1>
</div>
</template>

