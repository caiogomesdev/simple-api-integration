<template>
  <div id="app">
    <Header />
    <div v-if="isLoading">
      <img class="img-loading" src="./assets/loading-buffering.gif" />
    </div>
    <article v-else v-for="item in nutri" :key="item.id" class="post">
      <strong class="title">{{item.titulo}}</strong>
      <img :src="item.capa" />
      <span class="category">Categoria: {{item.categoria}}</span>
      <p class="subtitle">{{item.subtitulo}}</p>
      <a href="#" class="button">Acessar</a>
    </article>

  </div>
</template>

<script> 
import Api from "./services/Api"
import Header from "./components/Header.vue"
export default{
  name: 'App',
  components:{
    Header
  },
  data(){
    return {
      nutri : [],
      isLoading: true
    }
  },
  async created(){
    this.isLoading = true;
    const res = await Api.get('?api=posts')
    this.nutri = res.data;
    this.isLoading = false;
  }
}

</script>

<style scoped>
#app{
  display: flex;
  flex-direction: column;
  width: 100%;
  justify-content: center;
  align-items: center;
}
.post{
  display: flex;
  flex-direction: column;
  width: 700px;
  border-radius: 7px;
  margin: 8px;
  background-color: #fff;
  padding: 10px;
}
.title{
  font-size: 25px;
  margin: 25px 0px 10px 0px;
}
.category{
  padding: 15px 0px 8px 0px;
  font-weight: bold;
}
.button{
  margin-top: 10px;
  height: 40px;
  background: none;
  border: 2px solid #4c89e3;
  color: #4c89e3;
  border-radius: 5px;
  display: flex;
  justify-content: center;
  align-items: center;
  text-decoration: none;
  font-size: 18px;
  transition: all ease-in-out .4s;
}
.button:hover{
  background-color: #4c89e3;
  color: #fff;
}
.img-loading{
  width: 70px;
  margin-top: 20px;
}
</style>