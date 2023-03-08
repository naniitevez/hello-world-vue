<template>
  <h1>Vue JS</h1>
  <p>Marca: {{ brand }}</p>
  <div>
    Colores:
    <ol>
      <li v-for="color in colors" :key="color">{{ color }}</li>
    </ol>
  </div>
  <ul>
    <template v-for="power in powers" :key="power">
      <li v-if="power < 260">Menor a 300: {{ power }}</li>
      <li v-else-if="power === 260">Hibrido: {{ power }}</li>
      <li v-else>Mayor a 300: {{ power }}</li>
    </template>
  </ul>

  <button @click="print">CLick</button>

  <p>{{ aNumber }}</p>
  <button @click="add(5)">Add 5</button>
  <button @click="add(10)">Add 10</button>

  <hr />

  <TextComponent
    :numProp="aNumber"
    :printFC="aFunction"
    :bNumber="bNumber"
    @changeNumber="changeNumber"
  />
</template>
  
  <script>
import { ref } from "vue";
import TextComponent from "../components/TextComponent.vue";

export default {
  // data() {
  //   return {
  //     brand: "Audi",
  //   }
  // }
  components: {
    TextComponent,
  },
  setup() {
    const brand = "Audi";
    const colors = ["rojo", "verde", "amarillo"];
    const powers = [80, 100, 190, 200, 240, 260, 450, 480, 500];
    let aNumber = ref(10);
    let bNumber = ref(4);

    const print = () => {
      console.log("Console.log ejecutado");
    };

    const add = (num) => {
      aNumber.value = aNumber.value + num;
    };

    const aFunction = () => {
      console.log("Ejecuto una funcion pasada por props");
    };

    const changeNumber = () => {
      console.log("ya me aburri")
    };

    return {
      brand,
      colors,
      powers,
      print,
      aNumber,
      add,
      aFunction,
      bNumber,
      changeNumber,
    };
  },
};
</script>
  
  <style>
</style>