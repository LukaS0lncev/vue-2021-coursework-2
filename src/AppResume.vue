<template>
  <div class="card card-w70">
    <div v-for="res in resume">
      <div v-if="res.type == 'title'"><h1>{{ res.value }}</h1></div>
      <div class="avatar" v-else-if="res.type == 'avatar'">
        <img :src="res.value">
      </div>
      <div v-else-if="res.type == 'subtitle'">
        <h2>{{ res.value }}</h2>
      </div>
      <div v-else-if="res.type == 'text'">
        <p>{{ res.value }}</p>
      </div>
    </div>
    <h3 v-if="resume.length == 0">Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>

<script>
    export default {
        props: ['resume']
    }
</script>

<style scoped>

</style>
