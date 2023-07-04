<template>
  <the-header></the-header>
  <the-teams></the-teams>
</template>

<script>
import TheHeader from "./components/TheHeader.vue";
import TheTeams from "./components/teams/TheTeams.vue";
export default {
  components: {
    TheHeader,
    TheTeams,
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
html {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
}
</style>
