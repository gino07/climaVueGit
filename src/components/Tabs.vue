<template>
  <div class="Tabs">
    <button @click="$emit('showAddCity')" href="#">Agregar Ciudad</button>
    <button @click="$emit('showGetWheather')" href="#">Clima</button>
  </div>
</template>

<script>
export default {
  name: "Tabs",
  data() {
    return {};
  },
  methods: {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  margin: 10px;
  display: inline;
  color: #42b983;
}
</style>
