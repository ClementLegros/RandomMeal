<template>
  <div class="nav">
    <div class="nav-link">
      <router-link class="link" to="/">Random Meal</router-link>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  name: "MyNavbar",
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Inconsolata:wght@800&display=swap");
* {
  margin: 0;
  padding: 0;
}
.nav {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  background-color: #333;
  height: 4em;
}
.nav-link {
  height: 100%;
  width: 10em;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  margin-left: 10px;
  font-size: xx-large;
}
.nav-link:hover {
  background-color: rgb(150, 150, 150);
}
.link {
  color: white;
  text-decoration: solid;
  font-family: "Inconsolata", monospace;
}
</style>
