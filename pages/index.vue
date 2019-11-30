<template>
  <section>
<!--    <div class="container">-->
<!--      <div>-->
<!--        <logo />-->
<!--        <h1 class="title">-->
<!--          my_issue_app-->
<!--        </h1>-->
<!--        <h2 class="subtitle">-->
<!--          My ace Nuxt.js project-->
<!--        </h2>-->
<!--        <div class="links">-->
<!--          <a-->
<!--            href="https://nuxtjs.org/"-->
<!--            target="_blank"-->
<!--            class="button&#45;&#45;green"-->
<!--          >-->
<!--            Documentation-->
<!--          </a>-->
<!--          <a-->
<!--            href="https://github.com/nuxt/nuxt.js"-->
<!--            target="_blank"-->
<!--            class="button&#45;&#45;grey"-->
<!--          >-->
<!--            GitHub-->
<!--          </a>-->
<!--        </div>-->
<!--      </div>-->
<!--    </div>-->

<!--  issue 一覧画面の作成-->
    <h2>ISSUES</h2>
    <div class="text-right mb-3">
      <router-link class="btn byn-outline-primary" to="/new">Open New Issue</router-link>
    </div>
    <div>
      <div class="list-group list-group-flush">
        <router-link :to="`/issue/${issue.number}`" class="list-group-item-action" v-for="(issue,index) in issues" :key="index">
          <div class="">#{{issue.number}} {{issue.title}}</div>
        </router-link>
      </div>
    </div>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue'

export default {
  // components: {
  //   Logo
  // },
  data(){
      return{
        issues: [
            {number: "1", title: "Cras justo odio"},
            {number: "2", title: "Dapibus ac facilisis in"},
            {number: "3", title: "Morbi leo risus"},
            {number: "4", title: "Porta ac consectetur ac"},
            {number: "5", title: "Vestibulum at eros"},
        ]
      }
  },
    async mounted(){
      const url = "/repos/lec-cafe/books_nuxtjs_practice/issues"
      const response = await this.$axios.get(url,{
          headers:{
              Authorization:"105799ca7d01363042c951a7fabb0fda55059e26"
          }
      })
        console.log(response)
        this.issues = response.data
    }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
