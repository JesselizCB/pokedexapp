<template>
  <v-container>
    <v-row>
      <v-col cols="2">
        <v-btn icon @click="$router.back()">
          <v-icon>mdi-arrow-left</v-icon>
        </v-btn>
      </v-col>
      <v-col cols="10" class="text-center">
        <h1 class="text-capitalize">
          {{ pokeItem.name }} n.ª {{ pokeItem.order }}
        </h1>
      </v-col>
    </v-row>
    <v-divider class="ma-6"></v-divider>
    <v-row class="text-center pt-4">
      <v-col cols="12" lg="6" md="4" sm="6">
        <v-card class="mx-auto grey lighten-4" max-width="454">
          <v-img :src="officialArtwork"></v-img>
        </v-card>
      </v-col>
      <v-col cols="12" lg="6" md="4" sm="6">
        <v-row class="justify-center mt-2">
          <p class="font-weight-black text-h5">Tipos:</p>
          <div v-for="item in pokeItem.types" :key="item.types">
            <v-chip class="ma-2" label text-color="white" :color="getColor(item.type.name)"> {{item.type.name}} </v-chip>
          </div>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>
<script>
export default {
  data() {
    return {
      pokeItem: this.$route.params.pokemon,
    };
  },
  computed: {
    officialArtwork() {
      return this.pokeItem.sprites.other["official-artwork"].front_default;
    },
  },
  methods: {
    getColor(color) {
      const typeColor = {
        grass: "light-green",
        poison: "deep-purple lighten-3",
        water: "blue",
        fire: "orange",
        flying: "light-blue",
        bug: "lime",
        normal: "pink"
      };
      const defaultColor = 'gray'
      const finalColor = typeColor[color] || defaultColor
      return finalColor
    }
  },
  mounted() {
    console.log("pokeData desde about", this.$route.params.pokemon);
  },
};
</script>
