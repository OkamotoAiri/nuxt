<template>
<div>
  <Header />
  <Nuxt />
  </div>
</template>

<script>

import Header from "~/components/Header.vue";

export default {
  components: {
    Header
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding:0;
}

[v-cloak] {
    opacity: 0;
}

body {
  color: #333;
  font-family:"Verdana","sans-serif",;
  font-size: 14px;
  background-color: rgb(200, 211, 245);
  user-select: none;
}

h1 {
  font-size: 20px;
}

h2 {
  font-size: 20px;
  padding:10px;
  text-align: center;
  background-color: rgb(226, 232, 250);
  margin:90px 0 20px 0;
  font-weight: normal;
  color: rgb(87, 86, 86);
  box-shadow: 0px 0px 5px grey;
}

ul {
  list-style: none;
}

input[type="submit"],
button,
.btn {
  padding:5px 20px;
  background-color: rgb(99, 133, 247);
  border: none;
  border-radius: 6px;
  color: white;
  cursor: pointer;
}

</style>
