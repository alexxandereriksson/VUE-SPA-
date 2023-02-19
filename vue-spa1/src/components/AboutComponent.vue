<script setup>
import CustomButton from "./CustomButton.vue";
</script>
<template>
  <div class="hero-image">
    <div id="message">
      <label for="text"><b> Message to space:</b></label>
      <label for="text">
        <em> Min/10 Max/30</em> <b>{{ msgLength }}</b></label
      >
      <textarea
        v-model="message"
        id="text"
        name="text"
        rows="4"
        cols="50"
        maxlength="30"
      >
      </textarea>

      <button
        submit
        type="button"
        class="btn btn-success"
        v-if="message.length > 10"
        @click="onClick"
      >
        Send to space
      </button>
      <button disabled type="button" class="btn btn-danger" v-else>
        Send to
      </button>
      <p>{{ spacemsg }}</p>
    </div>
    <custom-button @custom-event="onEmit"></custom-button>
  </div>

</template>
<script>
export default {
  data() {
    return {
      message: "",
      spacemsg: this.message,
    };
  },
  computed: {
    msgLength() {
      return this.message.length;
    },
  },
  methods: {
    onClick() {
      this.spacemsg = this.message;
    },
    onEmit() {
     console.log(this.message);
    },
  },
  components: {
    CustomButton,
  },
  watch: {
    spacemsg(newMsg) {
      alert(`Youre message were succesfully sent ${newMsg}`);
    },
  },
};
</script>
<style scoped>
p {
  margin: 4vh;
  width: 30%;
  border: 2px solid white;
  border-radius: 10px 100px 10px 100px;
  padding: 30px;
  text-align: center;
  color: orange;
  font-size: 1.5rem;
}
#message {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
textarea {
  margin-top: 1vh;
  color: black;
}
label {
  padding-top: 2vh;

  color: orange;
}
.hero-image {
  background-image: linear-gradient(rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.6)),
    url(../assets/img/casey-horner-RmoWqDCqN2E-unsplash.jpg);
  height: 100vh;
  width: 100%;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  position: relative;
}
</style>
