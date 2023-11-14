<template>
  <base-card v-if="formSubmited && !showDialog "><form-submited></form-submited></base-card>
  <div v-else>
     <header>
    <h1>My Form</h1>
  </header>
  <p v-if="showError" class="showError">All fields must be populated!</p>
  <form @submit.prevent="submitForm">
    <div class="col">
      <label for="clientName">
        <span>Client name</span>
        <em>*</em>
      </label>
      <input type="text" placeholder="Your name here...." :class="{ showErrorInput: this.showError }" v-model="name" @keyup="removeError($event)">
    </div>
    <div class="col">
      <label for="company">
        <span>Company</span>
        <em>*</em>
      </label>
      <input type="text" placeholder="Your company name here...." :class="{ showErrorInput: this.showError }" v-model="companyName" @keyup="removeError($event)">
    </div>
    <div class="col">
      <label for="title">
        <span>Title</span>
        <em>*</em>
      </label>
      <input type="text" placeholder="Your title here...." :class="{ showErrorInput: this.showError }" v-model="title" @keyup="removeError($event)">
    </div>
    <div class="col">
      <label for="department">
        <span>Department</span>
        <em>*</em>
      </label>
      <select name="department" v-model="department" :class="{ showErrorInput: this.showError }" @change="removeError($event)">
        <option value="frontend">Frontend</option>
        <option value="backedn">Backend</option>
        <option value="design">Design</option>
      </select>
    </div>
    <div class="col">
      <label for="contactMethod">
        <span ref="prefCont" :class="{ showError: this.showError }">Preferred contact method</span>
        <em>*</em>
      </label>
      <div class="col-1">
        <label for="email">Email</label>
        <input type="radio" id="email" name="contact" value="Email" v-model="radioButtons" @change="removeError($event)">

        <label for="phone">Phone</label>
        <input type="radio" id="phone" name="contact" value="Phone" v-model="radioButtons" @change="removeError($event)">
      </div>
    </div>
    <div class="col">
      <label for="email">
        <span>Email</span>
        <em>*</em>
      </label>
      <input type="text" placeholder="Your email here...." :class="{ showErrorInput: this.showError }" v-model="emailText" @keyup="removeError($event)">
    </div>
    <div class="col">
      <label for="phone">
        <span>Phone</span>
        <em>*</em>
      </label>
      <input type="text" placeholder="Your phone here...." :class="{ showErrorInput: this.showError }" v-model="phoneText" @keyup="removeError($event)">
    </div>
    <div class="col">
      <label for="companyAddress">
        <span>Company address</span>
        <em>*</em>
      </label>
      <input type="text" placeholder="Your address 1 here...." v-model="address">
      <label for="address_1">
        <span>Address</span>
      </label>
      <input type="text" placeholder="Your address 2 here...." v-model="address_2">
      <label for="address_2">
        <span>Address 2</span>
      </label>
      <input type="text" placeholder="Your city...." v-model="city">
      <label for="city">
        <span>City</span>
      </label>
      <input type="text" placeholder="Your state...." v-model="state">
      <label for="state">
        <span>State</span>
      </label>
      <input type="text" placeholder="Your zip...." v-model="zip">
      <label for="zip">
        <span>Zip</span>
      </label>
    </div>
    <div class="col">
      <label for="additionalInfo">
        <span>Additional information</span>
      </label>
      <textarea id="info" name="info" rows="4" cols="50"></textarea>
    </div>
    <base-button type="button">Submit</base-button>
  </form>
  </div>
  <the-dialog v-if="showDialog" @close-dialog="closeDialog"
    :name="name"
    :companyName = "companyName"
    :title="title"
    :department="department"
    :radioButtons="radioButtons"
    :phoneText="phoneText"
    :emailText="emailText"
    :address="address"
    :address_2="address_2"
    :city="city"
    :state="state"
    :zip="zip"
    :additionalInfo="additionalInfo"
  ></the-dialog>
</template>

<script>
import TheDialog from './TheDealog.vue'
import FormSubmited from './FormSubmited.vue'

  export default {
    components: {
      TheDialog,
      FormSubmited
    },
    emits: ['close-dialog'],
    data() {
      return {
        name: '',
        companyName: '',
        title: '',
        department: '',
        radioButtons: '',
        phoneText: '',
        emailText: '',
        address: '',
        address_2: '',
        city: '',
        state: '',
        zip: '',
        additionalInfo: '',
        showDialog: false,
        formSubmited: false,
        showError: false
      }
    },
    methods: {
      submitForm() {
        this.formSubmited = true
        this.showDialog = true

        if (!this.name || !this.companyName || !this.department || !this.radioButtons || !this.phoneText || !this.emailText) {
          this.showError = true
          this.formSubmited = false
          this.showDialog = false
        }
      },
      closeDialog() {
        this.showDialog = false
      },
      removeError(e) {
       e.target.classList.remove('showErrorInput')
       this.$refs.prefCont.classList.remove('showError')
      }
    }
  }
</script>

<style scoped>
  header {
    padding: 20px;
    text-align: center;
    background-color: rgb(61, 61, 128);
    color: white;
  }

  em {
    color: red;
  }

  h1 {
    padding: 0;
    margin: 0;
  }

  input {
    border: none;
    border-bottom: 1px solid grey;
    width: 70%;
    padding: 10px;
  }

  label {
    float: left;
    min-width: 10%;
    padding-top: 10px;
  }

  .col {
    padding: 5px;
    width: 100%;
  }

  .col-1 {
    display: flex;
  }

  form {
    padding: 20px;
    width: 800px;
  }

  select {
    border: none;
    border-bottom: 1px solid grey;
    width: 70%;
  }

  textarea {
    width: 70%;
  }
  .showError {
    color: red;
  }

  .showErrorInput {
    border-bottom: 1px solid red;
  }

  .showErrorInput:focus {
    background-color: rgba(255, 0, 0, 0.423);
    border-bottom: 1px solid red;
  }
</style>