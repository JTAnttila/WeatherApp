<template>
  <div class="weather-box">
    <div class="sunrise_sunset">
      <div class="sunrise">Aurinko nousee {{ sunrise }} <img src="../assets/svg/sunrise.svg" alt=""></div>
      <div class="sunset">Aurinko laskee {{ sunset }} <img src="../assets/svg/sunset.svg" alt=""></div>
    </div>
    <div class="temp">{{ Math.round(weather.main.temp) }}°C</div>
    <div class="desc"> {{ weather.main.description }}</div>
    <div class="weather_desc">Tuntuu kuin {{ Math.round(weather.main.feels_like) }}°C</div>
    <div class="upDown">
      <div class="temp_min">Päivän alin lämpötila {{ Math.round(weather.main.temp_min) }}°C</div>
      <div class="temp_max">Päivän ylin lämpötila {{ Math.round(weather.main.temp_max) }}°C</div>
    </div>
    <div class="pressure">Ilmanpaine {{ weather.main.pressure }} hPa</div>
    <div class="humidity">Ilmankosteus {{ weather.main.humidity }}%</div>
    <div class="wind_speed">Tuulen nopeus {{ Math.round(weather.wind.speed) }} m/s</div>
    <div class="wind_deg">Tuulen suunta {{ weather.wind.deg }}°</div>
    <div class="weather">
      <img class="weather-symbol" :src="`/symbols/${weatherSymbol}.svg`" alt="">
    </div>
  </div>
</template>
<script>
export default {
  name: 'WeatherBox',
  props: {
    weather: {}
  },
  computed: {
    sunrise() {
      return (new Date(this.weather.sys.sunrise * 1000)).toLocaleTimeString('fi-FI', {
        hour: '2-digit',
        minute: '2-digit'
      });
    },
    sunset() {
      return (new Date(this.weather.sys.sunset * 1000)).toLocaleTimeString('fi-FI', {
        hour: '2-digit',
        minute: '2-digit'
      });
    },
    weatherSymbol() {
      switch (parseInt(this.weather.weather[0].icon)) {
        case 1:
          return 1;
        case 2:
          return 2;
        case 3:
          return 3;
        case 4:
          return 4;
        case 9:
          return 23;
        case 10:
          return 33;
        case 11:
          return 64;
        case 13:
          return 52;
        case 50:
          return 91;
        default:
          return 1;
      }
    }
  }
}
</script>
<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'montserrat', sans-serif;
}

main {
  min-height: 100vh;
  padding: 25px;

  background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.25), rgba(0, 0, 0, 0.75));
}

.weather-box {
  display: flex;
  flex-direction: column;
  text-align: center;
  background-color: rgb(21 29 33);
  border-radius: 16px;
  width: 50rem;
}

.upDown {
  display: flex;
  justify-content: space-between;
  padding: 35px;
}

.sunrise_sunset {
  display: flex;
  justify-content: space-between;
  padding: 20px 20px 0px 20px;
  color: #fff;
  font-size: 20px;
}

.weather-box .temp {
  display: inline;
  color: #fff;
  font-size: 102px;
  font-weight: 900;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  border-radius: 16px;
}

.weather-box .weather {
  width: 100%;
  display: flex;
  justify-content: center;
}

.weather-symbol {
  width: 200px;
}

.weather_desc {
  color: #fff;
  font-size: 20px;
  font-weight: 500;
  font-style: italic;
}

.temp_min {
  text-align: left;
  color: #fff;
  font-size: 20px;
  font-weight: 00;
  font-style: italic;
}

.temp_max {
  text-align: right;
  color: #fff;
  font-size: 20px;
  font-weight: 500;
  font-style: italic;
}

.pressure {
  color: #fff;
  font-size: 20px;
  font-weight: 500;
  font-style: italic;
}

.humidity {
  color: #fff;
  font-size: 20px;
  font-weight: 500;
  font-style: italic;
}

.wind_speed {
  color: #fff;
  font-size: 20px;
  font-weight: 500;
  font-style: italic;
}

.wind_deg {
  color: #fff;
  font-size: 20px;
  font-weight: 500;
  font-style: italic;
}
</style>