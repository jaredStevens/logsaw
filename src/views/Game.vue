<template>
  <v-container>
    <v-layout text-center row wrap>
      <v-flex mt-5 mb-4 xs12>
        <h1 class="display-2 font-weight-bold mb-3">
          Let's Play!
        </h1>
      </v-flex>

      <v-flex xs12 mt-5 mb-4>
        <Timer />
      </v-flex>

      <v-flex xs12 mt-5 mb-4>
        <Score />
      </v-flex>

      <v-flex xs12 mt-5 mb-4>
        <p>Pickup</p>
        <v-flex row wrap justify-center>
          <v-avatar
            tile
            v-for="(item, index) in items"
            :key="index"
            height="100px"
            width="100px"
          >
            <v-img contain height="75px" :src="item.src"></v-img>
          </v-avatar>
        </v-flex>
      </v-flex>

      <v-flex xs12 mt-5 mb-4>
        <Place />
      </v-flex>

      <v-flex mt-5 mb-4 xs12>
        <v-btn outlined to="/">Home</v-btn>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
// import draggable from "@/vuedraggable";
import Timer from "@/components/Timer.vue";
import Score from "@/components/Score.vue";
import Place from "@/components/Place.vue";
export default {
  name: "Game",
  components: {
    Timer,
    Score,
    Place
  },
  data() {
    return {
      items: [
        { src: require("@/assets/3.png"), id: 3 },
        { src: require("@/assets/5.png"), id: 5 },
        { src: require("@/assets/4.png"), id: 4 },
        { src: require("@/assets/2.png"), id: 2 },
        { src: require("@/assets/1.png"), id: 1 }
      ]
    };
  }
};
</script>
