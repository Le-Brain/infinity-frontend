<template>
  <div class="reg">
    <Promo/>
    <div class="reg__section">
      <InfinityLogo/>
      <div class="reg-form">
        <h2 class="reg__title">Регистрация</h2>
        <v-stepper
          v-model="e1"
        >
          <v-stepper-header>
            <v-stepper-step
              color="#C7493A"
              :complete="e1 > 1"
              step="1"
            >
              Основная <small>информация</small>
            </v-stepper-step>

            <v-divider></v-divider>

            <v-stepper-step
              color="#C7493A"
              :complete="e1 > 2"
              step="2"
            >
              Контактные <small>данные</small>
            </v-stepper-step>

            <v-divider></v-divider>

            <v-stepper-step
              color="#C7493A"
              step="3"
            >
              Завершение
            </v-stepper-step>
          </v-stepper-header>

          <v-stepper-items>
            <v-stepper-content step="1">
              <v-card
                class="mb-n12"
                color="110F0F"
                height="561px"
              >
                <h3 class="reg__form-title">ДАННЫЕ ДЛЯ РЕГИСТРАЦИИ</h3>
                <v-form v-model="valid">
                  <v-text-field
                    v-model="login"
                    :rules="loginRules"
                    counter
                    label="Login"
                    hint="Введите ваш логин"
                    required
                  ></v-text-field>
                  <v-text-field
                    v-model="password"
                    :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                    :rules="[rules.required, rules.min]"
                    :type="show1 ? 'text' : 'password'"
                    name="password"
                    hint="Введите пароль"
                    counter
                    @click:append="show1 = !show1"
                  ></v-text-field>
                  <v-text-field
                    v-model="email"
                    :rules="emailRules"
                    counter
                    label="Email"
                    hint="Введите ваш email"
                    required
                  ></v-text-field>
                  <v-text-field
                    v-model="password"
                    :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                    :rules="[rules.required, rules.min]"
                    :type="show1 ? 'text' : 'password'"
                    name="rpassword"
                    hint="Повторите ввод пароля"
                    counter
                    @click:append="show1 = !show1"
                  ></v-text-field>
                </v-form>
              </v-card>

              <div class="reg__optional">
                <v-btn
                  color="#FFF"
                  width="190"
                  height="52"
                  outlined
                  text
                  to="/main"
                >
                  Назад
                </v-btn>

                <v-btn
                  width="190"
                  height="52"
                  outlined
                  color="#C7493A"
                  @click="e1 = 2"
                >
                  Следующий шаг
                </v-btn>
              </div>
            </v-stepper-content>

            <v-stepper-content step="2">
              <v-card
                class="mb-n12"
                color="110F0F"
                height="561px"
              >
                <h3 class="reg__form-title">ДАННЫЕ ДЛЯ РЕГИСТРАЦИИ</h3>
              </v-card>

              <v-btn
                width="190"
                height="52"
                outlined
                text
                @click="e1 = 1"
              >
                Назад
              </v-btn>

              <v-btn
                width="190"
                height="52"
                outlined
                color="primary"
                @click="e1 = 3"
              >
                Следующий шаг
              </v-btn>
            </v-stepper-content>

            <v-stepper-content step="3">
              <v-card
                class="mb-n12"
                color="110F0F"
                height="561px"
              >
                <h3 class="reg__form-title">ДАННЫЕ ДЛЯ РЕГИСТРАЦИИ</h3>
              </v-card>

              <v-btn
                width="190"
                height="52"
                outlined
                text
                @click="e1 = 2"
              >
                Назад
              </v-btn>

              <v-btn
                width="190"
                height="52"
                outlined
                color="primary"
                @click="e1 = 1"
              >
                Завершить
              </v-btn>
            </v-stepper-content>
          </v-stepper-items>
        </v-stepper>

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
      password: 'Password',
      rules: {
        required: value => !!value || 'Required.',
        min: v => v.length >= 8 || 'Min 8 characters',
        emailMatch: () => (`The email and password you entered don't match`),
      },
      e1: 1,
    }
  }
}
</script>

<style lang="scss">
@import "./assets/variables.scss";

.reg {
  display: flex;
  background-color: $bg-color;
  margin-top: 30px;
}

.reg__section {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 30px;
}

.reg-form {
  width: 952px;
  height: 653px;
}

.reg__title, .reg__form-title {
  text-align: center;
}

.reg__title {
  font-size: 64px;
  padding: 50px 0 30px 0;
}

.reg__form-title {
  font-weight: 500;
  font-size: 20px;
  padding-top: 25px;
}

.reg__optional {
  position: absolute;
  bottom: 14%;
  right: 19%;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 230px;
}

.v-form {
  display: grid;
  grid-template-columns: 1fr 1fr;
  padding: 55px 89px 126px 89px;
  gap: 60px;
  justify-items: center;
}

.v-form > div {
  width: 299px;
}

.v-stepper__header {
  border-bottom: 2px solid rgba(17, 15, 15, 0.15);

}

.v-stepper__header, .theme--dark.v-card {
  background-color: #110F0F;
}

.theme--dark.v-stepper .v-stepper__header .v-divider {
  border-color: rgba(255, 255, 255, 0.6);
  margin: 0 5px 0 5px;
}

.v-stepper__wrapper {
  display: flex;
  flex-direction: column;
}

.v-stepper__content {
  padding: 0;
}

.theme--dark.v-btn.v-btn--outlined.v-btn--text {
  border-color: rgba(255, 255, 255, 1);
}
</style>

