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
    
  },metaInfo() {
        return { 
            title: "API Vue App",
            meta: [
                { name: 'description', content:  'Collected all my API pet projects and display them all in singe web app.'},
                { property: 'og:title', content: "API Vue App - Another vue pet project."},
                { property: 'og:site_name', content: 'API Vue Appssss'},
                { property: 'og:type', content: 'website'},    
                { name: 'robots', content: 'index,follow'},
                { property: 'og:image', content: "@/assets/images/logo.png" || ''}
            ]
        }
    }
}
</script>

<style>
  @import './App.css';
  
</style>
