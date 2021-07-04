<template>
    <div class="cat-container">
        <!-- <h1 class="title">{{title}}</h1> -->
        <h1 class="user-message">{{userMessage}}</h1>
        <h4 class="mt-4">{{text}}</h4>
        <button class="btn-submit mt-4" v-on:click="getFoodJoke">Random</button>
    </div>
</template>

<script>
// const aws = require('aws-sdk');
// let api_key =  process.env.VUE_APP_RAND_FOOD_JOKE_API

export default {
    name: "RandFoodJokesAPI",
    data() {
        return{
            title: "Random Food Jokes",
            userMessage: "Enjoy!!!!!",
            text: "Click button to show random food jokes",
            items: ['🤣 Ok','😂','🤣🤣 Hahaha','😆 LOL','😝 Ohhh','🙄🙄',
            '🤣','🤪']
        }
    },
    methods: {
        async getFoodJoke(){
            // console.log(process.env.VUE_APP_RAND_FOOD_JOKE_API);
            const api_key = process.env.VUE_APP_RAND_FOOD_JOKE_API;
            console.log(api_key);
            const api_url = `https://api.spoonacular.com/food/jokes/random?apiKey=${api_key}`
            const qry = await fetch(api_url)
            const res = await qry.json()
            const randNum = Math.floor(Math.random() * 8)
            
            this.userMessage = ""
            this.title = ""
            this.text = res.text
            setTimeout(() => {  this.userMessage = this.items[randNum]; }, 3000);
        }
    }
}
</script>
<style scoped>
    .cat-container { 
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    height: 740px;
    padding: 10px;
}
</style>