<template>
  <div v-if="result" class="about">
    <h1>This is the weather</h1>
    <p>Weather: {{ result.weather[0].description }}</p>
    <p>Location: {{ result.name }}<p>
    <p>Temperature: {{ result.main.temp }}</p>
    <p>Maximum temperature: {{ result.main.temp_max }}</p>
    <p>Minimum temperature: {{ result.main.temp_min }}</p>
    <p>Humidity: {{ result.main.humidity }}</p>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data: () => ({
    result: null,
  }),
    created(){
    axios.get("https://api.openweathermap.org/data/2.5/weather?q=playa%20del%20carmen&APPID=fc6a340b84bb7373e24e8491c17c9bf5").then((result) => {
      this.result = result.data;
    });
  },
};
</script>
