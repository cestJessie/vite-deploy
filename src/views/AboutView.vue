<template>
  <div class="about">
    <h1>This is an about page</h1>
    {{ data }}
  </div>
</template>

<script>
export default {
  //  data、mounted 都是 Vue 生命週期中，必要實體化過程的一部分，所以會強迫執行函數
  data() {
    return {
      data: {}
    }
  },
  mounted() {
    console.log(import.meta.env.VITE_TEXT)
    const url = import.meta.env.VITE_PATH
    this.$http.get(url) // https://randomuser.me/ 假API
      .then((res) => {
        console.log(res)
        this.data = res.data.results[0]
        console.log(this.data)
      })
  }
}
</script>


<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
