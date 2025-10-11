<template>
  <div class="container mx-auto px-4 py-8">
    <h1 class="text-3xl font-bold mb-6">Contact Me</h1>
    <p class="mb-4">Feel free to reach out using the form below:</p>
    <ContactForm />
  </div>
</template>

<script setup>
import ContactForm from '@/components/ContactForm.vue';
</script>

<style scoped>
.container {
  max-width: 800px;
}
</style>