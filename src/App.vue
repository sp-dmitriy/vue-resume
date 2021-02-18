<template>
  <div class="container column">
    <app-form
       @add-block="addBlock"
    ></app-form>
    <app-view
      :blocks="blocks"
    ></app-view>
  </div>
  <div class="container">
    <app-comments
      v-if="!isLoading" 
      :comments="comments"
      @load="loadComments"
    ></app-comments>
    <app-loading v-else></app-loading>
  </div>  
</template>

<script>
import axios from 'axios'
import AppForm from './components/AppForm'
import AppView from './components/AppView'
import AppLoading from './components/AppLoading'
import AppComments from './components/AppComments'

export default {
  data() {
    return {
      blocks: [],
      comments: [],
      isLoading:false,
    }
  },
  methods: {
    addBlock(data) {
      this.blocks.push(data)
    },
    async loadComments() {
      this.isLoading = true
      try{
         const res = await axios.get('https://jsonplaceholder.typicode.com/comments?_limit=42')
         this.comments = res.data
         
      } catch(e) {
        console.log(e.message)
      }    
      this.isLoading = false
    }
  },
  components: {
    AppForm, AppView,AppLoading,AppComments
  }
}
</script>

<style>

</style>
