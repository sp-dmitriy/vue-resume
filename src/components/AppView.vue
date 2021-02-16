<template>
  <div class="card card-w70">
    <div v-if="blocks.length">
      <component 
        v-for="block in blocks" 
        :key="block.id"  
        :is="'AppView' + block.type"
        :value="block.value"
      ></component>
    </div> 
    <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>

<script>
import AppViewTitle from './AppViewTitle'
import AppViewSubtitle from './AppViewSubtitle'
import AppViewAvatar from './AppViewAvatar'
import AppViewText from './AppViewText'

export default {
  props: {
    blocks: Array
  },
  components: {
    AppViewTitle, AppViewSubtitle, AppViewAvatar, AppViewText
  }
}
</script>
<style scoped>
h3{
  text-align: center;
}

</style>