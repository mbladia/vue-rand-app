<template>
    <div>
        <b-modal class="modaldal" id="bv-modal-example" hide-footer size="lg">
            <template #modal-title>
            <!-- <h2>{{modalTitle}}</h2> -->
            <h3>{{modalTitle}}</h3>
            </template>
            <div class="d-block text-center" v-if="modalId == 1">
                <RandDogAPI />
            </div>
             <div class="d-block text-center" v-if="modalId == 2">
                <RandFoodJokesAPI />
            </div>
            <div class="d-block text-center" v-if="modalId == 3">
                <RandCatAPI />
            </div>
            <div class="footer-modal"> {{modalApiSrc}}</div>
            <!-- <b-button class="mt-3" block @click="$bvModal.hide('bv-modal-example')">Close Me</b-button> -->
        </b-modal>
    </div>
</template>

<script>
import RandDogAPI from '../views/RandDogAPI.vue'
import RandFoodJokesAPI from '../views/RandFoodJokeAPI.vue'
import RandCatAPI from '../views/RandCatAPI.vue'
export default {
    
    name: "Modal",
    props: ["modalId","modalTitle","modalApiSrc"],
    components:{
        RandDogAPI,
        RandFoodJokesAPI,
        RandCatAPI
    },
    data(){
        
        return {
            "day":""
        }
    }    
}
</script>

<style>
    .modal-dialog{
        margin: 1 !important;
    }
    .modal-content{
        min-height: 95vh;
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
        position: absolute;
        bottom: 0;
        left: .1px;
        height: 30px;
        width: 100%;
        background-color: rgb(44, 148, 148);
        color: white;
    }
</style>