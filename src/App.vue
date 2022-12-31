<template>
  <div class="container text-center mt-3">
    <h1>Hola {{ name.toLowerCase() }}</h1>
    <h2 :class="changeColor">{{ contar }}</h2>
    <div class="btn-group">
      <button @click="increment" class="btn btn-success">+</button>

      <button @click="decrement" class="btn btn-danger">-</button>

      <button @click="reset" class="btn btn-secondary">Reset</button>
      <button @click="add" :disabled="bloqBtn" class="btn btn-primary">
        Add
      </button>
    </div>
    <ul class="list-group mt-4 ">
      <li v-for="(num, index) in arrayNumeros" :key="num" class="list-group-item">
        {{ num }}
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";

const name = "soy Lukitas";
const contar = ref(0);
const arrayNumeros = ref([]);

// Metodos
const increment = () => {
  contar.value++;
  console.log("La cuenta es", contar.value);
};
const decrement = () => {
  contar.value--;
  console.log("La cuenta ahora es", contar.value);
};
const reset = () => {
  contar.value = 0;
};

const add = () => {
  arrayNumeros.value.push(contar.value);
};

const changeColor = computed(() => {
  if (contar.value === 0) return "zero";
  if (contar.value > 0) return "positive";
  return "negative";
});

const bloqBtn = computed(() => {
  if (arrayNumeros.value.includes(contar.value)) return true;
  return false;
});
</script>

<style scoped>
.positive {
  color: green;
}
.negative {
  color: red;
}
.zero {
  color: gold;
}
</style>
