<template>
    <div>
        <b-navbar type="dark" class="header-title d-flex justify-content-center">
            <b-navbar-brand href="#">
            <!-- <img src="https://.com/g/30/30" class="d-inline-block align-top" alt="Kitten"> -->
                <b-navbar-brand tag="h1" class="mb-0">{{msg}}</b-navbar-brand>
            </b-navbar-brand>
        </b-navbar>
    </div>
</template>

<script>
export default {
    name: 'Header',
    props:{
        msg: String
    }
}
</script>

<style scoped>
.header-title{
    background-color: cadetblue;
    height: 100px;
    font-family: 'Limelight', cursive;
} 
.header-title h1{
    font-size: 3rem;
}

@media screen and (max-width: 576px) {
    .header-title h1{
        font-size: 2rem;
    }
  }
</style>