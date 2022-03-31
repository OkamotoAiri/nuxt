<template>
    <header>
    <Menu />
    <h1><span class="material-icons logo">groups</span>顧客管理</h1>
    </header>
</template>

<script>

import Menu from "~/components/Menu.vue";

export default {
  components: {
    Menu
  }
}
</script>

<style scoped>

header {
  background-color: rgb(99, 133, 247);
  color: white;
  padding:20px;
  position: fixed;
  z-index: 1;
  width: 100%;
  top:0;
}

.logo {
  margin-right: 10px;
}

</style>