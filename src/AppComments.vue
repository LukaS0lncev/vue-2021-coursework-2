<template>
  <div class="container">
    <app-button @load="loadComments"></app-button>
    <div v-if="visibleComments">
      <div class="card" v-if="comments.length > 0">
        <h2>Комментарии</h2>
        <ul class="list">
          <li class="list-item" v-for="comment in comments" :key="comment.id">
            <div>
              <p><strong>{{ comment.email }}</strong></p>
              <small>{{ comment.body }}</small>
            </div>
          </li>
        </ul>
      </div>
      <app-loader v-else></app-loader>
    </div>

  </div>
</template>

<script>
    import AppButton from "@/AppButton"
    import AppLoader from "@/AppLoader"
    export default {
        data() {
            return {
                visibleComments: false,
                comments: []
            }
        },
        methods: {
            async loadComments() {
                this.visibleComments = true
                const response = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=42', {
                    method: 'GET'
                })
                let comments = await response.text()
                this.comments = JSON.parse(comments)
            }
        },
        components: {AppButton, AppLoader}
    }
</script>

<style scoped>

</style>
