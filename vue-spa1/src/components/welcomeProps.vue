<template>
  <div>
    <h4>{{ welcome }}</h4>
  </div>
</template>

<script>
export default {
  props: {
    welcome: { type: String, required: true },
  },
};
</script>
<style scoped>
h4 {
  color: orange;
}
</style>
