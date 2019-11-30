<!--Issue　詳細画面-->
<template>
  <section>
    <h2 class="mb-3">#{{issue.number}}{{issue.title}}</h2>
    <div class="text-right mb-5">
      <a :href="issue.html_url">Open Github</a>
    </div>
    <div class="mb-5">{{issue.body}}</div>
    <router-link class="btn btn-outline-primary" to="/">back</router-link>
  </section>
</template>

<script>

  export default {
      async mounted(){
          const number = this.$route.params.id
          const url = `/lec-cafe/books_nuxtjs_practice/issues/${number}`
          const {data} = await this.$axios.get(url,{
              headers: {
                  Authorization: "105799ca7d01363042c951a7fabb0fda55059e26"
              }
          })
          console.log(data)
          this.issue = data
      },
      data(){
          return{
              issue:{
                  number: "1",
                  title: "Cras justo odio",
                  html_url: "https://github.com/lec-cafe/book_nuxt_api_state/issues/1",
                  body: "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ipsa nihil pariatur repudiandae soluta voluptas! Aperiam asperiores atque corporis ex hic illum in incidunt iure minus non obcaecati provident quam, voluptatum?"
              },
          }
      }
  }
</script>

<style>

</style>
