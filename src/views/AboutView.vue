<template>
  <div class="about">
    <h1>This is an about page</h1>
    {{ vuetxt }}
    {{ data }}
  </div>
</template>

<script>
export default {
  data() {
    return {
      data: {},
      vuetxt: ''
    } 
  },
  mounted() {
    // console.log(import.meta.env.VITE_TEXT)
    this.vuetxt = import.meta.env.VITE_TEXT

    const path = import.meta.env.VITE_PATH
    this.$http.get(path)
    .then((res) =>{
      console.log(res);
      this.data = res.data.results[0];
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
