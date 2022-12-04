<template>
    <div>
        <h2>My Age: {{age}}</h2>
        <h2>Favorite Movie: {{favMovie}}</h2>
        <h2>Love to do: {{loveTo}}</h2>
        <h2>Studying: {{studyCourse}}</h2>
    </div>
</template>

<script>
export default{
    name:"SecondComponent",
    props:{
        age:Number,
        favMovie:String,
        loveTo:String,
        studyCourse:String
    }
}
</script>

<style>

</style>