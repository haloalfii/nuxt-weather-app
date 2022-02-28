<template>
  <v-app>
    <v-content>
      <v-toolbar>
        <!-- <v-toolbar-side-icon></v-toolbar-side-icon> -->
        <v-toolbar-title
          ><nuxt-link to="/">Learning Nuxt</nuxt-link></v-toolbar-title
        >
        <v-spacer></v-spacer>
        <v-toolbar-items class="hidden-sm-and-down">
          <v-btn flat>
            <nuxt-link to="/weather-app">Weather App</nuxt-link></v-btn
          >
        </v-toolbar-items>
      </v-toolbar>

      <nuxt />
    </v-content>
  </v-app>
</template>

<script>
export default {
  head() {
    return {
      title: 'Weather App',
    }
  },
}
</script>

<style scoped>
a {
  text-decoration: none;
  color: white;
}
</style>
