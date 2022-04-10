<!--  Holds your entire application in this file -->

<!-- Javascript Content -->
<script>
import UserProfile from "./components/UserProfile.vue";
export default{
  name: 'App',
  components: {UserProfile}
}

</script>

<!-- HTML content -->
<template>
 <div id="app">
    <UserProfile></UserProfile>
 </div>
</template>




<!-- CSS stylings -->
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
-webkit-font-smooting: antialiased;
-moz-osx-font-smooting: grayscale;
  color: #2c3e50;
  min-height: 100vh;
  background-color: #F3F5FA;
}

</style>
