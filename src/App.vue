<template>
  <div id="app">

    <article v-for="item in nutri" :key="item.id">
      <strong>{{item.titulo}}</strong>
      <img :src="item.capa" alt="">
      <span>Categoria: {{item.categoria}}</span>
      <p>{{item.subtitulo}}</p>
    </article>

  </div>
</template>

<script> 
import Api from "./services/Api"

export default{
  name: 'App',
  data(){
    return {
      nutri : []
    }
  },
  async created(){
    const res = await Api.get('?api=posts')
    this.nutri = res.data
  }
}

</script>

<style scoped>

</style>