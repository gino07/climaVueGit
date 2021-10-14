<template>
  <div class="weather">
    <h2>Clima</h2>
    <!-- <input v-model="newCity" type="text" />
    <button @click="addCity" id="add">Agregar ciudad</button> -->

    <select @change="getWeather" name="" v-model="selectedCity">
      <option v-for="city in cities" :key="city"> {{ city }}</option>
    </select>
    <ul>
      <li v-for="city in cities" :key="city">
        {{ city }}<button @click="getWeather(city)">¿Cuál es el clima?</button
        ><button @click="deleteCity(city)">Eliminar</button>
      </li>
    </ul>
    <p>{{ selectedCity }}: {{ weather }}</p>
  </div>
</template>

<script>
import api from "../services/api";
export default {
  name: "Weather",
  props: ["cities"],

  data() {
    return {
      newCity: "",
      weather: "",
      selectedCity: "",
    };
  },
  methods: {
    deleteCity(selectedCity) {
      for (let index = 0; index < this.cities.length; index++) {
        if (this.cities[index] === selectedCity) {
          this.cities.splice(index, 1);
        }
      }
    },
    async getWeather(selectedCity) {
      try {
        let { data } = await api.getWeather(selectedCity);
        this.selectedCity = selectedCity;

        this.weather = data.weather[0].description;
      } catch (error) {
        alert("Error, vuelva a intentarlo nuevamente mas tarde");
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
p h3 {
  margin: 40px 0 0;
}
ul {
  margin: 0 200px;
  width: 500px;
  height: auto;
  color: white;
  background-color: indigo;
  list-style-type: none;
  padding: 0;
}
li {
  font: Comic Sans;
  margin: 10px 10px;
}
a {
  color: #42b983;
}
button {
  margin: 0px 10px;
}
</style>
