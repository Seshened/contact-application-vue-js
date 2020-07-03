<template>
  <div class='ui basic content center aligned segment'>
    <button class='ui basic button icon' v-on:click="openForm" v-show="!isCreating">
      <i class='plus icon'></i>
    </button>
    <div class='ui centered card' v-show="isCreating">
      <div class='content'>
        <div class='ui form'>
          <div class='field'>
            <label>Имя</label>
            <input v-model="nameText" type='text'>
          </div>
          <div class='field'>
            <label>Фамилия</label>
            <input v-model="surnameText" type='text'>
          </div>
          <div class='field'>
            <label>Email</label>
            <input v-model="emailText" type='text'>
          </div>
          <div class='field'>
            <label>Номер телефона</label>
            <input v-model="numberText" type='text'>
          </div>
          <div class='field'>
            <label>Адрес</label>
            <input v-model="addressText" type='text'>
          </div>
          <div class='ui two button attached buttons'>
            <button class='ui basic blue button' v-on:click="sendForm()">
              Создать
            </button>
            <button class='ui basic red button' v-on:click="closeForm">
              Отмена
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        nameText: '',
        surnameText: '',
        emailText: '',
        numberText: '',
        addressText: '',
        isCreating: false,
      };
    },
    methods: {
      openForm() {
        this.isCreating = true;
      },
      closeForm() {
        this.isCreating = false;
      },
      sendForm() {
        if (this.nameText.length > 0 && this.surnameText.length > 0
          && this.numberText.length > 0 && this.addressText.length > 0) {
          const name = this.nameText;
          const surname = this.surnameText;
          const email = this.emailText;
          const number = this.numberText;
          const address = this.addressText;
          this.$emit('create-contact', {
            name,
            surname,
            email,
            number,
            address,
          });
          this.nameText = '';
          this.surnameText = '';
          this.emailText = '';
          this.numberText = '';
          this.addressText = '';
          this.isCreating = false;
        }
      },
    },
  };
</script>
