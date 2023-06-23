<script setup>
import { ref,computed } from "vue";

const name = "Vue 3";


const counter = ref(0);
const arrayFavoritos = ref([])

const increment = () => {
    
    counter.value++;
};
const decrement = () => {
    
    counter.value--;
};
const reset = () => {
    
    counter.value = 0;
};

const add = () => {
arrayFavoritos.value.push(counter.value)
};

const bloquearbtn = computed (()=>{
  const numsearch = arrayFavoritos.value.find(num => num === counter.value);
  console.log(numsearch);
  if(numsearch === 0) return true;
  return numsearch ? true : false;
})

const classCounter = computed (()=>{
  if (counter.value === 0){
    return "zero"
  }
  if (counter.value > 0){
    return "positive"
  }
  if (counter.value < 0){
    return "negative"
  }
  
});

</script>

<template>
  
    <h1>Hola {{ name }}!</h1>
    <h2 :class="classCounter">
    {{ counter }}
    </h2>
    
    
    <button @click="increment">Click increment</button>
    <button @click="decrement">Click decrement</button>
    <button @click="reset">Click reset</button>
    <button @click="add" :disabled="bloquearbtn">add</button>
    {{ arrayFavoritos }}
<ul>
   <li v-for="(num, index) in arrayFavoritos"
   :key="index">
   {{ num }}
    

   </li>

</ul>

</template>

<style>

.positive {
  color : green;
}
.negative{
  color: red;
}
.zero{
  color: blue;
}
</style>
