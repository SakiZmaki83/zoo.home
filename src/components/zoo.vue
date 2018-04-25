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
        <th>Sector</th>
        <th>&nbsp;</th>
        <th>&nbsp;</th>
        
        
       
      </thead>
      <tbody>
      <tr v-for="(animal, key) in animals" :key="key">
        <td>{{ animal.species }}</td>
        <td>{{ animal.name }}</td>
        <td>{{ animal.date ? animal.date : 'nepoznat' }}</td>
        <td>{{ animal.sector.name }}</td>
        <td><button @click="remove(animal)">Remove animal</button></td>
        <td><button @click="topFunction(animal)">Move to top</button></td>

      </tr>
      </tbody>
    </table>

    <table>
       <thead>
          <th>Name</th>
          <th>Surface</th>
       </thead>

       <tbody>
       <tr v-for="(sector, key) in sectors" :key="key">
        <td>{{ sector.name }}</td>
        <td>{{ sector.surface }}</td>
       <td><button @click="seeAnimals(sector.name)">See animals</button></td>
        </tr>
       </tbody>
    </table>
  
  </div>
</template>

<script>
const sectors = [
        { name: 'Forest animals', surface: 'Cages' },
        { name: 'Forest', surface: 'Terarium' },
        { name: 'Ocean animals', surface: 'Aquarium' },
        { name: 'Savannah', surface: 'Cages' }
      ];


export default {
  name: 'AnimalList',
 data(){
   return{
     sectors: sectors,
     animals: [
       {species:'lion', name:'Simba', date: '2016', sector: sectors[3]},
       {species:'monkey', name:'Chita', date: '2017',sector: sectors[0]},
       {species:'fish', name:'Nemo', date: '',sector: sectors[2]},
       {species:'iguana', name:'Kamy', date: '2018',sector: sectors[1]},
       {species:'snake', name:'Set', date: '',sector: sectors[1]}
     ],
     newAnimal: {
       species: '',
       name: '',
       date: '',
       sector: ''
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
   },
  seeAnimals(sectorName) {
      let animals = this.animals
        .filter(animal => animal.sector.name === sectorName)
        .map(animal => animal.species + ' ' + animal.name)
        .join('\n');
      
      alert(animals);
   }
 }
}
</script>

