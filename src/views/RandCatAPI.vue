<template>
    <div>
        <h1></h1>
        <button v-on:click="getRandCat()">hello</button>
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
            const qry = await fetch('https://api.thecatapi.com/v1/images/search?&order=rand&limit=1&has_breeds=true&size=small');
            const dataJson = await qry.json();

            console.log(dataJson[0].breeds[0].name);
        }
    }
}
</script>

<style scoped>

</style>