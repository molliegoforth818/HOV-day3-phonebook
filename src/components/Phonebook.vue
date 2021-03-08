<template>
  <h1>Hello from the phonebook component</h1>
</template>

<script>
import ContactForm from './ContactForm'
export default {
    components: { ContactForm },
data() {
    return {
        contacts: [],
    };
},
};
</script>

<style>

</style>