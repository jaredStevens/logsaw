<template>
  <v-container>
    <v-layout text-center wrap>
      <v-flex xs12>
        <v-img
          :src="require('../assets/zoovu-logo.png')"
          class="my-3"
          contain
          height="150"
        ></v-img>
      </v-flex>

      <v-flex mb-4>
        <h1 class="display-2 font-weight-bold mb-3">
          Want to Play A Game?
        </h1>
      </v-flex>

      <v-flex mb-5 xs12>
        <v-layout justify-center> </v-layout>
        <p>
          Find the hidden card we're looking for.  You'll have 30 seconds to find the card we're looking for.  A bad guess, and we'll add 10 seconds to your limited time.  Good luck!!
        </p>
      </v-flex>

      <v-flex xs12 mb-5>
        <v-layout justify-center>
          <v-btn outlined to="/game">Enter to Play</v-btn>
        </v-layout>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  data: () => ({})
};
</script>
