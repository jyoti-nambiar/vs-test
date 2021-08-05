<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <ImageListMain msg="Welcome to Your Vue.js App"/>
    
  </div>
</template>

<script>
import ImageListMain from './components/ImageListMain.vue'

import axios from 'axios'
export default {
  name: 'App',
data(){
return {
    resource_url:"https://picsum.photos/v2/list?page=2&limit=100",
    
    imageData:[],

    options: {
      remote_data: 'nested.data',
      remote_current_page: 'nested.current_page',
      remote_last_page: 'nested.last_page',
      remote_next_page_url: 'nested.next_page_url',
      remote_prev_page_url: 'nested.prev_page_url',
      next_button_text: 'Go Next',
      previous_button_text: 'Go Back'
    }
   }

},
  components: {
    ImageListMain,
  },

methods: {
      
 updateResource:function(){

     axios.get("https://picsum.photos/v2/list?page=2&limit=100")
          .then(response=>{
            this.imageData = response.data;
            // console.log(JSON.stringify(this.picdetails)) 
          })

   },






    }




}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
