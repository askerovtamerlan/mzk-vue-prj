<template>
  <div class="container-narrow v-reg-curator">
    <baseBlock class="v-reg-curator__block">
      <form class="v-reg-curator__form" @submit.prevent="reg">
        <h1 class="typography-title v-reg-curator__title">Регистрация</h1>
        <div class="v-reg-curator__radios">
          <baseRadio
            :title="radio.title"
            name="radiobuttons"
            v-for="(radio, index) in radiobuttons"
            :key="index"
            :id="radio.id"
          />
        </div>
        <div class="v-reg-curator__fields">
          <base-input
            id="email"
            label="Email"
            placeholder="email@gmail.com"
            v-model="email"
          />
          <base-input
            id="password"
            label="Пароль"
            :type="type"
            placeholder="Введите пароль"
            :icon="icon"
            @button-click="changeVisibility"
          />
          <base-file id="image" label="Фотография профиля" />
          <base-input
            id="name"
            label="Имя (логин)"
            placeholder="Введите имя или название"
          />
          <base-input
            id="description"
            label="Описание"
            placeholder="Расскажите о себе и что вы ищите"
            :textarea="true"
          />
        </div>
        <base-button title="Зарегистрироваться" :primary="true" />
      </form>
      <base-social text="Или зарегистрироваться с помощью" />
    </baseBlock>
    <p class="v-reg-curator__account typography-text">
      Уже есть аккаунт?
      <router-link to="/login/curator" class="v-reg-curator__link"
        >Войти</router-link
      >
    </p>
  </div>
</template>

<script>
import { ref } from "vue";
import BaseBlock from "@/components/base1/BaseBlock.vue";
import BaseRadio from "@/components/base1/BaseRadio.vue";
import BaseInput from "@/components/base1/BaseInput.vue";
import BaseFile from "@/components/base1/BaseFile.vue";
import BaseButton from "@/components/base1/BaseButton.vue";
import BaseSocial from "@/components/base1/BaseSocial.vue";

export default {
  components: {
    BaseBlock,
    BaseRadio,
    BaseInput,
    BaseFile,
    BaseButton,
    BaseSocial,
  },
  methods: {
    changeVisibility() {
      if (this.icon === "eye") {
        this.icon = "eye-closed";
        this.type = "text";
      } else {
        this.icon = "eye";
        this.type = "password";
      }
    },
    reg() {},
  },
  setup() {
    const picked = ref("");
    const email = ref("");
    const radiobuttons = [
      { id: "play", title: "Плейлист", value: "play" },
      { id: "rad", title: "Радио", value: "rad" },
      { id: "media", title: "Медиа", value: "media" },
      { id: "label", title: "Лейбл", value: "label" },
      { id: "bloger", title: "Блогер", value: "bloger" },
      { id: "producer", title: "Продюссер", value: "producer" },
    ];
    const type = ref("password");
    const icon = ref("eye");

    return { radiobuttons, email, type, icon, picked };
  },
};
</script>

<style lang="sass" scoped>
.v-reg-curator
  margin-top: 95px
  margin-bottom: 60px
  +xs()
    margin-top: 23px
    margin-bottom: 23px

  &__form
    margin-bottom: 35px


  &__title
    text-align: center
    margin-bottom: 30px


  &__radios
    display: grid
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr))
    column-gap: 30px
    row-gap: clamp(12px, 2%, 20px)
    margin-bottom: 30px


  &__fields
    display: flex
    flex-direction: column
    gap: 30px
    margin-bottom: 38px


  &__social
    width: 100%
    display: flex
    gap: 30px


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
