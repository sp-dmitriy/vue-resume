<template>
 <form class="card card-w30">
      <div class="form-control">
        <label for="type">Тип блока</label>
        <select id="type" v-model="type">
          <option value="Title">Заголовок</option>
          <option value="Subtitle">Подзаголовок</option>
          <option value="Avatar">Аватар</option>
          <option value="Text">Текст</option>
        </select>
      </div>

      <div class="form-control">
        <label for="value">Значение</label>
        <textarea id="value" rows="3" v-model="value"></textarea>
      </div>

      <button class="btn primary" @click.prevent="submit" :disabled="isDisable">Добавить</button>
    </form>
</template>

<script>
import { v4 as uuidv4 } from 'uuid'

export default {
  data() {
    return {
      type:'Title',
      value:''
    }
  },
  methods: {
    submit() {
      this.$emit('add-block',{
        id: uuidv4(),
        type: this.type,
        value: this.value,
      })
      this.value = ''
      this.type = 'Title'
    }
  },
  computed: {
    isDisable() {
      return this.value.length < 3
    }
  }
}
</script>
