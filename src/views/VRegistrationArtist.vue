<template>
  <div class="v-registration-artist container-narrow">
    <base-block class="v-registration-artist__block">
      <h1 class="v-registration-artist__title typography-title">Регистрация</h1>
      <form class="v-registration-artist__form" @submit.prevent="register">
        <base-input
          id="login"
          label="Email или Логин"
          placeholder="email@gmail.com"
        />
        <base-input
          id="password"
          type="password"
          label="Пароль"
          placeholder="Введите пароль"
          icon="eye"
        />
        <base-button title="Зарегистрироваться" :primary="true" />
      </form>
      <base-social text="Или зарегистрироваться с помощью" />
    </base-block>
    <p class="v-registration-artist__account typography-text">
      Уже есть аккаунт?
      <router-link to="/login/artist" class="v-registration-artist__link"
        >Войти</router-link
      >
    </p>
  </div>
</template>

<script>
import BaseBlock from "@/components/base1/BaseBlock.vue";
import BaseInput from "@/components/base1/BaseInput.vue";
import BaseButton from "@/components/base1/BaseButton.vue";
import BaseSocial from "@/components/base1/BaseSocial.vue";

export default {
  name: "VLoginCurator",
  components: {
    BaseBlock,
    BaseInput,
    BaseButton,
    BaseSocial,
  },
  methods: {
    register() {
      this.$router.push("/login/accounts");
    },
  },
};
</script>

<style lang="sass" scoped>
.v-registration-artist
  margin-top: 95px
  margin-bottom: 123px
  +xs()
    margin-top: 23px
    margin-bottom: 23px

  &__title
    text-align: center
    margin-bottom: 40px


  &__form
    display: flex
    flex-direction: column
    gap: 30px
    margin-bottom: 30px


  &__account
    font-weight: 600
    text-align: center
    margin-top: 13px


  &__link
    color: $accent
    text-decoration: none
    font-weight: 600
    transition: 0.3s ease
    &:hover
      opacity: 0.9
</style>
