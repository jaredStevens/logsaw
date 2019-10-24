<template>
  <v-container>
    <v-layout text-center row wrap>
      <v-flex mt-5 mb-4 xs12>
        <h1 class="display-2 font-weight-bold mb-3">
          Let's Play!
        </h1>
      </v-flex>

      <v-flex mt-5 mb-4 xs12>
        <h1>Score:  {{ score || 0 }} seconds</h1>
      </v-flex>

      <v-flex v-if="findMe" mt-5 mb-4 xs12>
        <h1>Find Me</h1>
        <v-avatar
              tile
              height="100px"
              width="100px"
            >
              <v-img contain height="75px" :src="findMe.src"></v-img>
            </v-avatar>
      </v-flex>

      <v-flex xs12 mt-5 mb-4>
        <p><strong>Pickup Cards</strong> (Drag Cards below to put them in order.)</p>
        <v-flex class="hidden" row wrap justify-center>
          <draggable group="zoovu" :list="items" @start="drag = true" @end="drag = false">
            <v-avatar
              tile
              v-for="(item, index) in items"
              :key="index"
              height="100px"
              width="100px"
            >
              <v-img class="mask" contain height="75px" src="@/assets/placeholder.png"></v-img>
            </v-avatar>
          </draggable>
        </v-flex>
      </v-flex>

      <v-flex xs12 mt-5 mb-4>
        <p><strong>Zoovu Logo</strong> (Drag cards here to put the logo back together.)</p>
        <v-flex row wrap justify-center>
          <draggable class="droppable" group="zoovu" :list="logo" @start="drag = true" @end="drag = false" @change="cardRevealed">
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
        <v-btn class="ma-2" outlined to="/">Home</v-btn>
        <v-btn class="ma-2" outlined @click="refresh">Reset Game</v-btn>
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
      score: 0,
      findMe: null,
      winner: false,
      items: [
        { name: "o2", src: require("@/assets/3.png"), id: 3 },
        { name: "u", src: require("@/assets/5.png"), id: 5 },
        { name: "v", src: require("@/assets/4.png"), id: 4 },
        { name: "o1", src: require("@/assets/2.png"), id: 2 },
        { name: "z", src: require("@/assets/1.png"), id: 1 }
      ],
      logo: []
    };
  },
  mounted() {
    const randoCalrissian = this.getRandomInt(this.items.length)
    this.findMe = this.items[randoCalrissian]
  },
  methods: {
    refresh() {
      window.location.reload(true)
    },
    cardRevealed(card){
      if(this.score === 0) {
        setTimeout(this.updateScore, 1000)
      }
      if(card.added) {
        console.log(card.added.element.name)
        if(card.added.element.name === this.findMe.name) {
          this.winner = true
        } else {
          this.updateScore(10)
        }
      }
    },
    getRandomInt(max) {
      return Math.floor(Math.random() * Math.floor(max));
    },
    updateScore(increment){
      if(increment) {
        this.score += increment
      } else {
        this.score += 1
        if(!this.winner) {
          setTimeout(this.updateScore, 1000)
        }
      } if(this.score >= 45) {
        this.refresh()
      }
    }
  }
};
</script>
<style scoped>
.droppable {
  height: 75px;
  width: 100%;
}
</style>
