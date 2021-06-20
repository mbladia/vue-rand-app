<template>
    <div class="center-all-container">
        <!-- <h1 class="title">{{ appTitle }}</h1> -->
        <b-row class="justify-content-md-center row-no-margin">
            <b-col sm="12" lg="6" class="">
                    <div class="image-modal-main" :style="{'background-image': 'url('+ picture +')'}"></div>
            </b-col>
        
            <p class="dog-name"><b>Name:</b> {{ firstName }}</p>
            <p class="breed-for"><b>Breed for:</b> {{ breedFor }}</p>
            <p class="temperament"><b>Temperament:</b> {{ temperament }}</p>
            <b-col>
                <button class="btn-submit" v-on:click="getDog()">Random</button>
            </b-col>
        </b-row>
    </div>
</template>

<script>
export default {
    
    name: "RandDogAPI",
    data(){
        return {
            appTitle: "Random Dog Breed",
            firstName: "",
            breedFor: "",
            temperament: "",
            picture: "",
        }
    },
    methods: {
        async getDog(){
            // console.log(process.env.VUE_APP_RAND_DOG_BREED);
            const api_key = process.env.VUE_APP_RAND_DOG_BREED;
            // console.log(api_key);
            const qry =  await fetch(`https://api.thedogapi.com/v1/images/search?key=${api_key}&size=thumb&has_breeds=true&order=RANDOM&limit=1`)
            const data = await qry.json() 
            this.firstName = data[0].breeds[0].name,
            this.breedFor = data[0].breeds[0].bred_for,
            this.temperament = data[0].breeds[0].temperament,
            this.picture = data[0].url
        }
    }
}
</script>
<style scoped>

.dog-name{
    font-size: 30px;
    margin-bottom: 10px;
    text-align: center;
}
.breed-for{
    text-align: center;
    margin-bottom: 0;
}
.temperament{
    text-align: center;
}

</style>