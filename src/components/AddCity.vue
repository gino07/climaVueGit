<template>
  <div class="addCity">
    <h2>Agregar Ciudad</h2>
    <input v-model="newCity" type="text" />
    <button @click="addCity" :disabled="state" id="add">
      Agregar ciudad
    </button>
  </div>
</template>

<script>
import api from "../services/api";
export default {
  name: "AddCity",
  data() {
    return {
      newCity: "",
      state: false,
    };
  },
  methods: {
    async addCity() {
      try {
        this.state = true;
        let res = await api.getWeather(this.newCity);
        if (res.status === 200) {
          this.$emit("addNewCity", this.newCity);
        }
        this.newCity = "";
        this.state = false;
      } catch (error) {
        this.newCity = "";
        this.state = false;
        alert("Nombre de ciudad incorrecta");
      }
    },
  },
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
  color: #42b983;
}
</style>
