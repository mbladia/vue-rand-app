<template>
    <div>
        <b-modal class="modaldal" id="bv-modal-example" hide-footer size="lg">
            <template #modal-title>
            <!-- <h2>{{modalTitle}}</h2> -->
            <h3>{{modalTitle}}</h3>
            </template>
            <div class="box-box d-block text-center" v-if="modalId == 1">
                <RandDogAPI />
            </div>
             <div class="box-box d-block text-center" v-if="modalId == 2">
                <RandFoodJokesAPI />
            </div>
            <div class="box-box d-block text-center" v-if="modalId == 3">
                <RandCatAPI />
            </div>
            <div class="box-box d-block text-center" v-if="modalId == 4">
                <NewsAPI />
            </div>
            
            <div style="height:20px;"></div>
            <div class="footer-modal"> {{modalApiSrc}}</div>
            <!-- <b-button class="mt-3" block @click="$bvModal.hide('bv-modal-example')">Close Me</b-button> -->
        </b-modal>
        
    </div>
</template>

<script>
import RandDogAPI from '../views/RandDogAPI.vue'
import RandFoodJokesAPI from '../views/RandFoodJokeAPI.vue'
import RandCatAPI from '../views/RandCatAPI.vue'
import NewsAPI from '../views/NewsAPI.vue'
export default {
    
    name: "Modal",
    props: ["modalId","modalTitle","modalApiSrc"],
    components:{
        RandDogAPI,
        RandFoodJokesAPI,
        RandCatAPI,
        NewsAPI
    },
    data(){
        
        return {
            "day":""
        }
    }    
}
</script>

<style>
    .box-box{
        min-height: 736px !important;
    }
    .modal-dialog{
        margin: 1 !important;
    }
    .modal-content{
        min-height: 85vh;
    }
    .modal-body{
        /* background-color: red; */
        height: 790px;
        overflow:auto;
        padding: 0 !important;
    }
    .close{
        border: 1px solid red;
    color: red;
    font-size: 18px;
    padding: 5px 20px;
    border-radius: 5px;
    background-color: rgba(255, 168, 168, 0.39);
    }
    .footer-modal{
        text-align: center;
        position: relative;
        bottom: 0;
        left: .1px;
        height: 30px;
        width: 100%;
        background-color: rgb(44, 148, 148);
        color: white;
        clear: both;
    }
</style>