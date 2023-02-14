<template>
  <div>
    <h4>{{ welcome }}</h4>
  </div>
</template>

<script>
export default {
 
  props: {
    welcome: String,
  },
};
</script>
<style scoped>
h4 {
  color: white;
}
</style>
