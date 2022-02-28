<template>
  <v-container>
    <!-- <v-layout> -->
    <h1 class="display-1 text-center">Weather App</h1>
    <v-flex xs-12>
      <v-card color="blue-grey darken-2" dark>
        <v-card-text> Here is the Card </v-card-text>
      </v-card>
    </v-flex>
    <v-flex xs12 class="mt-4">
      <v-text-field label="Enter City Name" solo></v-text-field>
    </v-flex>
    <!-- </v-layout> -->
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      city: 'Sleman',
    }
  },
  created() {
    this.$axios
      .$get(
        'https://api.openweathermap.org/data/2.5/weather?q=' +
          this.city +
          '&appid=802117a63302fe5e07e0ab333218090d'
      )
      .then((res) => console.log(res))
  },
}
</script>
