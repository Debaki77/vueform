<template>
    <div>
      <form @submit.prevent="submitForm">
        <div>
          <label>Name:</label>
          <input v-model="form.name" type="text" />
          <span v-if="!$v.form.name.required">Name is required</span>
          <span v-if="!$v.form.name.minLength">Name must be at least 3 characters</span>
        </div>
        <button type="submit">Submit</button>
      </form>
    </div>
  </template>
  
  <script>
  import useVuelidate from "@vuelidate/core";
  import { required, minLength } from "@vuelidate/validators";
  
  export default {
    name:"ValidationExample",
    data() {
      return {
        form: { name: "" },
      };
    },
    validations() {
      return {
        form: {
          name: { required, minLength: minLength(3) },
        },
      };
    },
    created() {
      this.v$ = useVuelidate();
    },
    methods: {
      submitForm() {
        this.v$.$touch();
        if (this.v$.$invalid) {
          console.log("Form is invalid");
        } else {
          console.log("Form submitted", this.form);
        }
      },
    },
  };
  </script>
  