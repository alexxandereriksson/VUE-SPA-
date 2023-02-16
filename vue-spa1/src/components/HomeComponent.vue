<template>
  <div class="hero-image">
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
.hero-image {
  background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)),
    url(../assets/img/casey-horner-RmoWqDCqN2E-unsplash.jpg);
  height: 150vh;
  width: 100%;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  position: relative;
}
.col {
  margin-top: 20vh;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-around;
  align-items: center;
  position: absolute;
  top: 35%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.centered {
  position: absolute;
  top: 5%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
}

#wrapper-hero > div.home {
  top: 10%;
  color: white;
}

div > div.quotes {
  position: absolute;
  top: 85%;
  left: 40%;
  color: orange;
  text-align: center;
}
</style>
