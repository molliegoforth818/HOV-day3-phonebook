<template>
  <div>
    <v-row>
      <v-col :lg="8" :sm="12">
        <contact-table :contacts="contacts" />
      </v-col>
      <v-col :lg="4" :sm="12">
        <contact-form @contact-submit="addContact" />
      </v-col>
    </v-row>
  </div>
</template>

<script>
import ContactForm from "./ContactForm";
import ContactTable from "./ContactTable";
export default {
  components: { ContactForm, ContactTable },
  data() {
    return {
      contacts: [],
    };
  },
  mounted() {
    const existingContacts = JSON.parse(localStorage.getItem("contacts"));
    this.contacts = existingContacts || [];
  },
  methods: {
    addContact(newContact) {
      this.contacts.push(newContact);
      localStorage.setItem("contacts", JSON.stringify(this.contacts));
    },
  },
};
</script>

<style></style>
