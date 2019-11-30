<template>
  <section>
    <h2>Open New Issue</h2>
    <div>
      <form>
        <div class="form-group">
          <label>Title</label>
          <input type="text" class="form-control" v-model="form.title">
        </div>
        <a class="btn btn-primary" tabindex="" @click="submit">submit</a>
      </form>
    </div>
  </section>
</template>

<script>

export default{
    data(){
        return{
            form: {
                title: "",
                body:""
            }
        }
    },
    methods:{
        async submit(){
            const url = `/repos/lec-cafe/books_nuxtjs_practice/issues/`
            const requestBody = {
                title: this.form.title,
                body: this.form.body,
            }
            await this.$axios.post(url, requestBody,{
                headers:{
                    Authorization:"105799ca7d01363042c951a7fabb0fda55059e26"
                }
            })
            this.$router.push("/")
        }
    }
}
</script>

<style>

</style>
