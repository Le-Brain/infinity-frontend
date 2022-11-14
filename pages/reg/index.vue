<template>

  <div class="reg">

    <Promo/>
    <div class="reg__section">

      <InfinityLogo/>
      <div class="reg-form">

        <h2 class="reg__title">Регистрация</h2>
        <v-stepper v-model="e1">

          <v-stepper-header>

            <v-stepper-step
              step="1"
              color="#C7493A"
              :complete="e1 > 1"
            >
              Основная <small>информация</small>
            </v-stepper-step>

            <v-divider></v-divider>

            <v-stepper-step
              step="2"
              color="#C7493A"
              :complete="e1 > 2"
            >
              Контактные <small>данные</small>
            </v-stepper-step>

            <v-divider></v-divider>

            <v-stepper-step
              step="3"
              color="#C7493A"
            >
              Завершение
            </v-stepper-step>

          </v-stepper-header>

          <v-stepper-items>

            <v-stepper-content step="1">

              <v-card>

                <h3 class="reg__form-title">ДАННЫЕ ДЛЯ РЕГИСТРАЦИИ</h3>
                <v-form v-model="valid">

                  <v-text-field
                    v-model="login"
                    :rules="loginRules"
                    counter
                    label="Login"
                    hint="Введите ваш логин"
                    persistent-hint
                    required
                  ></v-text-field>

                  <v-text-field
                    v-model="password"
                    :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                    :rules="[rules.required, rules.min]"
                    :type="show1 ? 'text' : 'password'"
                    name="password"
                    hint="Введите пароль"
                    persistent-hint
                    counter
                    @click:append="show1 = !show1"
                  ></v-text-field>

                  <v-text-field
                    v-model="email"
                    :rules="emailRules"
                    counter
                    label="Email"
                    hint="Введите ваш email"
                    persistent-hint
                    required
                  ></v-text-field>

                  <v-text-field
                    v-model="password"
                    :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                    :rules="[rules.required, rules.min]"
                    :type="show1 ? 'text' : 'password'"
                    name="rpassword"
                    hint="Повторите ввод пароля"
                    persistent-hint
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

              <v-card>

                <h3 class="reg__form-title">ДАННЫЕ ДЛЯ РЕГИСТРАЦИИ</h3>
                <v-form v-model="valid">

                  <v-text-field
                    v-model="firstname"
                    :rules="nameRules"
                    counter=""
                    label="Имя"
                    required
                    hint="Введите ваше имя"
                    persistent-hint
                  ></v-text-field>

                  <v-autocomplete
                    v-model="country"
                    :items="countries"
                    :filter="customFilter"
                    color="white"
                    item-text="name"
                    hint="Введите страну"
                    persistent-hint
                  ></v-autocomplete>

                  <v-text-field
                    v-model="lastname"
                    :rules="nameRules"
                    counter=""
                    label="Фамилия"
                    required
                    hint="Введите вашу фамилию"
                    persistent-hint
                  ></v-text-field>

                  <v-text-field
                    v-model="phoneNumber"
                    :counter="7"
                    :rules="phoneRules"
                    hint="Введите номер телефона"
                    persistent-hint
                    required
                    type="tel"
                    mask="+# (###) ###-##-##"
                    masked="true"
                  ></v-text-field>

                  <div class="reg__form-radio">

                    <v-radio-group
                      v-model="radios"
                      row
                      mandatory
                      label="Ваш пол"
                    >
                      <div></div>
                      <v-radio
                        label="Мужской"
                        value="man"
                        color="#C7493A"
                      ></v-radio>

                      <v-radio
                        label="Женский"
                        value="women"
                        color="#C7493A"
                      ></v-radio>
                    </v-radio-group>

                  </div>

                </v-form>

              </v-card>

              <div class="reg__optional">
                <v-btn
                  color="#FFF"
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
                  color="#C7493A"
                  @click="e1 = 3"
                >
                  Следующий шаг
                </v-btn>
              </div>

            </v-stepper-content>

            <v-stepper-content step="3">
              <v-card
                class="mb-n12"
                color="110F0F"
                height="561px"
              >
                <h3 class="reg__form-title">ДАННЫЕ ДЛЯ РЕГИСТРАЦИИ</h3>
              </v-card>

              <div class="reg__optional">
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
                  color="#C7493A"
                  @click="e1 = 1"
                >
                  Завершить
                </v-btn>
              </div>

            </v-stepper-content>
          </v-stepper-items>
        </v-stepper>

      </div>
    </div>
  </div>
</template>

<script lang="ts">
import InfinityLogo from "@/assets/img/logo.svg";
import {mask} from 'vue-the-mask';

export default {
  name: 'RegPage',
  components: {
    InfinityLogo
  },
  directives: {
    mask
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
      e1: 1,
      hasSaved: false,
      countries: [
        { name: 'Россия', abbr: 'RU', id: 1 },
        { name: 'Казахстан', abbr: 'KZ', id: 2 },
        { name: 'Турция', abbr: 'TUR', id: 3 },
        { name: 'Таджикистан', abbr: 'TJK', id: 4 },
        { name: 'Узбекистан', abbr: 'UZB', id: 5 },
      ],
      country: 'Россия',
      phoneNumber: '',
    }
  },
  methods: {
    customFilter (item, queryText, itemText) {
      const textOne = item.name.toLowerCase()
      const textTwo = item.abbr.toLowerCase()
      const searchText = queryText.toLowerCase()

      return textOne.indexOf(searchText) > -1 ||
        textTwo.indexOf(searchText) > -1
    }
  },
}
</script>

<style lang="scss">
@import "@/assets/variables.scss";

.reg {
  display: flex;
  justify-content: center;
  background-color: $bg-color;
  margin-top: 30px;
}

.reg__section {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 30px 0 0 100px;
}

.reg-form {
  width: 952px;
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

.reg__form-radio .v-input--radio-group legend.v-label {
  font-size: 16px;
}

.reg__form-radio .v-input--radio-group__input {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}

.reg__form-radio .v-input--selection-controls {
  margin-top: -26px;
}

.reg__optional {
  position: absolute;
  bottom: 14%;
  right: 19%;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 230px;
}

.reg-form .v-form {
  display: grid;
  grid-template-columns: 1fr 1fr;
  padding: 55px 89px 126px 89px;
  gap: 60px;
  justify-items: center;
}

.reg-form .v-form > div {
  width: 299px;
}

.reg-form .v-stepper__header {
  border-bottom: 2px solid rgba(17, 15, 15, 0.15);
  height: 92px;
}

.reg-form .v-stepper__items {
  height: 561px;
}

.reg-form .v-stepper, .theme--dark.v-card {
  background-color: #110F0F;
}

.reg-form .theme--dark.v-stepper .v-stepper__header .v-divider {
  border-color: rgba(255, 255, 255, 0.6);
  margin: 0 5px 0 5px;
}

.reg-form .v-stepper__wrapper {
  display: flex;
  flex-direction: column;
}

.reg-form .v-stepper__content {
  padding: 0;
  transform: none;
  transition: none;
}

.reg-form .theme--dark.v-btn.v-btn--outlined.v-btn--text {
  border-color: rgba(255, 255, 255, 1);
}

.reg-form .v-text-field {
  padding-top: 0;
  margin-top: 0;
}
</style>

