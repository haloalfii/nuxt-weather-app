<template>
  <v-container>
    <!-- <v-layout> -->
    <h1 class="display-1 text-center">Weather App</h1>
    <v-flex xs-12 class="mt-4">
      <v-card color="blue-grey darken-2" dark>
        <v-card-text>
          <v-layout justify-center>
            <v-flex class="text-center" v-if="weather.main">
              <h4>Tempetarue</h4>
              <h1 class="display-1">{{ weather.name }}</h1>
              <img :src="icon" alt="" />
              <p>
                <span class="display-1">{{ temp() }} &#176;C</span>
              </p>
              <p>
                <span class="display-1">{{
                  weather.weather[0].description
                }}</span>
              </p>
            </v-flex>

            <v-flex class="text-center" v-if="weather.main">
              <h4>Wind & Pressure</h4>
              <h3 class="headline">
                Wind : {{ weather.wind.speed }} m/s ({{ weather.wind.deg }}
                &deg;)
              </h3>
              <h3 class="headline mt-2">
                Humidity : {{ weather.main.humidity }}%
              </h3>
              <h3 class="headline mt-2">
                Pressure : {{ weather.main.pressure }} pH
              </h3>
            </v-flex>

            <v-flex class="text-center" v-if="weather.main">
              <h4>Max and Min Temp</h4>
              <h3 class="headline">Max : {{ max_temp() }} &#176;C</h3>
              <h3 class="headline mt-2">Min : {{ min_temp() }} &#176;C</h3>
            </v-flex>
          </v-layout>
        </v-card-text>
      </v-card>
    </v-flex>
    <v-flex xs12 class="mt-4">
      <v-form @submit.prevent="getWeatherInfo">
        <v-text-field
          label="Enter City Name"
          solo
          v-model="city"
        ></v-text-field>
      </v-form>
    </v-flex>
    <!-- </v-layout> -->
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      city: 'London',
      weather: {},
    }
  },
  created() {
    this.getWeatherInfo()
  },
  computed: {
    icon() {
      return this.weather.weather
        ? 'https://openweathermap.org/img/w/' +
            this.weather.weather[0].icon +
            '.png'
        : ''
    },
  },
  methods: {
    getWeatherInfo() {
      this.$axios
        .$get(
          'https://api.openweathermap.org/data/2.5/weather?q=' +
            this.city +
            '&appid=802117a63302fe5e07e0ab333218090d'
        )
        .then((res) => (this.weather = res))
    },
    temp() {
      return this.weather.main ? Math.round(this.weather.main.temp - 273) : ''
    },
    max_temp() {
      return this.weather.main
        ? Math.round(this.weather.main.temp_max - 273)
        : ''
    },
    min_temp() {
      return this.weather.main
        ? Math.round(this.weather.main.temp_min - 273)
        : ''
    },
  },
}
</script>
