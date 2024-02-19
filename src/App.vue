<template>
  <div id="app">
    <div>
      <h2 id="intitulehaut">Ajouter une nouvelle dépense</h2>
      
      <form id="formDepense" @submit.prevent="ajouterDepense">
        <label>Intitulé de la dépense</label>
        <input class="inputmoney" placeholder="Loyer, courses, téléphone, cinéma..." type="text" v-model="nouvelleDepense.description" required>
        <label>Montant:</label>
        <input  id="inputmontant" type="currency" placeholder="0.00€" v-model.number="nouvelleDepense.montant" required>
        <button type="submit">Ajouter</button>
      </form>
    </div>
    <div>
      <h2 id="intitulehaut">Ajouter une nouvelle entrée d'argent</h2>
      <form id="formEntreeArgent" @submit.prevent="ajouterEntreeArgent">
        <label>intitulé de l'entrée d'argent</label>
        <input class="inputmoney" placeholder="Salaires..." type="text" v-model="nouvelleEntreeArgent.description" required>
        <label>Montant:</label>
        <input id="inputmontant" type="currency" placeholder="0.00€" v-model.number="nouvelleEntreeArgent.montant" required>
        <button type="submit">Ajouter</button>
      </form>
    </div>
    

    <ListeDepenses :depenses="depenses" />
    <ListeEntreesArgent :entreesArgent="entreesArgent" />
    
    <OperationsCreditDebit :depenses="depenses" :entreesArgent="entreesArgent" />
   
  </div>
</template>

<script>
import ListeDepenses from './components/ListeDepenses.vue';
import ListeEntreesArgent from './components/ListeEntreesArgent.vue';
import OperationsCreditDebit from './components/OperationsCreditDebit.vue';

export default {
  name: 'App',
  components: {
    ListeDepenses,
    ListeEntreesArgent,
    OperationsCreditDebit
  },
  data() {
    return {
      nouvelleDepense: { description: '', montant: null },
      nouvelleEntreeArgent: { description: '', montant: null },
      depenses: [],
      entreesArgent: []
    };
  },
  methods: {
    ajouterDepense() {
      this.depenses.push({ ...this.nouvelleDepense }); 
      this.nouvelleDepense = { description: '', montant: null }; 
    },
    ajouterEntreeArgent() {
      this.entreesArgent.push({ ...this.nouvelleEntreeArgent }); 
      this.nouvelleEntreeArgent = { description: '', montant: null }; 
    }
  }
};
</script>

<style>
body {
  background-color: #2c2b2b;
}

#app {
  font-family: Arial, sans-serif;
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
  background-color: #100f0f;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(71, 69, 69, 0.1);
  display: grid;
  grid-template-columns: auto;
  border-radius: 10px;
}
#depense {
  font-weight: bold;
  color: red;
}

.inputmoney::placeholder {
  font-family: monospace;
  font-weight: 0.5rem;
  font-size: small;
  color: #00000097;
}


#inputmontant {
  height: 30px;
  width: 206px;
  outline: none;
  caret-color: #45a049;
  font-size: 1.3rem;
  border-radius: 20px;
  border: none;
  padding-left: 20px;
}
input:focus{
  outline: none;
  border: none;
}
input::placeholder {
  color: #100f0f;
  font-family: monospace;
}
#intitulehaut {
  display: flex;
  justify-content: center;
  margin-bottom: 10px;
}

h2 {
  font-size: 1.3rem;
  font-family: monospace;
  font-weight: bold;
  color: rgb(221, 223, 217);
  margin-bottom: 5px;
  background-color: #4caf50;
  border-top-right-radius: 10px;
}
#intituledubas {
  background-color: #5aee61d2;
  display: flex;
  justify-content: center;
  border-top:#45a049;
  border-bottom:#45a049;
  border-top-right-radius: 10px;
  margin-bottom: 10px;
}
p {
  display: flex;
  justify-content: end;
  font-family: monospace;
  color: #FEFEFE;
}
form {
  margin-bottom: 50px;
  margin-top: 30px;
}

#formDepense {
  border-bottom: solid 1px #FEFEFE;
  border-right: solid 5px red;
}
#formEntreeArgent {
  border-bottom : solid 1px #FEFEFE;
  border-right: solid 5px #4caf50;
}
label {
  font-weight: bold;
  color: #4caf50;
  margin-right: 20px;
}

input[type="text"],
input[type="number"] {
  width: 98%;
  padding: 8px;
  margin: 8px 0;
  border: 1px solid #ccc;
  border-radius: 4px;
  outline: none;
  caret-color: #45a049;
  font-size: 1.2rem;
  font-style: monospace;
  font-weight: bold;
  color: #45a049;
}

button {
  background-color: #4caf50;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  justify-self: end;
  margin-left: 285px;
  margin-top: 20px;
  margin-bottom: 20px;
  font-size: 1.3rem;
  font-family: monospace;
}

button:hover {
  background-color: #45a049;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin-bottom: 8px;
  display: flex;
  justify-content: end;
  color: #FEFEFE;
  margin-top: 20px;
  margin-bottom: 20px;
}

.operations-container {
  display: flex;
  justify-content: space-between;
}

.operations-container p {
  font-size: 1.2rem;
}

.total-container {
  margin-top: 20px;
}

.total-container p {
  font-size: 1.5rem;
  font-weight: bold;
}
</style>



