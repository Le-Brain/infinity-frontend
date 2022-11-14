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
              height="64"
              width="155"
              color="#C7493A"
              outlined
            >Войти</v-btn>
          </div>
        </v-form>
        <p class="log__footnote">Нет аккаунта Infinity? <NuxtLink style="color: #C7493A" to="/reg">Зарегистрировать аккаунт</NuxtLink></p>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import InfinityLogo from "@/assets/img/logo.svg"

  export default {
    name: 'LogPage',
    components: {
      InfinityLogo
    },
    data () {
      return {
        show1: false,
        show2: true,
        show3: false,
        show4: false,
        password: 'Password',
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
  @import "@/assets/variables.scss";

  .log {
    width: 100%;
    display: flex;
    justify-content: center;
    background-color: $bg-color;
    margin-top: 30px;
  }

  .log__section {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 35px 0 0 200px;
  }

  .log__options {
    display: flex;
    align-items: baseline;
  }

  .log__options div {
    margin-right: 20px;
  }

  .login-form {
    max-width: 759px;
    max-height: 716px;
    background: #110F0F;
    border-bottom: 10px solid $primary-color;
    margin-top: 90px;
    padding: 50px 155px 80px 155px;
  }

  .log__title {
    text-align: center;
    font-size: 64px;
    margin-bottom: 45px;
  }

  .log__footnote {
    border-top: 1px solid rgba(255, 255, 255, 0.12);
    padding-top: 48px;
    margin-top: 40px;
  }

  .login-form p, a {
    margin-bottom: 0;
    text-decoration: none;
  }

  // ==================================== Стили form =======================================
  .login-form .v-form {
    background-color: #110F0F;
    margin: auto;
    width: 448px;
  }

  .login-form .v-form > div:nth-child(-n+2) {
    margin-bottom: 55px;
  }

  // ==================================== Стили switch =======================================
  .v-input--switch.v-input--dense .v-input--switch__track {
    height: 21px;
    width: 60px;
    border-radius: 10px
  }

  .v-application--is-ltr .v-input--switch.v-input--dense .v-input--selection-controls__ripple {
    left: -10.5px;
    top: -8.5px;
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
    font-size: 22px;
  }

  .log__options .v-btn__content {
    font-size: 24px;
  }
// ===========================================================================================
</style>
