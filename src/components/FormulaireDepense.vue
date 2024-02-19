<template>
  <div>
    <h2>Ajouter une nouvelle dépense</h2>
  
    <form @submit.prevent="ajouterDepense">
      <label>Description:</label>
      <input type="text" v-model="description" required>
      <label>Montant:</label>
      <input type="number" v-model.number="montant" required>
      <button type="submit">Ajouter</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      description: '',
      montant: null
    };
  },
  methods: {
    ajouterDepense() {
      this.$emit('nouvelle-depense', { description: this.description, montant: this.montant });
      this.description = '';
      this.montant = null;
    }
  }
};
</script>
