<template>
  <div id="app">
    <img alt="clima" src="./assets/clima.jpg" />
    <Tabs @showAddCity="showAddCity" @showGetWheather="showGetWheather" />
    <Weather v-bind:cities="cities" ref="weather" v-show="showWheather" />
    <AddCity v-show="showCity" @addNewCity="addNewCity" />
  </div>
</template>

<script>
import Weather from "./components/Weather.vue";
import AddCity from "./components/AddCity.vue";
import Tabs from "./components/Tabs.vue";

export default {
  name: "App",
  components: {
    Weather,
    AddCity,
    Tabs,
  },
  data() {
    return {
      cities: ["London", "Rosario"],
      showCity: false,
      showWheather: false,
    };
  },
  methods: {
    addNewCity(newCity) {
      let est = true;
      for (let index = 0; index < this.cities.length; index++) {
        if (this.cities[index] === newCity) {
          est = false;
        }
      }
      if (est) {
        this.cities.push(newCity);
      }
    },

    showAddCity() {
      this.showCity = !this.showCity;
      this.showWheather = false;
    },
    showGetWheather() {
      this.showWheather = !this.showWheather;
      this.showCity = false;
    },
  },
};
</script>

<style>
img {
  width: 300px;
  height: 300px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
