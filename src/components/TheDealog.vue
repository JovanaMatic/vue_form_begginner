<template>
  <div class="main-dialog" @click.self="closeDialog">
    <dialog open>
      <h3>These are the information you provided</h3>
      <p>Name: {{ name }}</p>
      <p>Company: {{ companyName }}</p>
      <p>title: {{ title }}</p>
      <p>department: {{ department }}</p>
      <p>radioButtons: {{ radioButtons }}</p>
      <p>phoneText: {{ phoneText }}</p>
      <p>emailText: {{ emailText }}</p>
      <p>address: {{ address }}</p>
      <p>address_2: {{ address_2 }}</p>
      <p>city: {{ city }}</p>
      <p>state: {{ state }}</p>
      <p>zip: {{ zip }}</p>
      <p>additionalInfo: {{ additionalInfo }}</p>
      <base-button @click="closeDialog">Okey!</base-button>
    </dialog>
  </div>
</template>

<script>
  export default {
    props: ['name', 'companyName', 'title', 'department', 'radioButtons', 'phoneText', 'emailText', 'address', 'address_2', 'city', 'state', 'zip', 'additionalInfo'],
    methods: {
      closeDialog() {
        this.$emit('close-dialog')
      }
    }
  }
</script>
<style scoped>

.main-dialog {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.437);
}

dialog {
  margin-top: 30px;
}

</style>