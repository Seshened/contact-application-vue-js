<template>
  <div>
    <p class="contacts">Контактов: {{contacts.length}}</p>
    <contact v-on:delete-contact="deleteContact" v-for="contact in contacts" :contact.sync="contact"></contact>
  </div>
</template>

<script type = "text/javascript" >
import sweetalert from 'sweetalert';
import Contact from './Contact';

export default {
  props: ['contacts'],
  components: {
    Contact,
  },
  methods: {
    deleteContact(contact) {
      sweetalert({
        title: 'Вы уверены что хотите удалить контакт?',
        text: 'Этот контакт будет удален...',
        type: 'warning',
        showCancelButton: true,
        confirmButtonColor: '#DD6B55',
        confirmButtonText: 'Да, удалить!',
        cancelButtonText: 'Отмена',
        closeOnConfirm: false,
      },
      () => {
        const contactIndex = this.contacts.indexOf(contact);
        this.contacts.splice(contactIndex, 1);
        sweetalert('Удалено!', 'Ваш контакт был удален.', 'success');
      });
    },
  },
};
</script>

<style scoped>
p.contacts {
  text-align: center;
}
</style>

