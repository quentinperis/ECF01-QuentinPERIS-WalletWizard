<template>
  <div>
    <h2 id="intituledubas">Historique des dépenses</h2>
    <ul>
      <li v-for="(depense, index) in depenses" :key="index">
        {{ depense.description }} - {{ depense.montant }} €
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['depenses']
};
</script>

<style scoped>

</style>
