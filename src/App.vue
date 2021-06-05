<template>
  <div class="container column">
    <app-form
    @resumeValue="resumeValue"
    ></app-form>
    <app-resume
    :resume="resume"
    ></app-resume>
  </div>

  <app-comments></app-comments>
</template>


<script>
import AppComments from "@/AppComments"
import AppForm from "@/AppForm"
import AppResume from "@/AppResume"
export default {
    data() {
        return {
          test: null,
          resume: []
        }
    },
    methods: {
        async loadPeople() {
            const response = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=42', {
                method: 'GET'
            })
            let comments = await response.text()
            this.comments = JSON.parse(comments)
        },
        resumeValue(value) {
            this.resume.push(value)
            console.log(this.resume)
        }
    },
    components: {AppComments, AppForm, AppResume}
}

</script>

<style>
  .avatar {
    display: flex;
    justify-content: center;
  }

  .avatar img {
    width: 150px;
    height: auto;
    border-radius: 50%;
  }
</style>
