<template>
  <div class="header">
    <InfinityLogo/>
    <v-container
      id="input"
    >
      <v-text-field
        color="#FFF"
        outlined
        persistent-placeholder
        placeholder="Поиск"
        append-icon="mdi-magnify"
      ></v-text-field>
    </v-container>
  </div>
</template>

<script lang="ts">
import InfinityLogo from "@/assets/img/logo.svg";

export default {
  name: 'InHeader',
  components: {
    InfinityLogo,
  }
}
</script>

<style lang="scss">
@import "@/assets/variables.scss";

#input {
  width: 265px;
}

</style>
