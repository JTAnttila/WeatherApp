<template>
  <div style="height: 160px;" />
  <div class="footer">
    <div class="logo">Anttila.io</div>
    <div class="footer_text">Weather information and details are being provided by OpenWeatherMap Open Data API</div>
  </div>
</template>
<script>
export default {
  name: 'FooterComponent'
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

.logo {
  color: #fff;
  font-family: "Kelly Slab";
  text-align: center;
  font-size: 50px;
}

.footer {
  bottom: 0;
  position: absolute;
  left: 7%;
  width: 85%;
  border-radius: 25px 25px 0px 0px;
  height: 160px;
  background: rgb(21 29 33);
  color: #fff;
  font-size: 25px;
  text-align: center;
}

</style>