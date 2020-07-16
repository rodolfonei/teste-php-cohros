<template>
  <div class="modal fade" id="formModal" data-backdrop="static" data-keyboard="false" tabindex="-1" role="dialog" aria-labelledby="formModalLabel" aria-hidden="true">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="formModalLabel">Adicionar contato</h5>
          <button type="button" class="close" data-dismiss="modal" aria-label="Close">
            <span aria-hidden="true">&times;</span>
          </button>
        </div>
        <div class="modal-body">

          <form>

            <div class="form-group">
              <label for="nomeInput">Nome</label>
              <input type="text" class="form-control" name="name" id="nameInput" v-model="newContact.name" required>
            </div>

            <div class="form-group">
              <label for="emailInput">E-mail</label>
              <input type="email" class="form-control" name="email" id="emailInput" v-model="newContact.email" required>
            </div>

            <div class="form-group">
              <label for="addressInput">Endereço</label>
              <input type="text" class="form-control" name="address" id="addressInput" v-model="newContact.address" required>
            </div>

          </form>

        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-danger" data-dismiss="modal">Cancelar</button>
          <button @click="createContact()" type="submit" class="btn btn-success">Adicionar</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {

  data() {
    return {
      newContact: {'name': '', 'email': '', 'address': ''}
    }
  },

  methods: {
    // Get the form input data and send as POST
    createContact() {
      var _this = this
      var input = this.newContact
      axios.post(`http://localhost/projeto-teste-php-cohros2/api/contact/create.php`, input).then(function (response) {
        _this.newContact = { 'name': '' };
        console.log(response);
        console.log(this.formModal);
        document.querySelector('#formModal').formModal.modal('hide');
      });
    }
  }

}

</script>
