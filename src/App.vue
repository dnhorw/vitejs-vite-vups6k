<script setup>
import { ref } from 'vue'
import VillagerList from './components/VillagerList.vue'

const newVillagerText = ref('')
const villagers = ref([
  {
    id: 1,
    title: 'Carl'
  },
  {
    id: 2,
    title: 'Bungo'
  },
  {
    id: 3,
    title: 'Gumpy'
  }
])

let nextVillagerId = 4

function addNewVillager() {
  villagers.value.push({
    id: nextVillagerId++,
    title: newVillagerText.value
  })
  newVillagerText.value = ''
}
</script>

<template>
<form v-on:submit.prevent="addNewVillager">
<label for="new-villager">Add a villager: </label>
<input
v-model="newVillagerText"
id="new-villager"
placeholder="E.g. Charles the Horse"
/>
<button>Add</button>
</form>
<ul>
  <villager-item
    v-for="(villager, index) in villagers"
    :key="villager.id"
    :title="villager.title"
    @remove="villagers.splice(index, 1)"
></villager-item>
</ul>
  </template>



