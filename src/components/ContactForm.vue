<template>
  <div>
    <h2>New Contact</h2>
    <v-form @submit.prevent="handleSubmit" ref="contactForm">
      <v-text-field outlined label="First Name" v-model="form.firstName" :rules="validators.firstName"/>
      <v-text-field outlined label="Last Name" v-model="form.lastName" :rules="validators.lastName"/>
      <v-text-field type="number" outlined label="Phone" v-model="form.phone" :rules="validators.phone" />
<v-select outlined label="Phone Type" :items="phoneTypeOptions"  v-model="form.type" />
      <v-text-field outlined label="Email" v-model="form.email" :rules="validators.email"/>
      <v-btn type="submit" color="green" dark>Submit</v-btn>
    </v-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        firstName: "",
        lastName: "",
        phone: "",
        type: "",
        email: "",
      },
      phoneTypeOptions: ["Home","Cell", "Office"],
      validators: {
          firstName: [
              val => !!val || "Contact first name is required",
              val => val.length < 25 || "First name must be less than 25 characters"
          ],
          lastName:[
              val => val.lastName < 25 || "Last name must be less than 25 characters"
          ],
          phone: [
              val => !!val || "Phone number is requred",
              val => val.length === 10 || "Enter at least 10 numbers"
          ],
          email: [
              val => val.includes('@') || "Enter a valid email address"
          ]
      }
    };
  },
  methods: {
      handleSubmit()  {
          const isValid = this.$refs.contactForm.validate();
          if (!isValid) {
              return;
          }
          this.$emit("contact-submit", this.form);
          this.form = {
            firstName: "",
            lastName: "",
            phone: "",
            type: "",
            email: "",  
          };
          this.$refs.contactForm.resetValidation();
      }
  }
};
</script>

<style></style>
