<template>
    <b-container class="card-container">
        <div class="row no-gutters card-to d-flex justify-content-center" >
            <b-col class="d-flex justify-content-center" cols="12" xl="3" lg="4" md="4" sm="6" v-for="item in items" :key="item.id">
                <b-card b-model="card" 
                    :title="item.title"
                    :img-src="item.imgSrc"
                    img-alt="Image"
                    img-top
                    tag="article"
                    style="max-width: 20rem;"
                    class="mb-2 mt-2"
                >
                    <b-card-text>{{item.description}}</b-card-text>
                <!-- <b-button class="w-100" href="#" pill variant="info">Try it</b-button> -->
                    <b-button class="w-100" id="show-btn" @click="$bvModal.show('bv-modal-example')" v-on:click="passToModal(item.id, item.title, item.api)">Try It!</b-button>
                    
                </b-card>

            </b-col>
        </div>
        
        <Modal :modalTitle=itemClicked :modalId=passId :modalApiSrc=itemApiSrcClick />
        
    </b-container>
</template>

<script>

import Modal from './Modal.vue'

export default {

    name: "Card",
    components: {
        Modal
    },
    transformToRequire: {
        'video': 'src',
        'source': 'src',
        'img': 'src',
        'image': 'xlink:href',
        'b-card': 'img-src'
    },
    data(){
        
        return{
            
            "passId":"",
            "itemClicked":"",
            "itemApiSrcClick": "",
            items:[
                
                {
                    "id":1,
                    "title": "Random Dog Breed",
                    "description" : "Because everyday is a Dog Day. Show a random dog breed.",
                    "imgSrc": require("../assets/dog-breed-app.jpg") ,
                    "app-link": "",
                    "api": "The Dog API - www.thedogapi.com"                  
                },
                {
                    "id":2,
                    "title": "Random Food Joke",
                    "description" : "Show a random joke that is related to food. Caution: this is an endpoint for adults!",
                    "imgSrc": require("../assets/rand-food-jokes.jpg") ,
                    "app-link": "",
                    "api":"Spoonacular API - www.spoonacular.com/food-api"
                },
                {
                    "id":3,
                    "title": "Random Cat Breed",
                    "description" : "Because everyday is a Caturday. Show a random cat breed.",
                    "imgSrc":require("../assets/rand-cat-breed.jpg"),
                    "app-link": "",
                    "api":"The Cat API - www.thecatapi.com"
                },
                {
                    "id":4,
                    "title": "NewsAPI",
                    "description" : "Show top and breaking headlines in philippines, articles are sorted by the earliest date published first.",
                    "imgSrc": require("../assets/news-api.jpg"),
                    "app-link": "",
                    "api":"News API - www.newsapi.org"

                },
                // {
                //     "id":5,
                //     "title": "Random Dog Breed",
                //     "description" : "This is just sample dog random breed",
                //     "imgSrc": "@/assets/dog-breed-app.jpg",
                //     "app-link": "",

                // },{
                //     "id":6,
                //     "title": "Random Dog Breed",
                //     "description" : "This is just sample dog random breed",
                //     "imgSrc": "../assets/dog-breed-app.jpg",
                //     "app-link": "",

                // },{
                //     "id":7,
                //     "title": "Random Dog Breed",
                //     "description" : "This is just sample dog random breed",
                //     "imgSrc": "../assets/dog-breed-app.jpg",
                //     "app-link": "",

                // }
            ]
        }
    },
    
    methods: {
        passToModal(itemId, modalItemTitle, itemApiSrc){
            this.passId = itemId
            this.itemClicked = modalItemTitle  
            this.itemApiSrcClick = itemApiSrc 
        }
        
    },
    
}
</script>

<style scoped>
    .card-container{
        min-height: 85vh;
    }
    .card-body{
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        font-family: 'Montserrat', sans-serif;
    }
    .card-to a{
        color: white;
    }
    .card{
        margin: 0 10px;
    }
</style>