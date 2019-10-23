/* eslint-disable */
<template>
  <v-container>
    <v-layout text-center row wrap>
      <v-flex mt-5 mb-4 xs12>
        <h1 class="display-2 font-weight-bold mb-3">
          Let's Play!
        </h1>
      </v-flex>

      <v-flex xs12 mt-5 mb-4>
        <p>Pickup Cards</p>
        <v-flex row wrap justify-center>
          <draggable group="zoovu" @start="drag = true" @end="drag = false">
            <v-avatar
              tile
              v-for="(item, index) in items"
              :key="index"
              height="100px"
              width="100px"
            >
              <v-img contain height="75px" :src="item.src"></v-img>
            </v-avatar>
          </draggable>
        </v-flex>
      </v-flex>

      <v-flex xs12 mt-5 mb-4>
        <p>Zoovu Logo</p>
        <v-flex row wrap justify-center>
          <draggable group="zoovu" @start="drag = true" @end="drag = false">
            <v-avatar
              tile
              v-for="(item, index) in logo"
              :key="index"
              height="100px"
              width="100px"
            >
              <v-img contain height="75px" :src="item.src"></v-img>
            </v-avatar>
          </draggable>
        </v-flex>
      </v-flex>

      <v-flex mt-5 mb-4 xs12>
        <v-btn outlined to="/">Home</v-btn>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import draggable from "vuedraggable";
export default {
  name: "Game",
  components: {
    draggable
  },
  data() {
    return {
      drag: false,
      items: [
        { src: require("@/assets/3.png"), id: 3 },
        { src: require("@/assets/5.png"), id: 5 },
        { src: require("@/assets/4.png"), id: 4 },
        { src: require("@/assets/2.png"), id: 2 },
        { src: require("@/assets/1.png"), id: 1 }
      ],
      logo: []
    };
  }
};
</script>
