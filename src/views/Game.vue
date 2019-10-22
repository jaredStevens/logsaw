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
        <Pickup />
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
import Timer from "@/components/Timer.vue";
import Pickup from "@/components/Pickup.vue";
import Score from "@/components/Score.vue";
import Place from "@/components/Place.vue";
export default {
  name: "Game",
  components: {
    Timer,
    Pickup,
    Score,
    Place
  },
  data() {
    return {};
  }
};
</script>
