<template>
  <div class="contain pt-5">
    <h2 class="text-center font-weight-bold"> Random Pickup Lines 😉</h2>
    <div class="container d-flex flex-column">
      <div class="container h-100 pt-5 d-flex flex-column justify-content-center align-items-center">
        <b-spinner variant="success" class="m-3" v-if="loading" label="Spinning"></b-spinner>
        <h2 class="bold text-center">{{joke}}</h2>
      </div>
      <b-button class="mx-auto mt-5" variant="success" v-on:click="postJoke">another one</b-button>
    </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'jokes',
  data() {
    return {
      joke: '',
      user: '',
      loading: false
    }
  },
  methods: {
    async postJoke(){
      this.loading = true;
      
      try {
            const res = await axios.get('https://vinuxd.vercel.app/api/pickup');
            const presentJoke = res.data.pickup;
            this.joke = presentJoke;
          } catch (error) {
              console.log(error.message);
          } 
        }
  },
  created(){
    this.postJoke();
  }
  
}
</script>

<style scoped>
  .contain{
    background-color: darkslategrey;
    color: #fff;
    height: 100vh;
    width: 100%;
  }
  .container > h2 {
    max-width: 500px;
  }
  .spinner-border{
    width: 20px;
    height: 20px;
   color: #fff;
  }
</style>
