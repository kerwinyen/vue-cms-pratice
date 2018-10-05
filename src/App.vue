<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
  <div>
    <router-view/>7
  </div>
</div>

</template>

<script>
  import { butter } from './buttercms'
  export default {
    name: 'App',
    data() {
      return {
        page_title: 'Customers',
        // Create array to hold the pages from ButterCMS API
        pages: []
      }
    },
    methods: {
      // Get List of Customer Pages
      getPages() {
        butter.page.list('customer_case_study')
          .then((res) => {
            console.log(res.data.data) // Check the results in the console
            this.pages = res.data.data
          })
      }
    },
    created() {
      // Fire on page creation
      console.log(butter.page,' from butter')
      this.getPages()
    }
  }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
