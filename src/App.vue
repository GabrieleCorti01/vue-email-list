<template>
  <div id="app">
    <HelloWorld />

    <ul>
      <li v-for="(element, index) in numeroRandomico" :key="index">
        {{ numeroRandomico }}
      </li>
    </ul>

  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios';

export default {
  name: 'App',
  components: {
    HelloWorld
  },
data: function(){
  return {
    numeroRandomico : '',
  }
},

  mounted() {
    console.log(axios);

    axios.get('https://flynn.boolean.careers/exercises/api/random/int')

  .then ((response) => {
    const result = response.data;
    console.log(result.response);
    this.numeroRandomico = result.response;
    });
  } 
}

</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
