<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->

    <FirstComponent myName="My Name is Jeff!"/>
    <SecondComponent age=25 favMovie="the Social Network" loveTo="Programming" studyCourse="Boring..."/>
    <div v-html="example"></div>
    <h2 v-bind:id="headingId">Heading</h2>
    <button v-bind:disabled="isDisabled">Click</button>

    <h2 class="underline">This is underline text | Vue Binding</h2>
    <h2 v-bind:class="status"> binding text status</h2>
    <h2 v-bind:class="isPromoted">Is the Movie promoted?</h2>

    <h2 v-bind:class="isNew && 'new-movie'">New Movie</h2>
    <h2 v-bind:class="isSoldOut ? 'sold-out':'new-movie'">Is Sold Out?</h2>

    <h2 v-bind:class="['new','promoted']">Newly promoted movie</h2>
    <h2 v-bind:class="[isPromoted && 'promoted',isSoldout?'sold-out':'new-movie']">Array Conditional</h2>

    <h2 v-bind:class="{
      promoted:isPromoted,
      'new-movie':isNew,
      'sold-out':isSoldOut
    }">Object Conditional Binding</h2>

    <h2 class="underline">Inline Style</h2>
    <h2 v-bind:style="{
      color:'blue',
      'font-size':dynFontSize +'px',
      backgroundColor:'orange'
    }">This text contains inline style.</h2>

    <h2 class="underline">Conditional Rendering (v-if,v-else-if...)</h2>
    <h2 v-if="(num===0)">1.This number is zero</h2>
    <h2 v-else-if="(num<0)">2.This number is Negative</h2>
    <h2 v-else>3.(v-else) The number is not zero</h2>
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
  },
  data(){
    return{
      example:"This is from v-html vue prop.",
      headingId:'head',
      isDisabled:"true",
      status:"danger",
      isPromoted:true,
      isNew:true,
      isSoldOut:false,
      dynFontSize:40,
      num:5
    }
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

.underline{
text-decoration: underline;
}

.danger{
  color: red;
}
.success{
  color:green;
}

.promoted{
  font-style: italic;
}

.new-movie{
color: orange;
}

.sold-out{
color:aqua;
}
</style>
