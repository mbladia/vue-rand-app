<template>
    <div class="news-container">
        <b-row  class="news-header">
            <!-- <b-col sm="0" class="text-center">
                <b-form-select class="dropdown-news" @change="getSelected()" v-model="selected" :options="options"></b-form-select>
            </b-col> -->
            <b-col  sm="12" class="d-flex-col mb-2">
                <b-input-group  class="mt-3">
                    <b-input-group-prepend>
                        <b-button  class="btn-clear" v-on:click="clear()"><b-icon icon="x" ></b-icon></b-button>
                    </b-input-group-prepend>
                    <b-form-input type="text" v-model="searched" class="input-text" placeholder="Search"> </b-form-input>
                    <b-input-group-append>
                        <b-button variant="primary"  v-on:click="getSelected()">Search</b-button>
                    </b-input-group-append>
                </b-input-group>
            </b-col>
            
            <!-- <b-col  sm="12" class="d-flex-col mb-2">
                <b-form-input type="text" v-model="searched" class="input-text" placeholder="Search"> </b-form-input>
            </b-col>
            <b-col sm="12" class="text-center">
                <b-button variant="light" class="btn-clear"  v-on:click="clear()">Clear</b-button>
                <b-button variant="primary"  v-on:click="getSelected()">Search</b-button>                
            </b-col> -->
        </b-row >
        <div class="list-result" v-if="totalResults > 0">
            <b-form-select class="dropdown-news" @change="getSelected()" v-model="selected" :options="options"></b-form-select>
            <b-row  class="result-box" v-for="(article, index) in articles" :key="index">
                <h5 class="news-title">{{article.title}}</h5>
                <b-col class="img-min-box" sm="12" lg="3" md="12">
                    <div class="news-image" v-if="article.urlToImage" :style="{'background-image':'url(' + article.urlToImage +')'}"></div>
                    <div class="news-image" v-else :style="{'background-image':'url(' + imgPlaceholder +')'}"></div> 
                </b-col>
                <b-col lg="8" sm="12">
                    <p>{{article.description}}</p>
                </b-col>
            </b-row>
        </div>

        <div class="list-result" v-else>
            <b-row>
                <h2 class="text-center">No Result</h2>
            </b-row>
        </div>
         <!-- <button class="btn-submit mt-4 text-center" v-on:click="loadMore()">Load More</button> -->
    </div>
</template>

<script>
export default {
    name: "NewsAPI",
    data(){
        return{
            articles:[],
            selected: 'general',
            options: [
                { value: 'general', text: 'General' },
                { value: 'business', text: 'Business' },
                { value: 'entertainment', text: 'Entertainment' },
                { value: 'health', text: 'Health' },
                { value: 'science', text: 'Science' },
                { value: 'sports', text: 'Sports' },
                { value: 'technology', text: 'Technology' },
                // { value: { C: '3PO' }, text: 'This is an option with object value' },
                // { value: 'd', text: 'This one is disabled', disabled: true }
            ],
            pageSize: 20,
            "imgPlaceholder":  require("../assets/img-placeholder.jpg") ,
            searched:"",
            "totalResults": 20,
            // "page": 1
        }
    },
    methods:{
        async getData(){
            const api_key = process.env.VUE_APP_NEWS_API;
            console.log(api_key);
            const selectCategory = this.selected
            let pageSize = this.pageSize
            let searched = this.searched
            // let page = this.page
            const qry = await fetch(`https://newsapi.org/v2/top-headlines?apiKey=${api_key}&country=ph&category=${selectCategory}&pageSize=${pageSize}&q=${searched}`)
            const dataToJson = await qry.json();

            this.totalResults = dataToJson.totalResults

            dataToJson.articles.forEach(element => {
                this.articles.push(element)
            })
            

        },
        doMath: function (index) {
            return index+1
        },
        getSelected(){
            
            this.articles.length = 0;
            window.onload = this.getData()
        },
        clear(){
            this.searched = ""
            window.onload = this.getData()
        },
        // loadMore(){
        //     this.page ++
        //     console.log(this.page);
        //     this.getData()
        // }
    },
    created(){
        this.getData()
    }
}
</script>

<style scoped>
    .d-flex-col{
        display: flex;
        /* flex-direction: row; */
    }
    .dropdown-news{
        outline: none;
        border-radius: 3px;
        border: none;
        padding: 0.375rem 0.75rem;
        /* width: 100%; */
        background-color: rgb(235, 235, 235);
        cursor: pointer;
    }
    .space-header{
        margin: 0 29px;
    }
    .news-container{
        text-align: left;
        position: relative;   
    }

    .news-image{
        height: 150px;
        /* min-width: 100%; */
        background-size:cover;
        background-position: center;
        /* margin-left: 13px; */
    }
    
    .news-title{
        cursor: pointer;
        margin-left: 0;
    }
    /* .news-title::before{
        position: absolute;
        left: 4px;
        content: "";
        background-color: red;
        height: 10px;
        margin-top: 7px;
        width: 10px;
        border-radius: 100%;
    } */
    .news-title:hover{
        color: rgb(0, 67, 129);
    }
    .news-header{
        position: sticky;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgb(238, 238, 238);
        display: flex;
        align-items: center;
        justify-content: center;
        padding: 5px;
    }
    .list-result{
        padding: 5px 16px 0 20px;
    }
    .result-box{
        border-bottom: 1px solid rgb(224, 224, 224);
        padding-bottom: 20px;
        padding-top: 20px;
    }
    .btn-submit{
        
        display: flex;
        justify-content: center;
        align-items: center;
    }

    @media only screen and (max-width: 991px) {
        .news-image{
            height: 250px;
        }
    }

</style>