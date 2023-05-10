<template>
  <div class="search-box">
    <input
        type="text"
        class="search-bar"
        placeholder="Enter city name..."
        v-model="query"
        @keyup.enter="$emit('search', query)"
    />
  </div>
</template>
<script>
export default {
  name: 'SearchField',
  emits: ['search'],
  data() {
    return {
      query: ""
    };
  },
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

.search-box {
  width: 100%;
  margin-bottom: 30px;
}

.search-box .search-bar {
  display: block;
  width: 100%;
  padding: 15px;

  color: #313131;
  font-size: 20px;

  appearance: none;
  border: none;
  outline: none;
  background: none;

  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
  background-color: rgb(21 29 33);
  border-radius: 16px;
  transition: 0.4s;
}

.search-box .search-bar:focus {
  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
  background-color: rgba(234, 233, 233, 0.75);
}

</style>