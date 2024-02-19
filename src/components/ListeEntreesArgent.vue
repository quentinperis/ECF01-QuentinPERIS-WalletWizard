<template>
  <div>
    <h2 id="intituledubas">Liste des entrées d'argent</h2>
    <ul>
      <li v-for="(entree, index) in entreesArgent" :key="index">
        {{ entree.description }} + {{ entree.montant }} €
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['entreesArgent'] 
};
</script>

<style scoped>

</style>
