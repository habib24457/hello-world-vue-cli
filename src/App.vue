<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <FirstComponent myName="My Name is Jeff!"/>
    <SecondComponent age=25 favMovie="the Social Network" loveTo="Programming" studyCourse="Boring..."/>
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import FirstComponent from './components/FirstComponent.vue';
import SecondComponent from './components/SecondComponent.vue';

export default {
  name:'App',
  components:{
    FirstComponent,
    SecondComponent
  }
  // name: 'App',
  // components: {
  //   HelloWorld
  // }
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
