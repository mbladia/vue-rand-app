<template>
  <div>
    <Header msg="Random App API" />
    <Card /> 
    
    <Footer />
  </div>
</template>

<script>

import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
// import Modal from './components/Modal.vue'
import Card from './components/Card.vue'

export default {
  name: 'App',
  components: {
    Header,
    Footer,
    Card
    
  }
}
</script>

<style>
  @import './App.css';
  
</style>
