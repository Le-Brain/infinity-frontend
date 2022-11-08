<template>
  <div class="promo">
    <h1 class="name">INFINITY</h1>
      <MainImage
        :maxWidth="681"
        :maxHeight="836"
      />
  </div>
</template>

<script lang="ts">

import {Component, Prop, Vue} from "vue-property-decorator";

@Component
export default class Promo extends Vue{

}
</script>

<style lang="scss">
  .promo {
    text-align: center;
    font-size: 64px;
  }
</style>
