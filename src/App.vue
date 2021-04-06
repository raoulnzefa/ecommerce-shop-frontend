<template>
  <div id="app">
    <v-app id="inspire">
      <Navbar />

      <v-main>
        <router-view></router-view>
      </v-main>
    </v-app>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar"

export default {
  name: 'App',

  components: {
    Navbar,
  },

  data: () => ({
    items: [
      { title: 'Home', icon: 'mdi-view-dashboard', router: "/" },
      { title: 'Cart', icon: 'mdi-cart', router: "/cart" },
      { title: 'About', icon: 'mdi-information', router: "/about" },
    ],
    right: null,
    products: undefined,
    drawer: null
  }),
};
</script>
