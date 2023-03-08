<template>
  <h3>Text</h3>
  <p>{{ numProp }}</p>
  <button @click="printFC">Ejecuta print</button>

  <br />
  <hr />
  <span>NUMBER: {{ bNumber }}</span>
  <button @click="myFunction">Aumentar</button>
</template>

<script>
export default {
  props: {
    printFC: Function,
    numProp: {
      type: Number,
      defaut: 10,
    },
    bNumber: Number,
  },
  emits: ["changeNumber"],
  setup(context) {
    
    const myFunction = () => {
      context.emit("changeNumber");
    };

    return {
      myFunction,
    };
  },
};
</script>

<style>
</style>