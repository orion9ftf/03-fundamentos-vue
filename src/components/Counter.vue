<template>
  <!-- <h2>{{ title || 'Counter' }}</h2> -->
  
  <h2>{{ customTitle }} {{ start }}</h2>

  <p>{{ counter }}</p>

<!-- la idea no es sobrecargar al componente con ecuaciones: -->
  <!-- <p>{{ counter }} <sup>2</sup> = {{ counter * counter }}</p> -->

<!-- methods -->
  <!-- <p>{{ counter }} <sup>2</sup> = {{ getSquareValue() }}</p> -->

<!-- computed -->
  <p>{{ counter }} <sup>2</sup> = {{ squareCounter }}</p>

  <div>
    <!-- <button v-on:click="increase">+1</button>
    <button v-on:click="decrease">-1</button> -->
    <button @click="increase">+1</button>
    <button @click="decrease">-1</button>
  </div>
</template>

<script>
export default {
  props: { //['title', 'start'], //properties
    title: String,
    start: {
      type: Number,
      default: 5,
      //required: true // obliga a pasarle un valor por defecto
      validator( value ) {
        return value >= 0 
      }
    }
  },
  //name: 'Counter'
  data() {
    return {
      counter: this.start
    }
  },
  methods: { //en este caso se dispara muchas veces el mismo método
    getSquareValue(){
      // console.log('getquareValue')
      return this.counter * this.counter
    },
    increase() {
      this.counter++
    },
    decrease() {
      this.counter--
    }
  },
  computed: { //las propiedades computadas, se almacenan en el caché, lo cual es eficiente
    squareCounter() {
      // console.log('ejecución de propiedad computada')
      return this.counter * this.counter
    },
    customTitle() {
      return this.title ? this.title : 'Counter'
      // return this.title || 'Counter'
    }
  }
}
</script>

<style>
  button {
    background-color: #0abb50;
    border-radius: 5px;
    border: 1px solid white;
    color: white;
    cursor: pointer;
    margin: 0 5px;
    padding: 5px 15px;
    transition: 0.3s ease-in-out;
  }

  button:hover {
    background-color: #069f43;
    transition: 0.3s ease-in-out;
  }
</style>