<template>
  <v-app dark>
    <AppHeader/>
    <nuxt />
  </v-app>
</template>

<script>
import AppHeader from "~/components/header/AppHeader";
export default {
  name: 'DefaultLayout',
  components: {
    AppHeader
  },
}
</script>
