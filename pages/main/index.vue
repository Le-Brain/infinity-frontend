<template>

  <div class="main">

    <div class="main__title">
      <InfinityLogo :maxWidth="200"/>
      <h2 class="main__text"><span class="main__text-color">Вас приветствует</span> INFINITY</h2>
    </div>

    <MainImage
      :maxWidth="878"
      :maxHeight="699"
    />

    <div class="main__log">
        <v-btn
          class="btn"
          height="40"
          color="#FFFFFF"
          outlined
          to="/log" nuxt
        >Войти</v-btn>
        <v-btn
          class="btn"
          height="40"
          color="#C7493A"
          outlined
        >Регистрация</v-btn>
    </div>

    <PrimaryLine/>

  </div>
</template>

<script lang="ts">
  import PrimaryLine from "@/assets/img/line.svg"
  export default {
    name: 'IndexPage',
    components: {
      PrimaryLine
    }
  }
</script>

<style lang="scss">
  @import "@/assets/variables.scss";

  .main {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .main__title {
    text-align: center;
  }

  .main__text {
    color: $primary-color;
    font-weight: 700;
    font-size: 64px;
    line-height: 96px;
  }

  .main__text-color {
    color: #E0C3C3;
  }

  .main__log {
    margin-bottom: 62px;
  }

  .btn {
    font-size: 24px;
    width: 200px;
  }

  .btn:last-child {
    margin-left: 38px;
  }

</style>
