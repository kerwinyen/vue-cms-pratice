


<template>
  <div id="customers-home">
    <h1>{{ page_title }}</h1>
    <div v-for="(page,index) in pages" :key="page.slug + '_' + index">
      <router-link :to="'/customers/' + page.slug">
        <div>
          <img :src="page.fields.customer_logo" alt="">
          <h2>{{ page.fields.headline }}</h2>
        </div>
      </router-link>
    </div>
  </div>
</template>


<script>
  import { butter } from './buttercms'
  export default {
    name: 'customers-home',
    data() {
      return {
        slug: this.$route.params.slug,
        page: {
          slug: '',
          fields: {}
        }
      }
    },
    methods: {
      getPage() {
        butter.page.retrieve('customer_case_study', this.slug)
          .then((res) => {
            console.log(res.data.data)
            this.page = res.data.data
          }).catch((res) => {
            console.log(res)
          })
      }
    },
    created() {
      this.getPage()
    }
  }
</script>