<template>
  <div>
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
        <td>{{ animal.date }}</td>
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
     ]
   }
 }
}
</script>

