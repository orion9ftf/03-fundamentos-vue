<template>
  <h2>Indecision Components</h2>

  <!-- <img v-bind:src="https://via.placeholder.com/250" alt="bg"> -->
  <img v-if="img" :src="img" alt="bg">

  <div class="bg-dark"></div>

  <div class="indecision-container">
    <input v-model="question" type="text" placeholder="Hazme una pregunta">
    <p>Recuerda terminar tu pregunta con un signo de interrogación <strong style="color:blue">(?)</strong></p>

    <div>
      <h2>¿Lloverá? => {{ question }}</h2>
      <h1>{{ answer }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return {
      question: null,
      answer: null,
      img: null
    }
  },
  methods: {
    async getAnswer(){
      this.answer = 'Pensando...'

      // const response = await fetch('https://yesno.wtf/api').then( resp => resp.json() )
      // console.log(response)

      //desestructurando solo que necesitamos:
      const { answer, image } = await fetch('https://yesno.wtf/api').then( resp => resp.json() )
      console.log(answer)

      this.answer = answer
      this.img = image

    }
  },
  watch: {
    question(value, oldValue) { //question debe llamarse igual que la propiedad que debe escuchar los cambios
      if ( !value.includes('?') ) return

      this.getAnswer()
    }
  }
}
</script>

<style scoped>
  img, .bg-dark {
      height: 100vh;
      left: 0px;
      max-height: 100%;
      max-width: 100%;
      position: fixed;
      top: 0px;
      width: 100vw;
  }

  .bg-dark {
      background-color: rgba(0, 0, 0, 0.4);
  }

  .indecision-container {
      position: relative;
      z-index: 99;
  }
  
  input {
      width: 250px;
      padding: 10px 15px;
      border-radius: 5px;
      border: none;
  }
  input:focus {
      outline: none;
  }

  p {
      color: white;
      font-size: 20px;
      margin-top: 0px;
  }

  h1, h2 {
      color: white;
  }
  
  h2 {
      margin-top: 150px;
  }
</style>