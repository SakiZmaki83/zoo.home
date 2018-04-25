<template>
  <div>
  <form @submit.prevent="addAnimal">

  <label for="species">Species</label>
  <input type="text" id="species" v-model="newAnimal.species">

  <label for="name">Name</label>
  <input type="text" id="name" v-model="newAnimal.name">

  <label for="date">Date</label>
  <input type="number" id="date" v-model="newAnimal.date">
  
  <button type="submit">Add animal</button>
  </form>
    <table>
      <thead>
        <th>Species</th>
        <th>Name</th>
        <th>Date</th>
      </thead>
      <tbody>
      <tr v-for="(animal, key) in animals" :key="key">
        <td>{{ animal.species }}</td>
        <td>{{ animal.name }}</td>
        <td>{{ animal.date ? animal.date : 'nepoznat' }}</td>
        <td><button @click="remove(animal)">Remove animal</button></td>
        <td><button @click="topFunction(animal)">Move to top</button></td>

      </tr>
      </tbody>
    </table>
  
  </div>
</template>

<script>
export default {
  name: 'AnimalList',
 data(){
   return{
     animals: [
       {species:'lion', name:'Simba', date: '2016'},
       {species:'monkey', name:'Chita', date: '2017'},
       {species:'fish', name:'Nemo', date: ''},
       {species:'iguana', name:'Kamy', date: '2018'},
       {species:'snake', name:'Set', date: ''}
     ],
     newAnimal: {
       species: '',
       name: '',
       date: ''
     }
   }
 },
 methods: {
   remove(animal){
     this.animals.splice(this.animals.indexOf(animal), 1)
   },
   topFunction(animal){
     this.animals.splice(this.animals.indexOf(animal), 1)
     this.animals.unshift(animal);
   },
   addAnimal(){
     this.animals.push(this.newAnimal);
     this.newAnimal = {};
   }
 }
}
</script>

