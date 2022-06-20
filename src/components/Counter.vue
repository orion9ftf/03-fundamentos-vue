<template>
  <h2>Counter</h2>
  <p>{{ counter }}</p>

<!-- la idea no es sobrecargar al componente con ecuaciones: -->
  <p>{{ counter }} <sup>2</sup> = {{ counter * counter }}</p>

<!-- methods -->
  <!-- <p>{{ counter }} <sup>2</sup> = {{ getSquareValue() }}</p> -->

<!-- computed -->
  <p>{{ counter }} <sup>2</sup> = {{ squareCounter }}</p>

</template>

<script>
export default {
  //name: 'Counter'
  data() {
    return {
      counter: 5
    }
  },
  methods: { //en este caso se dispara muchas veces el mismo método
    getSquareValue(){
      // console.log('getquareValue')
      return this.counter * this.counter
    }
  },
  computed: { //las propiedades computadas, se almacenan en el caché, lo cual es eficiente
    squareCounter() {
      // console.log('ejecución de propiedad computada')
      return this.counter * this.counter
    }
  }
}
</script>

<style>

</style>