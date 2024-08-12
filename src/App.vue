<template>
  <div>
    <VenteForm />
    <VentesTable :ventes="ventes" />
  </div>
</template>

<script setup>
import VenteForm from './components/VenteForm.vue';
import VentesTable from './components/VentesTable.vue';
import { ref } from 'vue';

const ventes = ref([]);
</script>
