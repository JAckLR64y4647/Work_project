<template>
    <div v-if="weatherLoaded" class="current-weather">
      <div>
        <h2 class="title-style">{{ selectedCity }} {{ temperature }}°C</h2>
      </div>
      <div class="weather-backgroud extra-backgroud extra-info">
        <p class="info-style">Описание: {{ description }}</p>
        <p class="info-style">Влажность: {{ humidity }}%</p>
        <p class="info-style">Порывы ветра: {{ windSpeed }} м/с</p>
      </div>
      <div
        class="map-cell weather-backgroud extra-backgroud"
        style="height: 400px; margin-top: 35px"
      >
        <MapWeather />
      </div>
    </div>
  </template>
  
  <script setup lang="ts">
  import { ref, watch, onMounted } from "vue";
  import MapWeather from "./MapWeather.vue";
  
  const props = defineProps<{
    selectedCity: boolean;
  }>();
  
  const temperature = ref("");
  const description = ref("");
  const humidity = ref("");
  const windSpeed = ref("");
  const weatherLoaded = ref(false);
  async function showWeather() {
    try {
      const apiKey = "d76774aebcd4655f95ed4847639da2af";
      const weatherUrl = `https://api.openweathermap.org/data/2.5/weather?q=${props.selectedCity}&units=metric&appid=${apiKey}`;
      const weatherResponse = await fetch(weatherUrl);
      const weatherData = await weatherResponse.json();
      if (weatherData && weatherData.main) {
        temperature.value = weatherData.main.temp;
        description.value = weatherData.weather[0].description;
        humidity.value = weatherData.main.humidity;
        windSpeed.value = weatherData.wind.speed;
        weatherLoaded.value = true;
      }
    } catch (error) {
      console.log("Error fetching weather data:", error);
    }
  }
  onMounted(() => {
    showWeather();
  });
  watch(
    () => props.selectedCity,
    () => {
      showWeather();
    }
  );
  </script>
  <style scoped>
  @import url("https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css");
  @import url("../css/CurrentWeather.css");
  
  .map-cell {
    width: 100%;
    margin-bottom: 20px;
    display: none;
  }
  
  @media (min-width: 1024px) {
    .map-cell {
      width: 70%;
      display: flex;
    }
  }
  </style>
  