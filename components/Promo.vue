<template>

  <div class="promo">

    <h1 class="name">INFINITY</h1>

    <AuthImage/>

  </div>

</template>

<script lang="ts">
import AuthImage from "@/assets/img/authorization.svg";
import {Component, Vue} from "vue-property-decorator";

@Component({
  components: {
    AuthImage
  }
})
export default class Promo extends Vue {

}

</script>

<style lang="scss">
@import "@/assets/variables.scss";

  .promo {
    text-align: center;
    font-size: 64px;
  }

  .name {
    color: $primary-color;
  }
</style>
