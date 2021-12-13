<template>
  <div class="container">
    <div>
      <h1>Buscar Operadoras</h1>
      <input v-model="searchText">
    </div>
    <ul v-if="operadoras.length">
      <li v-for="operadora in operadoras" :key="operadora.registro_ans">
        {{operadora.razao_social}}
      </li>
    </ul>
  </div>
</template>

<script> 
import axios from 'axios'
import debounce from 'debounce'

export default {
  name: 'Searcher',
  data: function() {
    return {
      searchText: '',
      operadoras:{}
    }
  },
  watch: {
    searchText: function() {
        this.debounceSearchOperadoras()
    }
  },
  created: function () {
    this.debounceSearchOperadoras = debounce(this.searchOperadoras, 500 )
  },
  methods: {
    searchOperadoras: function() {
      if(this.searchText === '') {
        this.operadoras = {}
        return;
      }

      axios.get('http://localhost:3000/search', {
        params: {
          text: this.searchText
        }
      }).then((response) => {
          this.operadoras = response.data
        }).catch((response) => {
          console.log(response)
        })
    }
  }

}
</script>

<style>
input {
  height: 2.3em;
  font-size: 20px;
  color: #6c6c6c;
  padding-left: 20px;
  border:1px solid #6c6c6c;
  outline: none;
}
input:focus {
  border:1px solid #2450b7;
}
.container {
  height: 100%;
  width: 75%;
  margin: auto;
  padding-top:20px;
}
h1 {
  margin: 0;
}
ul {
  list-style: none;
}
ul li {
  border: 1px solid #ccc;
  padding: 10px 0 2px;
}
</style>




