<template>
    <div class="container mt-5">
      <h3>Ventes Enregistrées</h3>
      <table class="table">
        <thead>
          <tr>
            <th>Référence</th>
            <th>Désignation</th>
            <th>Quantité Vendue</th>
            <th>Prix de Vente</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(vente, index) in ventes" :key="index">
            <td>{{ vente.reference }}</td>
            <td>{{ vente.designation }}</td>
            <td>{{ vente.quantite }}</td>
            <td>{{ vente.prix }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const ventes = ref([]);
  </script>
  