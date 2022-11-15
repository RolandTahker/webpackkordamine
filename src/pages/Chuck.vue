<template>
  <h2>{{joke}}</h2>
</template>

<script>
import axios from 'axios';
export default {
    created(){
        axios.get('https://api.chucknorris.io/jokes/random').then(res => {
            console.log(res.data.value);
            this.joke = res.data.value;
        });
    }, 
    data(){
        return {
            joke: ''
        }
    }
}
</script>

<style>
h2 {
    text-align: center;
    color: rgba(219, 214, 214, 0.808);
    font-family: sans-serif;
    font-size: 15pt;
}


</style>
