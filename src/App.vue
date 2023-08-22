<template>

 <NavigationMenu/>

<br>  
  <SignUp/>

 
</template>

<script>
import NavigationMenu from './components/navigation.vue'
import SignUp from './components/SignUp.vue'
export default {
  name: 'App',
 components: {
  SignUp,
  NavigationMenu

 }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
