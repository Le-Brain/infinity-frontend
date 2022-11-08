<template>
  <div class="log">
    <Promo/>
    <div class="log__section">
      <InfinityLogo/>
      <div class="login-form">
        <h2 class="log__title">Авторизация</h2>
        <v-form v-model="valid">
          <v-text-field
            v-model="email"
            :rules="emailRules"
            :counter="10"
            label="Логин / Email"
            hint="Введите ваш логин или email"
            required
          ></v-text-field>
          <v-text-field
            v-model="password"
            :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
            :rules="[rules.required, rules.min]"
            :type="show1 ? 'text' : 'password'"
            name="password"
            label=""
            hint="Введите пароль"
            counter
            @click:append="show1 = !show1"
          ></v-text-field>
          <div class="log__options">
            <v-switch
              v-model="ex11"
              label="Запомнить меня"
              color="#C7493A"
              value=""
              dense
              hide-details
            ></v-switch>
            <v-btn
              class="btn"
              height="40"
              color="#C7493A"
              outlined
            >Войти</v-btn>
          </div>
          <p class="log__footnote">Нет аккаунта Infinity? <a style="color: #C7493A" href="/reg">Зарегистрировать аккаунт</a></p>
        </v-form>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
  export default {
    name: 'IndexPage',
    data () {
      return {
        show1: false,
        show2: true,
        show3: false,
        show4: false,
        password: '------------',
        rules: {
          required: value => !!value || 'Required.',
          min: v => v.length >= 8 || 'Min 8 characters',
          emailMatch: () => (`The email and password you entered don't match`),
        },
        ex11: ['red', 'indigo', 'orange', 'primary', 'secondary', 'success', 'info', 'warning', 'error', 'red darken-3', 'indigo darken-3', 'orange darken-3'],
      }
    }
  }
</script>

<style lang="scss">
  @import "./assets/variables.scss";

  .log {
    display: flex;
    background-color: $bg-color;
    margin-top: 30px;
  }

  .log__section {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 35px;
  }

  .log__options {
    display: flex;
    align-items: baseline;
    justify-content: space-between;
  }

  .login-form {
    max-width: 759px;
    max-height: 716px;
    background: #110F0F;
    border-bottom: 10px solid $primary-color;
    padding: 50px 155px 80px 155px;
    margin-top: 90px;
  }

  .log__title {
    text-align: center;
    font-size: 64px;
    margin-bottom: 45px;
  }

  // ==================================== Стили form =======================================
  .v-form {
    background-color: #110F0F;
    width: 448px;
    margin: auto;
  }

  .v-form > div:not(:last-child) {
    margin-bottom: 55px;
  }

  // ==================================== Стили switch =======================================
  .v-input--switch.v-input--dense .v-input--switch__track {
    height: 21px;
    width: 60px;
    border-radius: 10px
  }

  .v-input--switch.v-input--dense .v-input--switch__thumb {
    width: 21px;
    height: 21px;
  }

  .v-input--switch__track {
    top: calc(50% - 10px);
  }

  .v-application--is-ltr .v-input--switch.v-input--is-dirty .v-input--selection-controls__ripple, .v-application--is-ltr .v-input--switch.v-input--is-dirty .v-input--switch__thumb {
    transform: translate(45px, 0);
  }

  .v-input--switch .v-input--selection-controls__input {
    width: 64px;
    margin-right: 12px;
  }

  .log__options .v-label {
    font-size: 24px;
  }
// ===========================================================================================
</style>
