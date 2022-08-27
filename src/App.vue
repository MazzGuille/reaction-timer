<template>
    <h1 class="texto">MazzTimer</h1>
    <p class="texto">DESARROLLADO CON VUE</p>
    <p class="texto">Al darle click al boton apracera un cuadro azul en un intervalo de tiempo aleatorio, entre 2-7 segundos.
      <br> <br>
     <b>¡HAZ CLICK LO MAS RAPIDO POSIBLE!</b></p>
    <button class="boton" @click="start" :disabled="isPlaying">Jugar</button>   
    <Block v-if="isPlaying" :delay="delay" @end="endGame"/>    
    <Results v-if="showResults" :puntuacion="score"/>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'


export default {
  name: 'App',
  components: {Block, Results},
  data(){
    return{
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods:{
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true,
      this.showResults= false
    },
    endGame(reactionTime){
      this.score = reactionTime,
      this.isPlaying= false,
      this.showResults= true
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

.boton{
  border-radius: 12px;
  background-color: transparent;
  color: blue;
  border: 1px solid blue;
  width: 100px;
  padding: 10px 0;
  cursor: pointer;
}

.boton:disabled{
  opacity: .5;
}

.texto{
  color: blue;
}
</style>
