<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <b-table hover :items="results" :busy.sync="isBusy"></b-table>


  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import axios from 'axios';

export default {

  name: 'home',
  data() {
    return {
      isBusy:  false,
      search: "",
      results: {}
    }
  },

  mounted(){
    this.getUser();
  },

  methods: {
    getUser() {
      axios
              .get("http://localhost:3000/users")
              .then(response => (this.results = response.data))
              .catch(error => alert(error));
    }
  },

  components: {
    HelloWorld
  }
}
</script>
