<template>
  <main>
    <HeaderComponent/>
    <SearchField @search="fetchWeather"/>

    <div class="weather-wrap" v-if="weather.main">
      <div class="location-box">
        <div class="location">{{ weather.name }}, {{ weather.sys.country }}</div>
        <div class="date">{{ dateBuilder() }}</div>
      </div>
      <WeatherBox :weather="weather"/>
    </div>
    <FooterComponent/>
  </main>
</template>

<script>
import FooterComponent from "@/components/FooterComponent.vue";
import HeaderComponent from "@/components/HeaderComponent.vue";
import SearchField from "@/components/SearchField.vue";
import WeatherBox from "@/components/WeatherBox.vue";

export default {
  name: 'app',
  components: {WeatherBox, SearchField, HeaderComponent, FooterComponent},
  data(){
    return{
      api_key: import.meta.env.VITE_APP_WEATHER,
      url_base: 'https://api.openweathermap.org/data/2.5/',
      weather: {}
    }
  },
  methods: {
    fetchWeather(string) {
      fetch(`${this.url_base}weather?q=${string}&units=metric&APPID=${this.api_key}`)
          .then(res => res.json())
          .then(data => {
            this.weather = data;
          });
    },
    setResults (results){
      this.weather = results;
    },
    dateBuilder(){
      return (new Date()).toLocaleDateString('fi-FI', {
        weekday: 'long',
        day: 'numeric',
        month: 'long',
        year: 'numeric'
      });
    }
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body{
  font-family: 'montserrat', sans-serif;
}

#app{
  background-image: url("./assets/Moonlit Asteroid.jpg");
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}

main{
  min-height: 100vh;
  padding: 25px;

  background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.25), rgba(0, 0, 0, 0.75));
}

.weather-wrap {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.location-box .location{
  color: #fff;
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0,0,0,0.25);
}

.location-box .date{
  color: #fff;
  font-size: 20px;
  font-weight: 300;
  font-style: italic;
  text-align: center;
}

</style>