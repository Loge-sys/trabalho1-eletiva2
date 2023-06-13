<script setup>
</script>

<template>
  <main>
    <h1>Busque o personagem da disney</h1>
    <div class="container_input">
      <input type="search" v-model="input_busca" placeholder="Insira o nome">
      <input type="button" value="Buscar" @click="buscar()">
    </div>
    <div v-if="itens_response && itens_response.length < 1 && buscou">
      <p v-if="erro_requisicao">Ocorreu um erro ao processar a requisição!</p>
      <p v-else>Nenhum registro encontrado!</p>
    </div>
    <div v-else>
      <div v-if="Array.isArray(itens_response)">
        <div class="container_info"  v-for="(item, index) in itens_response" :key="index">
            <img :src='item.imageUrl'>
            <p>{{ item.name }}</p>
        </div>
      </div>
      <div v-else>
        <img :src='itens_response.imageUrl'>
        <p>{{ itens_response.name }}</p>
      </div>
    </div>
  </main>
</template>

<script>
import api from '../services/api'
export default {
    name: 'Menu',
    components: { api },
    data () {
      return {
        input_busca: '',
        itens_response: [],
        buscou: false,
        erro_requisicao: false
      }
    },
    methods: {
      buscar () { 
        api.get(`?name=${this.input_busca}`).then(res => {
          this.buscou = true   
          this.itens_response = res.data.data
        }).catch(() => {
          this.erro_requisicao = true
          this.buscou = true            
        }).finally(() => {
          setTimeout(() => {
            this.buscou = false
          }, 3000);
        })     
      }
    }
}
</script>

<style scoped>
  .container_input {
    margin-top: 20px;
  }

  .container_info {
    margin-top: 20px;
  }
</style>