<template>
  <div id="wrapper-hero">
    <img
      src="../assets/img/casey-horner-RmoWqDCqN2E-unsplash.jpg"
      class="img-fluid"
      alt="space"
    />

    <div class="centered">
      <h1 :style="{ color: color }">FINAL SPACE</h1>
    </div>
    <!-- Card -->

    <div class="row">
      <div class="col">
        <div
          v-for="character in characters"
          :key="character.id"
          class="card"
          style="width: 18rem"
        >
          <img
            :src="character.img_url"
            class="card-img-top rounded"
            :alt="character.name"
          />
          <div class="card-body">
            <h5 class="card-title">MY NAME IS: {{ character.name }}</h5>
            <p class="card-text">THEY CALL ME!! {{ character.alias[2] }}</p>
            <p class="card-text">Status: {{ character.status }}</p>
            <p class="card-text">Gender: {{ character.gender }}</p>
            <p class="card-text">
              Abilities: {{ character.abilities[0] + character.abilities[1] }}
            </p>
            <button @click="getQuote()" type="button" class="btn btn-secondary">
              Let me tell you something!
            </button>
          </div>
        </div>
      </div>
    </div>
    <div v-for="quote in quotes" :key="quote.id" class="quotes">
      <h2>{{ quote.quote }}</h2>
    </div>
    <h2>{{ aQuote }}</h2>
    <!-- end hero div -->
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      characters: [],
      quotes: [],
      home: "Welcome Home Space cowboy",
      color: "orange",
    };
  },

  computed: {},
  created() {
    this.getCharacters();
    
  },
  methods: {
    async getCharacters() {
      axios
        .get("https://finalspaceapi.com/api/v0/character?limit=4")
        .then((response) => (this.characters = response.data));
    },
    async getQuote() {
      axios
        .get("https://finalspaceapi.com/api/v0/quote/?limit=1")
        .then((response) => (this.quotes = response.data));
    },
  },
};
</script>
<style scoped>
.col {
  margin-top: 40vh;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-around;
  align-items: center;
  position: absolute;
  top: 56%;
  left: 50%;
  transform: translate(-50%, -50%);
}
#wrapper-hero img {
  margin: 0 auto;
  height: 100%;
  overflow-x: hidden;
}

.centered {
  position: absolute;
  top: 25%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
}

#wrapper-hero > img {
  opacity: 0.9;
  height: 150vh;
  width: 100%;
}
.home {
  position: absolute;
  font-size: 100px;
}
#wrapper-hero > div.home {
  top: 10%;
  color: white;
}
.characters {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
  font-size: 3rem;
}
#wrapper-hero > div.quotes {
  position: absolute;
  top: 140%;
  left: 40%;
  color: orange;
  text-align: center;
}
</style>
