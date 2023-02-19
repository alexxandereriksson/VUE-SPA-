<template>
  <div>
    <input :value="value" @click="onClick" type="button" />
  </div>
</template>
<script>
export default {
  data() {
    return {
      value: "Message to log",
    };
  },
  methods: {
    onClick() {
      this.$emit("custom-event");
    },
  },
};
</script>
<style scoped>
input {
  background-color: black;
  color: orange;
}
</style>
