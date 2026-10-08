<script setup>
import { ref, computed } from 'vue'

const nouvelleTache = ref('')
const taches = ref([])
const filtre = ref('toutes')

function ajouterTache() 
{
  if (nouvelleTache.value.trim() !== '')
   {
    taches.value.push({
      id: Date.now(),
      libelle: nouvelleTache.value ,
      terminee: false
    })
    nouvelleTache.value = ''
  }
}

function supprimerTache(id) 
{
  const nouvellesTaches = []
  for (let i = 0; i < taches.value.length; i++)
  {
    if (taches.value[i].id !== id) 
    {
      nouvellesTaches.push(taches.value[i])
    }
  }
  taches.value = nouvellesTaches
}

function calculerNonTerminees()
{
  let compteur = 0
  for (let i = 0; i < taches.value.length; i++) 
  {
    if (taches.value[i].terminee == false) 
    {
      compteur++
    }
  }
  return compteur
}

const nbTachesNonTerminees = computed(calculerNonTerminees)

function filtrerTaches() 
{
  const resultat = []
  for (let i = 0; i < taches.value.length; i++)
   {
    if (filtre.value === 'encours' && taches.value[i].terminee === false) 
    {
      resultat.push(taches.value[i])
    } 
    else if (filtre.value === 'terminees' && taches.value[i].terminee === true) 
    {
      resultat.push(taches.value[i])
    } 
    else if (filtre.value === 'toutes')
    {
      resultat.push(taches.value[i])
    }
  }
  return resultat
}

const tachesFiltrees = computed(filtrerTaches)
</script>

<template>
  <div>
    <h1>Liste des tâches</h1>

    <input v-model="nouvelleTache" type="text" >
    <button @click="ajouterTache">Ajouter</button>

    <!--la question facultatif-->
    <div style="margin-top: 10px;">
      <button @click="filtre = 'toutes'">Toutes</button>
      <button @click="filtre = 'encours'">En cours</button>
      <button @click="filtre = 'terminees'">Terminées</button>
    </div>

    <p v-if="tachesFiltrees.length == 0">Aucune tâche pour le moment</p>

    <!--la liste -->
    <ul v-else>
      <li v-for="tache in tachesFiltrees" :key="tache.id">

        <input type="checkbox" v-model="tache.terminee">
        <span :class="{ barre: tache.terminee }">
          {{ tache.libelle }}
        </span>

        <button @click="supprimerTache(tache.id)">Supprimer</button>
      </li>
    </ul>
  <!-- Le compteur -->
    <p>Nombre de tâches non terminées : {{ nbTachesNonTerminees }}</p>

  </div>
</template>
<style>
.barre 
{
  text-decoration: line-through;
}
</style>