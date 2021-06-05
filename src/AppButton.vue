<template>
    <p>
      <button class="btn primary" @click="$emit('load')">Загрузить комментарии</button>
    </p>
</template>

<script>
    export default {
        emits: ['load']
    }
</script>

<style scoped>

</style>
