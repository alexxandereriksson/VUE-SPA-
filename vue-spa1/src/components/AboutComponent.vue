<script setup></script>
<template>
  <div id="message">
    <label for="text">Message to space:</label>
    <textarea
      v-model="message"
      id="text"
      name="text"
      rows="4"
      cols="50"
      maxlength="30"
    >
    </textarea>

    <p v-if="message.length > 10">Message going to space: {{ message }}</p>
    <p v-else style="color: red">
      Youre message will be sent when conditions are met!
    </p>
  </div>
</template>
<script>
export default {
  data() {
    return {
      message: "",
    };
  },
};
</script>
<style scoped>
p {
  margin: 10px;
  width: 30%;
  border: 1px solid black;
  padding: 20px;
  text-align: center;
}
textarea {
  display: flex;
  justify-content: center;
}
</style>
