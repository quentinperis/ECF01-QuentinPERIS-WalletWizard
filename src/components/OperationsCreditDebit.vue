<template>
  <div>
    <h2 id="intituledubas" >Opérations de crédit et de débit</h2>
    <p>Total des dépenses: {{ totalDepenses.toFixed(2) }} €</p>
    <p>Total des entrées d'argent: {{ totalEntrees.toFixed(2) }} €</p>
    <p :class="{'solde-positif': solde >= 0, 'solde-negatif': solde < 0}">Solde: {{ solde }} €</p>
  </div>
</template>

<script>
export default {
  props: ['depenses', 'entreesArgent'],
  computed: {
    totalDepenses() {
      return this.depenses.reduce((total, depense) => total + depense.montant, 0);
    },
    totalEntrees() {
      return this.entreesArgent.reduce((total, entree) => total + entree.montant, 0);
    },
    solde() {
      return (this.totalEntrees - this.totalDepenses).toFixed(2);
    }
  }
};
</script>

<style scoped>
.solde-positif {
  color: green;
}

.solde-negatif {
  color: red;
  font-size: 1.3rem;
}
</style>
