<template>
  <img
    src="@/assets/img/main.png"
    alt="Infinity main image"
    :style="{imageWidth, imageHeight}"
  />
</template>

<script lang="ts">

import {Component, Prop, Vue} from "vue-property-decorator";

@Component
export default class MainImage extends Vue{
  @Prop({type: Number, default: 300})
  readonly maxWidth!: number;
  readonly maxHeight!: number;

  get imageWidth () {
    return {
      maxWidth: `${this.maxWidth}px`,
    }
  }
  get imageHeight () {
    return {
      maxHeight: `${this.maxHeight}px`,
    }
  }
}
</script>

<style lang="scss">

</style>
