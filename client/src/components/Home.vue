<template>
  <div>
    <h1 class="my-5">Agenda de contatos</h1>
    <button data-toggle="modal" data-target="#formModal" class="btn btn-primary">Adicionar Contato</button>
    <ContactList />
  </div>
</template>

<script>

import ContactList from '@/components/ContactList.vue'

export default {
    components: {
      ContactList
    }
  }

</script>
