<template>
  <div class="card card-w70">
    <div v-if="blocks.length">
      <component 
        v-for="block in blocks" 
        :key="block.id"  
        :is="'r-' + block.type"
        :value="block.value"
      ></component>
    </div> 
    <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>

<script>
import rTitle from './AppViewBlock/r-title'
import rSubtitle from './AppViewBlock/r-subtitle'
import rAvatar from './AppViewBlock/r-avatar'
import rText from './AppViewBlock/r-text'

export default {
  props: {
    blocks: Array
  },
  components: {
   rTitle, rSubtitle, rAvatar, rText
  }
}
</script>
<style scoped>
h3{
  text-align: center;
}

</style>