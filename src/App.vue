<script setup>
import { ref, computed } from 'vue';

const cities = ref([
  'São Paulo',
  'Rio de Janeiro',
  'Belo Horizonte',
  'Salvador',
  'Fortaleza',
  'Curitiba',
  'Manaus',
  'Recife',
  'Porto Alegre',
  'Brasília',
])

const cityadd = ref()

const addCity = () => {
  cities.value.push(cityadd.value[0].toUpperCase() + cityadd.value.slice(1))
}

const sortcities = computed (()=>{
  return cities.value.sort()
})

const removeCity = (index) => {
  return cities.value.splice(index,1)
} 

</script>
<template>
    <main>
      <div class="renderization">
        <ul v-for="(city, index) in cities" :key="index">
          <div class="city">
            <img src="./assets/images/cityIcon.png" alt="Imagem cidade" class="icon-city">
            <li >{{ city }}</li>
            <button @click="removeCity(index)" class="remove-button">X</button>
          </div>
        </ul>
      </div>

      <div class="add-edit-remove-button">
        <div class="add-button">
          <input v-model="cityadd" placeholder="please state some city to add" type="text" class="inputCity" >
          <button @click="addCity(), sortcities()">Adiconar</button>
          
        </div>
      </div>

    </main>
</template>

<style scoped>
ul{
  display: flex;
  flex-direction: row;
}

.city{
  display: flex;
  margin: 10px 0 0 10px;
}

.inputCity {
  text-transform: capitalize;
}

li {
  list-style: none;
  margin-left: 5px;
  width: 7vw;
}

li img{
  width: 17px;
  height: 17px;
}

.icon-city {
  width: 17px;
}

.add-button {
  display: flex;
  justify-content: center;
  flex-direction: column;
}

.remove-button{
  display: none;
  background-color: rgba(240, 248, 255, 0);
  border: none;
  color: red;
}

.city:hover > .remove-button{
  display: flex; 
  justify-content: end;

}

</style>
