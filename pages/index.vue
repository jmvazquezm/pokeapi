<template>
  <div>
    <b-container>
      <b-row>
        <b-col cols='4' v-for='poke in pokes' :key='poke.name'>
          <b-card :title='poke.name'>

          </b-card>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'IndexPage',

  data(){
    return {
      pokes: [],
    }
  },
  asyncData(){
    return axios.get('https://pokeapi.co/api/v2/pokemon')
    .then((res) => {
      console.log(res.data.results);
      return{
        pokes: res.data.results,
      }
    })
    .catch((err) =>{
      console.log(err);
    })
  }
}
</script>
