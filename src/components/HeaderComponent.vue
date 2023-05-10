<template>
  <div class="logo">
    <h1>Weather app</h1>
  </div>
</template>
<script>
export default {
  name: 'HeaderComponent'
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

</style>