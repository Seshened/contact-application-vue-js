<template>
  <div class='ui centered card'>
    <div class="content" v-show="!isEditing">
      <div class='header'>
          {{ contact.name }}
      </div>
      <div class='header'>
          {{ contact.surname }}
      </div>
      <div class='meta'>
          {{ contact.email }}
      </div>
      <div class='meta'>
          {{ contact.number }}
      </div>
      <div class='meta'>
          {{ contact.address }}
      </div>
      <div class='extra content'>
          <span class='right floated edit icon' v-on:click="showForm">
          <i class='edit icon'></i>
        </span>
        <span class='right floated trash icon' v-on:click="deleteContact(contact)">
          <i class='trash icon'></i>
        </span>
      </div>
    </div>
    <div class="content" v-show="isEditing">
      <div class='ui form'>
        <div class='field'>
          <label>Имя</label>
          <input type='text' v-model="contact.name" >
        </div>
        <div class='field'>
          <label>Фамилия</label>
          <input type='text' v-model="contact.surname" >
        </div>
        <div class='field'>
          <label>Email</label>
          <input type='text' v-model="contact.email" >
        </div>
        <div class='field'>
          <label>Номер телефона</label>
          <input type='text' v-model="contact.number" >
        </div>
        <div class='field'>
          <label>Адрес</label>
          <input type='text' v-model="contact.address" >
        </div>
        <div class='ui two button attached buttons'>
          <button class='ui basic blue button' v-on:click="hideForm">
            Закрыть X
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script type="text/javascript">
  export default {
    props: ['contact'],
    data() {
      return {
        isEditing: false,
      };
    },
    methods: {
      deleteContact(contact) {
        this.$emit('delete-contact', contact);
      },
      showForm() {
        this.isEditing = true;
      },
      hideForm() {
        this.isEditing = false;
      },
    },
  };
</script>
