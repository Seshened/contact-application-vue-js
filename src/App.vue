<template>
  <div id="app">
    <h1 class="title">
      Contacts App
    </h1>

    <div class='columns'>
      <div class='column'>
        <contact-list v-bind:contacts="contacts"></contact-list>
        <create-contact v-on:create-contact="createContact"></create-contact>
      </div>
    </div>
  </div>
</template>

<script>
  import sweetalert from 'sweetalert';
  import ContactList from './components/ContactList';
  import CreateContact from './components/CreateContact';

  export default {
    name: 'app',
    components: {
      ContactList,
      CreateContact,
    },
    data() {
      return {
        contacts: [{
          name: 'Владимир',
          surname: 'Иванов',
          email: 'vivanov@mail.ru, ivanovmail@gmail.com',
          number: '+88005553535, +350858690, 8234123412134',
          address: 'Johnny street, Baker Street, Lincoln Avenue',
        }, {
          name: 'Бахром',
          surname: 'Гафуров',
          email: 'bgafurov@mail.ru, gafuroff.@gmail.com',
          number: '+123456677, +8895423452',
          address: 'Ahmed Donish street, Ortasaroy street',
        }, {
          name: 'Александр',
          surname: 'Владимиров',
          email: 'vladimirovalex@mail.ru, vlalex@.gmail.com',
          number: '+881245789789, +1237843789879',
          address: 'Novomoskovskaya street',
        }, {
          name: 'Джеймс',
          surname: 'Кинниган',
          email: 'jamesproperty@kinnigans.com, amodeus@gmail.com',
          number: '+123566573, +12369879698, +9988293923',
          address: 'Swyllow street, Matthew Garbish street, Valentin Ikof street',
        }],
      };
    },
    methods: {
      createContact(newContact) {
        this.contacts.push(newContact);
        sweetalert('Успешно!', 'Контакт создан!', 'success');
      },
    },
  };
</script>

<style>
  .app {

  }

  .title {
    padding-top: 1rem;
    text-align: center;
  }
</style>
