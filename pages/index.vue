<template>
  <form>
    <h1>Роги и копыта</h1>
    <v-subheader class="pl-0 mb-3">Анкета нового сотрудника</v-subheader>

    <v-text-field
            v-model="name"
            label="Ваше полное ФИО"
            v-validate="'required'"
            :error-messages="errors.collect('name')"
            data-vv-name="name"
            required
    ></v-text-field>

    <v-select
            v-model="sex"
            :items="['Мужской', 'Женский']"
            label="Пол"
            v-validate="'required'"
            :error-messages="errors.collect('sex')"
            data-vv-name="sex"
            required
    ></v-select>

    <date-input
            v-model="birthday"
            label="День рождения"
            v-validate="'required'"
            :error-messages="errors.collect('birthday')"
            data-vv-name="birthday"
    ></date-input>

    <file-input
        v-model="photo"
        label="Фотография"
    ></file-input>

    <v-text-field
            v-model="phone"
            label="Телефон"
            v-validate="'required'"
            :error-messages="errors.collect('phone')"
            data-vv-name="phone"
            required
    ></v-text-field>

    <v-text-field
            v-model="email"
            v-validate="'required|email'"
            :error-messages="errors.collect('email')"
            data-vv-name="email"
            label="E-mail"
            required
    ></v-text-field>

    <v-textarea v-model="interests" label="Ваши интересы"></v-textarea>

    <v-textarea v-model="why" label="Почему вы хотите работать в компании РиК"></v-textarea>

    <v-btn class="ma-0" color="primary" @click="submit">Отправить</v-btn>
  </form>
</template>

<script>
  import DateInput from "../components/DateInput";
  import FileInput from "../components/FileInput";
  export default {
    components: {FileInput, DateInput},
    data: () => ({
      name: null,
      sex: null,
      phone: null,
      why: null,
      interests: null,
      birthday: null,
      email: null,
      photo: null,
    }),

    head: () => ({
      title: 'Анкета нового сотрудника',
    }),

    methods: {
      submit() {
        this.$validator.validateAll().then(result => {

        })
      },
    }
  }
</script>
