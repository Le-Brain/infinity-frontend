<template>
    <img
      src="@/assets/img/logo.png"
      alt="Infinity Logo"
      :style="imageWidth"
    />
</template>

<script lang="ts">

import {Component, Prop, Vue} from "vue-property-decorator";

@Component
export default class InfinityLogo extends Vue{
  @Prop({type: Number, default: 300})
  readonly maxWidth!: number;

  get imageWidth () {
    return {
      maxWidth: `${this.maxWidth}px`,
    }
  }
}
</script>

<style lang="scss">

</style>
