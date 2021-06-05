<template>
  <form class="card card-w30" @submit.prevent>
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select id="type" v-model="selectValue">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea id="value" rows="3" v-model.trim="textareaValue"></textarea>
    </div>

    <button :disabled="isDisabled" class="btn primary" @click="resumeValue">Добавить</button>
  </form>
</template>

<script>
    export default {
        emits: ['resumeValue'],
        data() {
            return {
                selectValue: 'title',
                textareaValue: '',
                arrayValue: [],
                isDisabled: true,
                results: []
            }
        },
        methods: {
            resumeValue() {
                this.arrayValue = {type:  this.selectValue, value: this.textareaValue}
                this.$emit('resumeValue', this.arrayValue)
                this.selectValue = 'title'
                this.textareaValue = ''
            }
        },
        watch: {
            textareaValue() {
                this.isDisabled = (this.textareaValue.length > 3) ? false : true
            }
        }
    }
</script>

<style scoped>

</style>
