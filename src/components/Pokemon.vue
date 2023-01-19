<template>
  <v-container>
    <v-card class="mx-auto" max-width="344">
      <v-img
        :src="datos.sprites.other.home.front_default"
      ></v-img>
      <v-card-title>{{ datos.name }}</v-card-title>
    </v-card>
  </v-container>
</template>

<script>
import axios from 'axios';
export default {
  name: "pokemon",
  props: {
    pokemonItem: Object
  },
  data: () => ({
    datos: {}
  }),
  mounted() {
    axios.get(this.pokemonItem.url).then((res) => {
      this.datos = res.data
      console.log(this.datos)
    })
  }
};
</script>
