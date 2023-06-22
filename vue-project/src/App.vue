<template>
  <div id="app" :class="backgroundColorClass">
    <nav class="navbar navbar-expand-lg navbar-light bg-light nav-bar">
      <div class="container">
        <a
          class="navbar-brand"
          href="#"
          style="color: white; font-weight: bold; font-size: 24px"
        >
          <CloudIcon class="icons" />Weather App
        </a>
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarNav"
          aria-controls="navbarNav"
          aria-expanded="false"
          aria-label="Toggle navigation"
          style="background-color: white"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav ml-auto">
            <li class="nav-item">
              <div class="d-flex">
                <input
                  type="text"
                  v-model="searchInput"
                  class="input-style"
                  placeholder="Введите город"
                  style="width: 500px"
                />
                <button class="btn-style ml-2" @click="searchWeather">
                  <MagnifyingGlassIcon class="icons" /> Поиск
                </button>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </nav>
    <WeatherDisplay v-if="selectedCity" :selectedCity="selectedCity" />
  </div>
</template>

<script>
import WeatherDisplay from "./components/WeatherDisplay.vue";
import CityList from "./components/CityList.vue";
import { MagnifyingGlassIcon, CloudIcon } from "@heroicons/vue/24/solid";

export default {
  components: {
    WeatherDisplay,
    CityList,
    MagnifyingGlassIcon,
    CloudIcon,
  },
  data() {
    return {
      backgroundColorClass: "my-custom-navbar",
      searchInput: "",
      selectedCity: "",
    };
  },
  methods: {
    searchWeather() {
      this.selectedCity = this.searchInput;
    },
  },
};
</script>

<style>
@import url("../src/css/Base.css");

.nav-bar {
  box-shadow: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
  border-radius: 16px;
  background: rgb(110, 93, 207);
  background: linear-gradient(
    90deg,
    rgba(110, 93, 207, 1) 0%,
    rgba(194, 125, 252, 1) 52%,
    rgba(234, 235, 237, 1) 100%
  );
}

.btn-style {
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 16px;
  background-color: #4b408f;
  font-weight: bolder;
  border: 0px;
  color: white;
  padding: 10px;
  outline: 0;
  outline-offset: 0;
}

.btn-style:hover {
  border-radius: 16px;
  background-color: #7362db;
  font-weight: bolder;
  border: 0px;
  color: white;
  padding: 10px;
}

.btn-style:focus {
  outline: 0;
  outline-offset: 0;
}

.input-style {
  width: 100%;
  border-radius: 16px;
  border: 0px;
  padding-left: 5px;
  outline: 0;
  outline-offset: 0;
}

.icons {
  height: 32px;
  width: 32px;
}
</style>
