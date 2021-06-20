<template>
    <div class="center-all-container">

        <div class="image-modal-main" :style="{'background-image': 'url('+ imgUrl +')'}"></div>
        <p class="cat-name"><b>Name:</b> {{ name }}</p>
        <p class="origin"><b>Origin:</b> {{ origin }}</p>
        <p class="temperament"><b>Temperament:</b> {{ temperament }}</p>
        <p class="description"><b>Description:</b> {{ description }}</p>
        <button class="btn-submit" v-on:click="getRandCat()">Random</button>
   
    </div>
</template>

<script>
export default {
    name: "RandCatAPI",
    data(){
        return{
            "name":"",
            "temperament":"",
            "origin":"",
            "description":"",
            "imgUrl":""
        }
    },
    methods:{
        async getRandCat(){
            const api_key = process.env.VUE_APP_RAND_CAT_BREED;

            const qry = await fetch(`https://api.thecatapi.com/v1/images/search?key=${api_key}&order=rand&limit=1&has_breeds=true&size=small`);
            const dataJson = await qry.json();
            const data = dataJson[0].breeds[0];
            // console.log(dataJson[0].url);
            // console.log(data);

            this.name = data.name
            this.temperament = data.temperament
            this.origin = data.origin
            this.description = data.description
            this.imgUrl = dataJson[0].url

        }
    }
}
</script>

<style scoped>

.cat-name{
    font-size: 30px;
    margin-bottom: 10px;
}
.origin{
    margin-bottom: 0;
}

.description.origin.temperament.cat-name{
    text-align: center;
}
</style>