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

    <template v-if="isDisplay">
      <h2>This section is using template instead of div</h2>
      <h2 v-show="isDisplay" class="underline">v-show vs v-if</h2>
      <h2> v-show is toggle between display none to display block css property.</h2>
    </template>

    <div>
      <h2 class="underline">v-for directive for Array of strings, objects, arrays block of html and object key value pairs</h2>
      <h2 class="underline">1.Array of Strings:</h2>
      <h2 v-for="(heroName,index) in names" :key="heroName">{{index}} {{heroName}}</h2>
      <h2 class="underline">2.Array of objects</h2>
      <h2 v-for="(heroFullName,index) in fullNames" :key="heroFullName.first">{{(index+1)}} {{heroFullName.first}} {{heroFullName.last}}</h2>
      <h2 class="underline">3.Array of array</h2>
      <div  v-for="actor in actors" :key="actor.actorName">
          <h2 class="sub-menu">{{actor.actorName}}</h2>
          <h2 v-for="movie in actor.movies" :key="movie">{{movie}}</h2>
      </div>

      <h2 class="sub-menu">My Info | Object | v-for</h2>
      <h2 v-for="value in myInfo" :key="value">{{value}}</h2>
    </div>

    <h2 class="underline">Methods or functions</h2>
    <h2>Add Three Numbers (10+20+30)= {{add(10,20,30)}}</h2>
    <h2>Multiped by 5= {{baseMultiplier(5 )}}</h2>

    <div>
      <h2 class="underline">Click and other events</h2>
      <h2>{{myUserName}}</h2>
      <button v-on:click="myUserName='Rahman'">Change Name</button>
      <h2>{{count}}</h2>
      <button @click="(count+=1)">Increase</button>
      <button @click="(count-=1)">Decrease</button>
      <br/>
      <button @click="getEvent">Click to Pass the event and Check the Console</button>
      <button @click="passValue(5)">Pass value to method</button>
      <br/>
      <button @click="passArgNevent(10,$event)">Pass arguement and event</button>
      <br/>
      <br/>
      <h2>Event 1:{{myNum}} | Event 2:{{myUserName}} </h2>
      <button @click="(increaseFive(5),changeVal('red'))">Handle Two Events on One Click</button>
    </div>

    <div>
      <h2 class="underline"></h2>
    </div>

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
      num:5,
      isDisplay:true,
      names:['Bruce Wayne', 'Clark Cent', 'Aurthur'],
      fullNames:[
        {first:'Peter',last:'Parker'},
        {first:'Tony',last:'Stark'},
        {first:'Thor',last:'Odin'},
      ],
      actors:[
        {
          actorName:"Ben Stiller",
          movies:['Secret Life of Walter Mitty', 'Brads Status', 'Something about Marry']
      },
      {
        actorName:"Natalie Portman",
        movies:['Black Swan', 'Star Wars']
      }
      ],
      myInfo:{
        myName:'Habib',
        job:'Web Dev',
        age:'26'
      },
      multiplierNum:5,
      myUserName:"Habib",
      count:0,
      myNum:10
    }
  },
  methods:{
    add(a,b,c){
      return a+b+c;
    },
    baseMultiplier(num){
      //'this' keyward is used here bcz multiplierNum is a variable from data:{}
      return num*this.multiplierNum
    },
    getEvent(event){
      console.log(event)
    },
    passValue(num){
      console.log(num)
    },
    passArgNevent(val,e){
      console.log(val,e);
    },
    increaseFive(num){
      console.log(num)
      this.myNum = num + this.myNum
      return this.myNum
    },
    changeVal(strVal){
      console.log(strVal)
      this.myUserName = strVal+this.myUserName
      return this.myUserName
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
background-color: orange;
}

.sub-menu{
  background-color: green;
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
