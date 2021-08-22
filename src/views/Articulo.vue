<template>
  <Titulo texto="Artículo con parámetros"/>
  <h2>Parámetro: {{ $route.params.id }}</h2>
  <h3>{{ post.title }}</h3>
  <p>{{ post.id }} - {{ post.body }}</p>
</template>

<script>
import Titulo from '../components/Titulo'

export default {
  components: {
    Titulo
  },
  data() {
    return {
      post: {}
    }
  },
  methods: {
    async getPost() {
      try {
        const data = await fetch(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`)
        const item = await data.json()
        console.log(item)
        this.post = item
      } catch (error) {
        console.log(error)
      }
    }
  },
  created() {
    this.getPost()
  }
}
</script>

<style>

</style>