<template>
    <div class="container mt-5">
      <form @submit.prevent="enregistrerVente">
        <div class="mb-3">
          <label for="reference" class="form-label">Référence</label>
          <input type="text" class="form-control" id="reference" v-model="vente.reference">
          <div v-if="errors.reference" class="text-danger">{{ errors.reference }}</div>
        </div>
        <div class="mb-3">
          <label for="designation" class="form-label">Désignation</label>
          <input type="text" class="form-control" id="designation" v-model="vente.designation">
          <div v-if="errors.designation" class="text-danger">{{ errors.designation }}</div>
        </div>
        <div class="mb-3">
          <label for="quantite" class="form-label">Quantité Vendue</label>
          <input type="number" class="form-control" id="quantite" v-model="vente.quantite">
          <div v-if="errors.quantite" class="text-danger">{{ errors.quantite }}</div>
        </div>
        <div class="mb-3">
          <label for="prix" class="form-label">Prix de Vente</label>
          <input type="number" class="form-control" id="prix" v-model="vente.prix">
          <div v-if="errors.prix" class="text-danger">{{ errors.prix }}</div>
        </div>
        <button type="submit" class="btn btn-primary">Enregistrer Vente</button>
      </form>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const vente = ref({
    reference: '',
    designation: '',
    quantite: '',
    prix: ''
  });
  
  const errors = ref({});
  
  const validerFormulaire = () => {
    errors.value = {};
    
    if (!vente.value.reference) {
      errors.value.reference = 'La référence est obligatoire';
    }
    
    if (!vente.value.designation) {
      errors.value.designation = 'La désignation est obligatoire';
    }
  
    if (!vente.value.quantite || vente.value.quantite <= 0) {
      errors.value.quantite = 'Veuillez entrer une quantité valide';
    }
  
    if (!vente.value.prix || vente.value.prix <= 0) {
      errors.value.prix = 'Veuillez entrer un prix valide';
    }
  
    return Object.keys(errors.value).length === 0;
  };
  
  const enregistrerVente = () => {
    if (validerFormulaire()) {
      // Envoyer les données vers une base de données ou ajouter à une liste de ventes.
      ventes.value.push({ ...vente.value });
      // Réinitialiser le formulaire
      vente.value = {
        reference: '',
        designation: '',
        quantite: '',
        prix: ''
      };
    }
  };
  
  const ventes = ref([]);
  </script>
  