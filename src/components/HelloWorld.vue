<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    
    <button class="outline-primary" v-on:click="recupJson">Recup JSON</button>
    <p>{{ json }}</p>

  </div>
</template>

<script>

const axios = require('axios');

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return{
      json: ''
    }
  },
  methods: {
    recupJson() {
      //axios.get('LPTLWTM.json') --> fonctionne car LPTLWTM.json dans le dossier public
      axios.get('http://pokeapi.co/api/v2/pokemon/ditto/') //--> fonctionne
      //axios.get('http://voca2.univ-poitiers.fr/~subrenat/toto.html') //--> Error: Network error
      //axios.get('http://mchabaud.projet.sfasp2mi.univ-poitiers.fr/gs-jury-gestion/back-end/web/app_dev.php/etudiantsLPTLWTM') // --> Error: Network error
      .then( (res) => {
        //window.alert(res)
        this.json = res;
      })
      .catch(function (error) {
        window.alert(error + " " + error.response)
      });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
</style>
