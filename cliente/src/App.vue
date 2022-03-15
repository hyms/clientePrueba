<template>
  <div id="app">
    <b-tabs content-class="mt-3">
      <b-tab title="Listar Usuarios" active><Users></Users></b-tab>
      <b-tab title="Nuevo Usuario"><Form></Form></b-tab>
      </b-tabs>
    
  </div>
</template>

<script>
import Users from './components/listUsers.vue'
import Form from './components/formClient.vue'

export default {
  name: 'App',
  components: {
    Users,
    Form
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
