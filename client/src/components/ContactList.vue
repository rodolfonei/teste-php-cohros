<template>
  <div>
    <div>
      <h2 class="my-3">Lista de contatos</h2>
      <ul class="list-group" v-if="contacts && contacts.length">
        <li v-for="contact of contacts" v-bind:key="contact" class="list-group-item">
          <p><strong>Nome:</strong> {{contact.name}}</p>
          <p><strong>E-mail:</strong> {{contact.email}}</p>
          <p><strong>Endereço:</strong> {{contact.address}}</p>
          <p><strong>Telefone(s):</strong></p>
          <ul>
            <li v-for="phone_number of contact.phone_numbers" v-bind:key="phone_number">
              <p>{{phone_number}}</p>
            </li>
          </ul>

        </li>
      </ul>
    </div>

    <FormModal />
  </div>
</template>

<script>
import axios from 'axios';
import FormModal from '@/components/FormModal.vue'

export default {
  data() {
    return {
      contacts: []
    }
  },

  components: {
    FormModal
  },

  // Fetches posts when the component is created.
  created() {
    axios.get(`http://localhost/projeto-teste-php-cohros2/api/contact/read.php`)
    .then(response => {
      // JSON responses are automatically parsed.
      this.contacts = response.data.data
    })
    .catch(e => {
      this.contacts.push(e)
    })
  }
}

</script>
